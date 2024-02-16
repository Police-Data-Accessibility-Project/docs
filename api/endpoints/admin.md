---
description: Use the API to managing users, keys, and access as PDAP staff
---

# Admin

## Base URL

```
https://data-sources.pdap.io
```

## Login & API keys

{% swagger expanded="true" method="post" path="/user" baseUrl="[base-url]" summary="Creates a new user." fullWidth="true" %}
{% swagger-description %}
Users can sign up for an account through the post function in [resources/User.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/User.py). The user's password is hashed using werkzeug.security’s generate\_pasword\_hash function. The user's email and hashed password is stored in the users table in the Data Sources database.
{% endswagger-description %}

{% swagger-parameter in="body" name="email" required="true" type="String" %}
User's email - must be unique
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" required="true" type="String" %}
User's password
{% endswagger-parameter %}

{% swagger-response status="201: Created" description="User successfully created" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
id int
created_at string
updated_at string
email string
password_digest string
api_key string
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"id": 103,
	"created_at": "2023-08-21T19:07:47.587523+00:00",
	"updated_at": "2023-08-21T19:07:47.587523+00:00",
	"email": "test@test.com",
	"password_digest": "pbkdf2:sha256:600000$oil7FzYFZLWpQfHU$44a61e71c063fe90dc22d0d498743dd7870e559c07a660c8de578cff86d5b3f4",
	"api_key": null
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Failed to create user" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/user" baseUrl="[base-url]" summary="Logs in the user." expanded="false" fullWidth="true" %}
{% swagger-description %}
The login function can be found through the get function in [resources/User.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/User.py). If the email and password match a row in the database, "Successfully logged in" will be returned.
{% endswagger-description %}

{% swagger-parameter in="body" name="email" required="true" %}
Matches exactly with the "email" property in user's table
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" type="String" required="true" %}
Checked against the password\_digest for the user with the matching "email" property using werkzeug.security’s check\_password\_hash function
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful login" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
api_key string
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"api_key": "2bd77a1d7ef24a1dad3365b8a5c6994e"
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Bad credentials, failed to login" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/request-reset-password" baseUrl="[base-url]" summary="Sends user a password reset link." expanded="false" fullWidth="true" %}
{% swagger-description %}
This functionality can be found in the get function in [resources/RequestResetPassword.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/tree/main/resources/RequestResetPassword.py). If the email and password match a row in the database, "Successfully logged in" will be returned.
{% endswagger-description %}

{% swagger-parameter in="body" name="email" required="true" %}
Matches exactly with the "email" property in user's table
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful reset request" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
api_key string
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"api_key": "2bd77a1d7ef24a1dad3365b8a5c6994e"
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Failed to match email" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/reset-password/[token]" baseUrl="[base-url]" summary="Reset password token check." fullWidth="true" expanded="true" %}
{% swagger-description %}
This functionality can be found in the get function in [resources/ResetPassword.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/ResetPassword.py). If the token matches a row in the database, "The submitted token is valid" will be returned.
{% endswagger-description %}

{% swagger-parameter in="path" name="token" required="true" %}
Reset password token
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Reset password token validated" %}
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

{% swagger-response status="400: Bad Request" description="Token is invalid" %}
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
{% endswagger %}

{% swagger expanded="true" method="put" path="/user" baseUrl="[base-url]" summary="Updates user password." fullWidth="true" %}
{% swagger-description %}
Users can update their password through the put function in [resources/User.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/User.py). The user's password is hashed using werkzeug.security’s generate\_pasword\_hash function. The user's email and hashed password is stored in the users table in the Data Sources database.
{% endswagger-description %}

{% swagger-parameter in="body" name="email" required="true" type="String" %}
User's email - must be unique
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" required="true" type="String" %}
User's password
{% endswagger-parameter %}

{% swagger-response status="201: Created" description="User password successfully updated" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
id int
created_at string
updated_at string
email string
password_digest string
api_key string
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"id": 103,
	"created_at": "2023-08-21T19:07:47.587523+00:00",
	"updated_at": "2023-08-21T19:07:47.587523+00:00",
	"email": "test@test.com",
	"password_digest": "pbkdf2:sha256:600000$oil7FzYFZLWpQfHU$44a61e71c063fe90dc22d0d498743dd7870e559c07a660c8de578cff86d5b3f4",
	"api_key": null
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Failed to update password" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api_key" baseUrl="[base-url]" summary="Returns an API key for a valid user and password." expanded="false" fullWidth="true" %}
{% swagger-description %}
The key generation function can be found through the get function in [resources/ApiKey](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/ApiKey.py). If the email and password match a row in the database, a new API key is created using uuid.uuid4().hex, updated in for the matching user in the users table, and the API key is sent to the user.
{% endswagger-description %}

{% swagger-parameter in="body" name="email" required="true" %}
Matches exactly with the "email" property in user's table
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" type="String" required="true" %}
Checked against the password\_digest for the user with the matching "email" property using werkzeug.security’s check\_password\_hash function
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful login" %}
{% tabs %}
{% tab title="Schema" %}
```plsql
api_key string
```
{% endtab %}

{% tab title="Example" %}
```json
{
	"api_key": "2bd77a1d7ef24a1dad3365b8a5c6994e"
}
```
{% endtab %}
{% endtabs %}
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Bad credentials, failed to login" %}

{% endswagger-response %}
{% endswagger %}
