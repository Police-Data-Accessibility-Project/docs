# Development Testing

## Test Databases

Currently, two test databases exist:

* Sandbox - This is to be used by developers to test out changes to the schema and content of the database in connection with development versions of the app. Sensitive information from the production database, such as user information, are excluded in this environment.
* Stage - This is used to test stage code in an environment as closely modeling the production database as possible, and is not designed to be accessed directly by developers. Sensitive information is included in this environment.

Both databases are refreshed daily from the production database, using logic in the [https://github.com/Police-Data-Accessibility-Project/prod-to-dev-migration](https://github.com/Police-Data-Accessibility-Project/prod-to-dev-migration) repository. Additionally, they are updated with SQL code from [dev\_scripts.sql](https://github.com/Police-Data-Accessibility-Project/prod-to-dev-migration/blob/main/dev\_scripts.sql), which provides the most up-to-date development version of the database.

## Obtaining test database information for admins

Connection information can be obtained through access the databases on Digital Ocean.

* In [https://cloud.digitalocean.com/databases](https://cloud.digitalocean.com/databases?i=feca0b), you will be able to select different databases. From here, you can click on the `Actions` dropdown, and select `Connection Details` to obtain information about the relevant connection.

Login information for users can be obtained through environment variables provided for the Prod to Stage and Sandbox Migration Job, currently located at: [https://automation.pdap.io/job/Prod%20to%20Stage%20and%20Sandbox%20Migration/configure](https://automation.pdap.io/job/Prod%20to%20Stage%20and%20Sandbox%20Migration/configure)

* Look for environment variables for:
  * SANDBOX\_DEV\_USER
  * SANDBOX\_DEV\_PASSWORD
* Additional information about the database, including the server name, the port number, and the database name, can also be found on connection strings labeled with the "SANDBOX\_" or "STAGE\_" prefixes.



## Running Tests Locally

A connection string will need to be input into the `DEV_DB_CONN_STRING` and `DO_DATABASE_URL` environment variables for your local copy of [data\_sources\_app ](https://github.com/Police-Data-Accessibility-Project/data-sources-app). This connection string will take the following form:

`postgresql://user:password@server:port/dbname?sslmod=require`

Once this is set, you can run tests by running `pytest <directory-or-file>`

Full pytest documentation can be found [here](https://docs.pytest.org/en/stable/contents.html).
