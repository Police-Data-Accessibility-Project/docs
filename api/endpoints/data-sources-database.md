---
description: Use the API to find, use, and manage Data Sources.
---

# Data Sources database

## Base URL

```
https://data-sources.pdap.io
```

## Search Tokens

## Generate API token for front end search

<mark style="color:blue;">`GET`</mark> `[base-url]/search-tokens/{search}/{location}`

The search tokens endpoint is located in [resources/SearchTokens.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The search tokens endpoint generates an API token valid for 5 minutes and forwards the search parameters to the Quick Search endpoint. This endpoint is meant for use by the front end only.

#### Query Parameters

| Name                                   | Type   | Description                                                                                                                                   |
| -------------------------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------- |
| arg1<mark style="color:red;">\*</mark> | String | The first argument that will be forwarded on to the appropriate endpoint. Currently either "search" for quick-search or "id" for data-sources |
| arg2<mark style="color:red;">\*</mark> | String | The second argument that will be forwarded on to the appropriate endpoint. Currently just used for "location" for quick-search                |
| endpoint                               | String | The endpoint that will be accessed after a search token is generated                                                                          |

{% tabs %}
{% tab title="200: OK Successful operation" %}
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
{% endtab %}
{% endtabs %}

## Search

## Quick Search Data Sources by search term and location

<mark style="color:blue;">`GET`</mark> `[base-url]/quick-search/{search}/{location}`

The quick search endpoint is located in [resources/QuickSearch.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The quick search endpoint executes its search using the agency\_source\_link table in the Data Sources database, which links each data source in the data\_sources table with its associated agency in the agencies table. This endpoint is meant for use by the search tokens endpoint only.

#### Path Parameters

| Name                                       | Type   | Description                                                                                                                                                                                                                                   |
| ------------------------------------------ | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| search<mark style="color:red;">\*</mark>   | String | Checks partial matches on any of the following properties on the data\_source table: "name", "description", "record\_type", and "tags". The search term will is case insensitive and will match singular and pluralized versions of the term. |
| location<mark style="color:red;">\*</mark> | String | Checks partial matches on any of the following properties on the agencies table: "county\_name", "state\_iso", "municipality", "agency\_type", "jurisdiction\_type", "name"                                                                   |

#### Headers

| Name                                            | Type   | Description                                         |
| ----------------------------------------------- | ------ | --------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Value formatted as "Bearer \[access token/api key]” |

{% tabs %}
{% tab title="200: OK Successful operation" %}
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
{% endtab %}

{% tab title="400: Bad Request No API key found" %}
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
{% endtab %}

{% tab title="403: Forbidden Invalid API key" %}

{% endtab %}

{% tab title="500: Internal Server Error Something went wrong" %}

{% endtab %}
{% endtabs %}

## Data Sources

## Get all Data Sources

<mark style="color:blue;">`GET`</mark> `[base-url]/data-sources`

The data sources endpoint is located in [resources/DataSources.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The data sources endpoint returns all approved rows in the corresponding Data Sources database table by default. An optional JSON object can be passed to get data sources needing identification instead.

#### Headers

| Name                                            | Type   | Description                                         |
| ----------------------------------------------- | ------ | --------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Value formatted as "Bearer \[access token/api key]” |

#### Request Body

| Name | Type | Description                                                              |
| ---- | ---- | ------------------------------------------------------------------------ |
| Data | JSON | In order to get data sources needing identification: {"approved": False} |

{% tabs %}
{% tab title="200: OK Successful operation" %}
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
{% endtab %}

{% tab title="400: Bad Request No API key found" %}
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
{% endtab %}

{% tab title="403: Forbidden Invalid API key" %}

{% endtab %}
{% endtabs %}

## Get Data Source by Id

<mark style="color:blue;">`GET`</mark> `[base-url]/data-sources-by-id/[id]`

The data sources endpoint is located in [resources/DataSources.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The data source by id endpoint returns just the row for the data source that corresponds to the id passed.

#### Path Parameters

| Name                                 | Type   | Description    |
| ------------------------------------ | ------ | -------------- |
| id<mark style="color:red;">\*</mark> | String | Data source id |

#### Headers

| Name                                            | Type   | Description                                         |
| ----------------------------------------------- | ------ | --------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Value formatted as "Bearer \[access token/api key]” |

{% tabs %}
{% tab title="200: OK Successful operation" %}
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
{% endtab %}

{% tab title="400: Bad Request No API key found" %}
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
{% endtab %}

{% tab title="403: Forbidden Invalid API key" %}

{% endtab %}
{% endtabs %}

## Create Data Source

<mark style="color:green;">`POST`</mark> `[base-url]/data-sources`

The data sources endpoint is located in [resources/DataSources.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The create data source endpoint posts a new data source to the database and returns True if successful and False if not.

#### Headers

| Name                                            | Type   | Description                                         |
| ----------------------------------------------- | ------ | --------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Value formatted as "Bearer \[access token/api key]” |

#### Request Body

| Name | Type | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ---- | ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Data | JSON | <p>A JSON object of the data source information. Refer to the Data Source dictionary for available fields: <a href="https://docs.pdap.io/activities/data-dictionaries/data-sources-data-dictionary">https://docs.pdap.io/activities/data-dictionaries/data-sources-data-dictionary</a>. However, the following fields cannot be edited: rejection_note, data_source_request, approval_status, airtable_uid, airtable_source_last_modified </p><p></p><p>Below is an example of an acceptable body:</p><p>{ "name":  "Calls for Service for Chicago Police Department - IL",</p><p>"record_type": "Calls for Service",</p><p>"source_url": "https://informationportal.igchicago.org/911-calls-for-cpd-service",</p><p>"coverage_start": "2019-01-01"</p><p>}</p> |

{% tabs %}
{% tab title="200: OK Successful operation" %}
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
{% endtab %}

{% tab title="403: Forbidden Invalid API key" %}

{% endtab %}
{% endtabs %}

## Update Data Source by Id

<mark style="color:orange;">`PUT`</mark> `[base-url]/data-sources-by-id/[id]`

The data sources endpoint is located in [resources/DataSources.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The update data source by id endpoint updates a data source and returns a status to confirm a successful update.

#### Path Parameters

| Name                                 | Type   | Description    |
| ------------------------------------ | ------ | -------------- |
| id<mark style="color:red;">\*</mark> | String | Data source id |

#### Headers

| Name                                            | Type   | Description                                         |
| ----------------------------------------------- | ------ | --------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Value formatted as "Bearer \[access token/api key]” |

#### Request Body

| Name | Type | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ---- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Data | JSON | <p>A JSON object of the data to be updated. Refer to the Data Source dictionary for available fields: <a href="https://docs.pdap.io/activities/data-dictionaries/data-sources-data-dictionary">https://docs.pdap.io/activities/data-dictionaries/data-sources-data-dictionary</a>. However, the following fields cannot be edited: data_source_request, airtable_uid, airtable_source_last_modified</p><p></p><p>Below is an example of an acceptable body:</p><p>{ "name":  "Calls for Service for Chicago Police Department - IL",</p><p>"record_type": "Calls for Service",</p><p>"source_url": "https://informationportal.igchicago.org/911-calls-for-cpd-service",</p><p>"coverage_start": "2019-01-01"</p><p>}</p> |

{% tabs %}
{% tab title="200: OK Successful operation" %}
```json
{"status": "success"}
```
{% endtab %}
{% endtabs %}

## Archives

## Get all Archived urls

<mark style="color:blue;">`GET`</mark> `[base-url]/archives`

The archives endpoint is located in [resources/Archives.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/Archives.py). The get method  on the archives endpoint returns all rows for urls that the [automatic archives](https://github.com/Police-Data-Accessibility-Project/automatic-archives/blob/main/cache\_url.py) script has cached in the Internet Archive.

#### Headers

| Name                                            | Type   | Description                                         |
| ----------------------------------------------- | ------ | --------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Value formatted as "Bearer \[access token/api key]” |

{% tabs %}
{% tab title="200: OK Successful operation" %}
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
{% endtab %}

{% tab title="400: Bad Request No API key found" %}
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
{% endtab %}

{% tab title="403: Forbidden Invalid API key" %}

{% endtab %}
{% endtabs %}

## Get all Archived urls

<mark style="color:orange;">`PUT`</mark> `[base-url]/archives`

The archives endpoint is located in [resources/Archives.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/Archives.py). The put method on the archives endpoint updates the data source matching the passed id, updating the last\_cached date if it alone is passed, or it and the broken\_source\_url\_as\_of field and the url\_status to 'broken'.&#x20;

#### Headers

| Name                                            | Type   | Description                                         |
| ----------------------------------------------- | ------ | --------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Value formatted as "Bearer \[access token/api key]” |

#### Request Body

| Name                                                          | Type   | Description                                                                        |
| ------------------------------------------------------------- | ------ | ---------------------------------------------------------------------------------- |
| id<mark style="color:red;">\*</mark>                          | String | The airtable uid for the data source that was cached                               |
| broken\_source\_url\_as\_of<mark style="color:red;">\*</mark> | Date   | The current date if the url is no longer active, otherwise None                    |
| last\_cached<mark style="color:red;">\*</mark>                | Date   | The current date since the data source url was just cached in the Internet Archive |

{% tabs %}
{% tab title="200: OK Successful operation" %}
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
{% endtab %}

{% tab title="400: Bad Request No API key found" %}
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
{% endtab %}

{% tab title="403: Forbidden Invalid API key" %}

{% endtab %}
{% endtabs %}

## Agencies

## Get all Agencies

<mark style="color:blue;">`GET`</mark> `[base-url]/agencies/{page}`

The agencies endpoint is located in [resources/Agencies.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py). The agencies endpoint returns 1000 rows from the corresponding Data Sources database table offset by the page number passed.

#### Path Parameters

| Name                                   | Type   | Description                                                                                  |
| -------------------------------------- | ------ | -------------------------------------------------------------------------------------------- |
| page<mark style="color:red;">\*</mark> | String | Passing 1 will return the first 1000 rows. Subsequent page number return  subsequent results |

#### Headers

| Name          | Type   | Description                                         |
| ------------- | ------ | --------------------------------------------------- |
| Authorization | String | Value formatted as "Bearer \[access token/api key]” |

{% tabs %}
{% tab title="200: OK Successful operation" %}
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
{% endtab %}

{% tab title="400: Bad Request No API key found" %}
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
{% endtab %}

{% tab title="403: Forbidden Invalid API key" %}

{% endtab %}
{% endtabs %}
