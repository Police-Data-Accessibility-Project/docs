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
Users can sign up for an account through the post function in 

[resources/User.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/User.py)

. The user's password is hashed using werkzeug.security’s generate_pasword_hash function. The user's email and hashed password is stored in the users table in the Data Sources database.
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

{% swagger method="get" path="/user" baseUrl="[base-url]" summary="Logs in the user and returns an API key." expanded="false" fullWidth="true" %}
{% swagger-description %}
The login function can be found through the get function in 

[resources/User.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/resources/User.py)

. Each time a user logs in, a new API key is created using uuid.uuid4().hex, updated in for the matching user in the users table, encoded in a JWT token, and the JWT token is sent to the user to be stored on the client side.
{% endswagger-description %}

{% swagger-parameter in="body" name="email" required="true" %}
Matches exactly with the "email" property in user's table
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" type="String" required="true" %}
Checked against the password_digest for the user with the matching "email" property using werkzeug.security’s check_password_hash function
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
