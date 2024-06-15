# v2 API docs (WIP)

We are working on [data-sources-app-v2](https://github.com/Police-Data-Accessibility-Project/data-sources-app/issues/248) and will use this page to build documentation for the new version. The v2 API is not yet ready for the public.

## Base URL

```
https://data-sources.pdap.io/api
```

## Endpoints

### Homepage Search Cache

<mark style="color:blue;">`GET`</mark> `[base-url]/homepage-search-cache`

**Headers**

| Name          | Type   | Description                                         |
| ------------- | ------ | --------------------------------------------------- |
| Authorization | String | Value formatted as "Bearer \[access token/api key]” |

**Responses**

{% tabs %}
{% tab title="200: OK Successful operation" %}
```json
[
    {
        "SUBMITTED_NAME": "string",
        "JURISDICTION_TYPE": "string",
        "STATE_ISO": "string",
        "MUNICIPALITY": "string",
        "COUNTY_NAME": "string",
        "AIRTABLE_UID": "string",
        "COUNT_DATA_SOURCES": "integer",
        "ZIP_CODE": "string",
        "NO_WEB_PRESENCE": "Boolean"
    }
]
```
{% endtab %}
{% endtabs %}

<mark style="color:blue;">`POST`</mark> `[base-url]/homepage-search-cache`

**Headers**

| Name          | Type   | Description                                         |
| ------------- | ------ | --------------------------------------------------- |
| Authorization | String | Value formatted as "Bearer \[access token/api key]” |

**Request Body**

| Name            | Type      | Description                         |
| --------------- | --------- | ----------------------------------- |
| agency\_uid     | String    | The UID of the agency               |
| search\_results | \[String] | List of search results to be cached |

**Example Request Body**

```json
{
    "agency_uid": "uid123",
    "search_results": ["result1", "result2"]
}
```

#### Responses

{% tabs %}
{% tab title="200: OK Successful Operation" %}
```json
{
    "message": "Search Cache Updated"
}
```
{% endtab %}
{% endtabs %}

