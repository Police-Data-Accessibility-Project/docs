---
description: Use the API to find, use, and manage Data Sources.
---

# Data Sources database

## Base URL

```
https://data-sources.pdap.io
```

## Search Tokens

{% swagger method="get" path="/search-tokens/{search}/{location}" baseUrl="[base-url]" summary="Generate API token for front end search" fullWidth="true" expanded="true" %}
{% swagger-description %}
The search tokens endpoint is located in [resources/SearchTokens.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The search tokens endpoint generates an API token valid for 5 minutes and forwards the search parameters to the Quick Search endpoint. This endpoint is meant for use by the front end only.
{% endswagger-description %}

{% swagger-parameter in="query" name="endpoint" %}
The endpoint that will be accessed after a search token is generated
{% endswagger-parameter %}

{% swagger-parameter in="query" name="arg1" type="String" required="true" %}
The first argument that will be forwarded on to the appropriate endpoint. Currently either "search" for quick-search or "id" for data-sources
{% endswagger-parameter %}

{% swagger-parameter in="query" name="arg2" type="String" required="true" %}
The second argument that will be forwarded on to the appropriate endpoint. Currently just used for "location" for quick-search
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation" %}
{% tabs %}
{% tab title="Schema" %}
<pre class="language-plsql"><code class="lang-plsql">count int
<strong>data array[object]
</strong>    agency_name string
    municipality string
    state_iso string
    data_source_name string
    description string
    record_type string
    source_url string
    record_format string
    coverage_start string
    coverage_end string
    agency_supplied boolean
</code></pre>
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 1,
	"data": [
		{
			"agency_name": "Allegheny County Police Department - PA",
			"municipality": "Pittsburgh",
			"state_iso": "PA",
			"data_source_name": "Allegheny County Police Review Board Transcripts",
			"description": null,
			"record_type": "Policies & Contracts",
			"source_url": "https://www.alleghenycounty.us/county-council/police-review-board-meetings.aspx",
			"record_format": "[\"PDF: Machine Created\"]",
			"coverage_start": "2018-08-29",
			"coverage_end": "2018-09-26",
			"agency_supplied": true
		}
	]
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}
{% endswagger %}

## Search

{% swagger method="get" path="/quick-search/{search}/{location}" baseUrl="[base-url]" summary="Quick Search Data Sources by search term and location" fullWidth="true" expanded="true" %}
{% swagger-description %}
The quick search endpoint is located in [resources/QuickSearch.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The quick search endpoint executes its search using the agency\_source\_link table in the Data Sources database, which links each data source in the data\_sources table with its associated agency in the agencies table. This endpoint is meant for use by the search tokens endpoint only.
{% endswagger-description %}

{% swagger-parameter in="path" name="search" type="String" required="true" %}
Checks partial matches on any of the following properties on the data\_source table: "name", "description", "record\_type", and "tags". The search term will is case insensitive and will match singular and pluralized versions of the term.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="location" type="String" required="true" %}
Checks partial matches on any of the following properties on the agencies table: "county\_name", "state\_iso", "municipality", "agency\_type", "jurisdiction\_type", "name"
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Value formatted as "Bearer \[access token/api key]”
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation" %}
{% tabs %}
{% tab title="Schema" %}
<pre class="language-plsql"><code class="lang-plsql">count int
<strong>data array[object]
</strong>    agency_name string
    municipality string
    state_iso string
    data_source_name string
    description string
    record_type string
    source_url string
    record_format string
    coverage_start string
    coverage_end string
    agency_supplied boolean
</code></pre>
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 1,
	"data": [
		{
			"agency_name": "Allegheny County Police Department - PA",
			"municipality": "Pittsburgh",
			"state_iso": "PA",
			"data_source_name": "Allegheny County Police Review Board Transcripts",
			"description": null,
			"record_type": "Policies & Contracts",
			"source_url": "https://www.alleghenycounty.us/county-council/police-review-board-meetings.aspx",
			"record_format": "[\"PDF: Machine Created\"]",
			"coverage_start": "2018-08-29",
			"coverage_end": "2018-09-26",
			"agency_supplied": true
		}
	]
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="No API key found" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
count int
data array[object]
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 0,
	"data": []
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Invalid API key" %}

