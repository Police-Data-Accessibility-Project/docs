# Introduction

## Overview

The PDAP API is how internal and external users programmatically access information and make changes to the PDAP [Data Sources database](../activities/data-sources/explore-data-sources.md).

## Get access

Reach out to [contact@pdap.io](mailto:contact@pdap.io) or make noise in Discord if you'd like access to the API.

See the [administration page](endpoints/admin.md) for information on user creation with the API.

## Authentication

API routes that read and modify the Data Sources database should be protected through authentication. The API has an @api\_required decorator (located in [/middleware/security.py](https://github.com/Police-Data-Accessibility-Project/data-sources-app/blob/main/middleware/security.py)) that can be added to each route so that only authenticated users can access the database. To protect a route with this decorator, add @api\_required on the line above a given route.

### @api\_required decorator

The @api\_required decorator requires a request header to include an `Authorization` key with the value formatted as `Bearer [api_key]`. The api\_required function parses the request header and checks to see if the api\_key is defined. If it isn’t, it’ll return a message requesting an API key.

### Validating the API key

If there is an API key, it’s passed to the is\_valid function. This function connects to the Data Source database’s users table and finds the user in the table with the matching API key. The function then checks that a valid user was returned from the database. If not, the function returns `false` to `api_required`, which sends a response stating that the API key was invalid.

## Rate limits

The rate limit for querying the database currently maxes out at 3000 rows, which is larger than the row count of any table in the database right now.
