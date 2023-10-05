---
description: Use the API to find, use, and manage Data Sources.
---

# Data Sources database

## Base URL

```
https://data-sources.pdap.io
```

## Search

{% swagger method="get" path="/quick-search/{search}/{location}" baseUrl="[base-url]" summary="Quick Search Data Sources by search term and location" fullWidth="true" expanded="true" %}
{% swagger-description %}
The quick search endpoint is located in [resources/QuickSearch.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The quick search endpoint executes its search using the agency\_source\_link table in the Data Sources database, which links each data source in the data\_sources table with its associated agency in the agencies table.
{% endswagger-description %}

{% swagger-parameter in="path" name="search" type="String" required="true" %}
Checks partial matches on any of the following properties on the data\_source table: "name", "description", "record\_type", and "tags". The search term will is case insensitive and will match singular and pluralized versions of the term.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="location" type="String" required="true" %}
Checks partial matches on any of the following properties on the agencies table: "county\_name", "state\_iso", "municipality", "agency\_type", "jurisdiction\_type", "name"
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Value formatted as "Bearer \[jwt\_token]”
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

## Data Sources

{% swagger method="get" path="/data-sources" baseUrl="[base-url]" summary="Get all Data Sources" fullWidth="true" expanded="true" %}
{% swagger-description %}
The data sources endpoint is located in [resources/DataSources.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The data sources endpoint returns all rows in the corresponding Supabase table up to the current row limit set in Supabase.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Value formatted as "Bearer \[jwt\_token]”
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

## Agencies

{% swagger method="get" path="/agencies/{page}" baseUrl="[base-url]" summary="Get all Agencies" fullWidth="true" expanded="true" %}
{% swagger-description %}
The agencies endpoint is located in [resources/Agencies.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The agencies endpoint returns 1000 rows from the corresponding Supabase table offset by the page number passed.
{% endswagger-description %}

{% swagger-parameter in="path" name="page" required="true" %}
Passing 1 will return the first 1000 rows. Subsequent page number return  subsequent results
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" %}
Value formatted as "Bearer \[jwt\_token]”
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