{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Something went wrong" %}

{% endswagger-response %}
{% endswagger %}

## Data Sources

{% swagger method="get" path="/data-sources" baseUrl="[base-url]" summary="Get all Data Sources" fullWidth="true" expanded="true" %}
{% swagger-description %}
The data sources endpoint is located in [resources/DataSources.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The data sources endpoint returns all rows in the corresponding Data Sources database table.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Value formatted as "Bearer \[access token/api key]”
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation" %}
{% tabs %}
{% tab title="Schema" %}
<pre class="language-plsql"><code class="lang-plsql">count int
<strong>data array[object]
</strong>    agency_name string
    municipality string
    state_iso string
    data_source_name string
    description string
    record_type string
    source_url string
    record_format string
    coverage_start string
    coverage_end string
    agency_supplied boolean
</code></pre>
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 1,
	"data": [
		{
			"agency_name": "Allegheny County Police Department - PA",
			"municipality": "Pittsburgh",
			"state_iso": "PA",
			"data_source_name": "Allegheny County Police Review Board Transcripts",
			"description": null,
			"record_type": "Policies & Contracts",
			"source_url": "https://www.alleghenycounty.us/county-council/police-review-board-meetings.aspx",
			"record_format": "[\"PDF: Machine Created\"]",
			"coverage_start": "2018-08-29",
			"coverage_end": "2018-09-26",
			"agency_supplied": true
		}
	]
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="No API key found" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
count int
data array[object]
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 0,
	"data": []
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Invalid API key" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/data-sources-by-id/[id]" baseUrl="[base-url]" summary="Get Data Source by Id" fullWidth="true" expanded="true" %}
{% swagger-description %}
The data sources endpoint is located in [resources/DataSources.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The data source by id endpoint returns just the row for the data source that corresponds to the id passed.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Value formatted as "Bearer \[access token/api key]”
{% endswagger-parameter %}

{% swagger-parameter in="path" name="id" required="true" %}
Data source id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation" %}
{% tabs %}
{% tab title="Schema" %}
<pre class="language-plsql"><code class="lang-plsql">count int
<strong>data array[object]
</strong>    agency_name string
    municipality string
    state_iso string
    data_source_name string
    description string
    record_type string
    source_url string
    record_format string
    coverage_start string
    coverage_end string
    agency_supplied boolean
</code></pre>
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 1,
	"data": [
		{
			"agency_name": "Allegheny County Police Department - PA",
			"municipality": "Pittsburgh",
			"state_iso": "PA",
			"data_source_name": "Allegheny County Police Review Board Transcripts",
			"description": null,
			"record_type": "Policies & Contracts",
			"source_url": "https://www.alleghenycounty.us/county-council/police-review-board-meetings.aspx",
			"record_format": "[\"PDF: Machine Created\"]",
			"coverage_start": "2018-08-29",
			"coverage_end": "2018-09-26",
			"agency_supplied": true
		}
	]
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="No API key found" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
count int
data array[object]
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 0,
	"data": []
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Invalid API key" %}

{% endswagger-response %}
{% endswagger %}

## Archives

{% swagger method="get" path="/archives" baseUrl="[base-url]" summary="Get all Archived urls" fullWidth="true" expanded="true" %}
{% swagger-description %}
The archives endpoint is located in [resources/Archives.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/Archives.py). The get method  on the archives endpoint returns all rows for urls that the [automatic archives](https://github.com/Police-Data-Accessibility-Project/automatic-archives/blob/main/cache\_url.py) script has cached in the Internet Archive.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Value formatted as "Bearer \[access token/api key]”
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation" %}
{% tabs %}
{% tab title="Schema" %}
<pre class="language-plsql"><code class="lang-plsql">count int
<strong>data array[object]
</strong>    agency_name string
    municipality string
    state_iso string
    data_source_name string
    description string
    record_type string
    source_url string
    record_format string
    coverage_start string
    coverage_end string
    agency_supplied boolean
</code></pre>
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 1,
	"data": [
		{
			"agency_name": "Allegheny County Police Department - PA",
			"municipality": "Pittsburgh",
			"state_iso": "PA",
			"data_source_name": "Allegheny County Police Review Board Transcripts",
			"description": null,
			"record_type": "Policies & Contracts",
			"source_url": "https://www.alleghenycounty.us/county-council/police-review-board-meetings.aspx",
			"record_format": "[\"PDF: Machine Created\"]",
			"coverage_start": "2018-08-29",
			"coverage_end": "2018-09-26",
			"agency_supplied": true
		}
	]
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="No API key found" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
count int
data array[object]
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 0,
	"data": []
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Invalid API key" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="/archives" baseUrl="[base-url]" summary="Get all Archived urls" fullWidth="true" expanded="true" %}
{% swagger-description %}
The archives endpoint is located in [resources/Archives.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/Archives.py). The put method on the archives endpoint updates the data source matching the passed id, updating the last\_cached date if it alone is passed, or it and the broken\_source\_url\_as\_of field and the url\_status to 'broken'.&#x20;
{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="String" required="true" %}
The airtable uid for the data source that was cached
{% endswagger-parameter %}

{% swagger-parameter in="body" name="last_cached" type="Date" required="true" %}
The current date since the data source url was just cached in the Internet Archive
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Value formatted as "Bearer \[access token/api key]”
{% endswagger-parameter %}

{% swagger-parameter in="body" name="broken_source_url_as_of" type="Date" required="true" %}
The current date if the url is no longer active, otherwise None
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation" %}
{% tabs %}
{% tab title="Schema" %}
<pre class="language-plsql"><code class="lang-plsql">count int
<strong>data array[object]
</strong>    agency_name string
    municipality string
    state_iso string
    data_source_name string
    description string
    record_type string
    source_url string
    record_format string
    coverage_start string
    coverage_end string
    agency_supplied boolean
</code></pre>
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 1,
	"data": [
		{
			"agency_name": "Allegheny County Police Department - PA",
			"municipality": "Pittsburgh",
			"state_iso": "PA",
			"data_source_name": "Allegheny County Police Review Board Transcripts",
			"description": null,
			"record_type": "Policies & Contracts",
			"source_url": "https://www.alleghenycounty.us/county-council/police-review-board-meetings.aspx",
			"record_format": "[\"PDF: Machine Created\"]",
			"coverage_start": "2018-08-29",
			"coverage_end": "2018-09-26",
			"agency_supplied": true
		}
	]
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="No API key found" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
count int
data array[object]
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 0,
	"data": []
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Invalid API key" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="" baseUrl="[base-url]/data-sources" summary="Create Data Source" fullWidth="true" %}
{% swagger-description %}
The data sources endpoint is located in [resources/DataSources.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The create data source endpoint posts a new data source to the database and returns True if successful and False if not.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
Value formatted as "Bearer \[access token/api key]”
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Data" type="JSON" %}
A JSON object of the data source information. Refer to the Data Source dictionary for available fields: [https://docs.pdap.io/activities/data-dictionaries/data-sources-data-dictionary](https://docs.pdap.io/activities/data-dictionaries/data-sources-data-dictionary). However, the following fields cannot be edited: rejection\_note, data\_source\_request, approval\_status, airtable\_uid, airtable\_source\_last\_modified&#x20;



Below is an example of an acceptable body:

{ "name":  "Calls for Service for Chicago Police Department - IL",

"record\_type": "Calls for Service",

"source\_url": "https://informationportal.igchicago.org/911-calls-for-cpd-service",

"coverage\_start": "2019-01-01"

}
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
boolean
```
{% endtab %}

{% tab title="Example" %}
```json
True
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Invalid API key" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="" baseUrl="[base-url]/data-sources-by-id/[id]" summary="Update Data Source by Id" fullWidth="true" %}
{% swagger-description %}
The data sources endpoint is located in [resources/DataSources.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The update data source by id endpoint updates a data source and returns a status to confirm a successful update.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Value formatted as "Bearer \[access token/api key]”
{% endswagger-parameter %}

{% swagger-parameter in="path" name="id" required="true" %}
Data source id
{% endswagger-parameter %}

{% swagger-parameter in="body" type="JSON" name="Data" %}
A JSON object of the data to be updated. Refer to the Data Source dictionary for available fields: [https://docs.pdap.io/activities/data-dictionaries/data-sources-data-dictionary](https://docs.pdap.io/activities/data-dictionaries/data-sources-data-dictionary). However, the following fields cannot be edited: data\_source\_request, airtable\_uid, airtable\_source\_last\_modified



Below is an example of an acceptable body:

{ "name":  "Calls for Service for Chicago Police Department - IL",

"record\_type": "Calls for Service",

"source\_url": "https://informationportal.igchicago.org/911-calls-for-cpd-service",

"coverage\_start": "2019-01-01"

}
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation" %}
```json
{"status": "success"}
```
{% endswagger-response %}
{% endswagger %}

## Agencies

{% swagger method="get" path="/agencies/{page}" baseUrl="[base-url]" summary="Get all Agencies" fullWidth="true" expanded="true" %}
{% swagger-description %}
The agencies endpoint is located in [resources/Agencies.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The agencies endpoint returns 1000 rows from the corresponding Data Sources database table offset by the page number passed.
{% endswagger-description %}

{% swagger-parameter in="path" name="page" required="true" %}
Passing 1 will return the first 1000 rows. Subsequent page number return  subsequent results
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" %}
Value formatted as "Bearer \[access token/api key]”
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful operation" %}
{% tabs %}
{% tab title="Schema" %}
<pre class="language-plsql"><code class="lang-plsql">count int
<strong>data array[object]
</strong>    agency_name string
    municipality string
    state_iso string
    data_source_name string
    description string
    record_type string
    source_url string
    record_format string
    coverage_start string
    coverage_end string
    agency_supplied boolean
</code></pre>
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 1,
	"data": [
		{
			"agency_name": "Allegheny County Police Department - PA",
			"municipality": "Pittsburgh",
			"state_iso": "PA",
			"data_source_name": "Allegheny County Police Review Board Transcripts",
			"description": null,
			"record_type": "Policies & Contracts",
			"source_url": "https://www.alleghenycounty.us/county-council/police-review-board-meetings.aspx",
			"record_format": "[\"PDF: Machine Created\"]",
			"coverage_start": "2018-08-29",
			"coverage_end": "2018-09-26",
			"agency_supplied": true
		}
	]
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="No API key found" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
count int
data array[object]
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"count": 0,
	"data": []
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Invalid API key" %}

{% endswagger-response %}
{% endswagger %}
