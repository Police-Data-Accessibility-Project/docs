# Endpoints

## Base URL

```http
https://data-sources-app-bda3z.ondigitalocean.app/
```

## Quick Search

{% swagger method="get" path="/quick-search/{search}/{county}" baseUrl="[base-url]" summary="Get Data Sources by search term and location" fullWidth="true" expanded="true" %}
{% swagger-description %}
The quick search endpoint is located in 

[resources/QuickSearch.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/QuickSearch.py)

. The quick search endpoint executes its search using the agency_source_link table in the Data Sources database, which links each data source in the data_sources table with its associated agency in the agencies table.  
{% endswagger-description %}

{% swagger-parameter in="path" name="search" type="String" required="true" %}
Checks for partial match in "name" property of data_sources table, case insensitive.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="county" type="String" required="true" %}
Matches "county" property of linked agencies exactly. Counties are case sensitive and don’t include the word “county”. 
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Value formatted as "Bearer [api_key]”
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

Here are some examples of what would and wouldn’t be considered a partial match for the search term:

| Search  | Data Source Name                                 | Partial Match                                                                                                    |
| ------- | ------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| review  | Allegheny County Police Review Board Transcripts | True                                                                                                             |
| reviews | Allegheny County Police Review Board Transcripts | False because the search term has an “s” at the end of “review” but “review” is singular in the data source name |
| ReViEw  | Allegheny County Police Review Board Transcripts | True                                                                                                             |

{% tabs %}
{% tab title="Example Endpoint" %}
```http
https://data-sources-app-bda3z.ondigitalocean.app/quick-search/review/Allegheny
```
{% endtab %}

{% tab title="Example Python" %}
```python
import requests
base_url = "https://data-sources-app-bda3z.ondigitalocean.app/"
search_term = "review"  # Replace with your search term
county = "Allegheny"   # Replace with your desired county
api_key = "YOUR_API_KEY_HERE"  # Replace with your actual API key

url = f"{base_url}quick-search/{search_term}/{county}"

# Create the Authorization header
headers = {
    "Authorization": f"Bearer {api_key}"
}

# Make the GET request with the Authorization header
response = requests.get(url, headers=headers)
```
{% endtab %}

{% tab title="Example JavaScript" %}
```javascript
const axios = require('axios');

const baseUrl = "https://data-sources-app-bda3z.ondigitalocean.app/";
const search_term = "review";  // Replace with your search term
const county = "Allegheny";    // Replace with your desired county
const api_key = "YOUR_API_KEY_HERE";  // Replace with your actual API key

const url = `${baseUrl}quick-search/${search_term}/${county}`;

// Create the Authorization header
const headers = {
  'Authorization': `Bearer ${api_key}`
};

// Make the GET request with the Authorization header
axios.get(url, { headers })
  .then(response => {
    console.log("Search results:");
    response.data.forEach(item => {
      console.log(`Data Source Name: ${item.name}`);
    });
  })
  .catch(error => {
      console.error("An error occurred:", error.message);
    }
  });

```
{% endtab %}
{% endtabs %}

***
