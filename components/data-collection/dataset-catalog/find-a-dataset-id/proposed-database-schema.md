---
description: Specification Sheet on our DoltHub database
---

# Datasets schema

![Current Database Schema \(as of 14 May 2021\)](../../../../.gitbook/assets/image%20%286%29.png)

  
The `agencies` table prevents redundancy in `datasets` and establishes a true one-to-many relationship \(one agency may have many associated datasets\). Agencies are described primarily by their location. 

Datasets are described primarily by an agency and the URL of the data.

`update_frequency`: annual, semi-annual, quarterly, monthly, weekly, daily

`agency_types`: federal, state, municipal, university

`status_id`: not started, invalid URL, scraping in progress, initial data scraped, initial data loaded, done; process automated

You can also view our schema [here](https://dbdiagram.io/d/607762c7b6aeb3052d90271b), with a little more interactability.





We will also have a separate DoltHub repository \([pdap/data-intake](https://www.dolthub.com/repositories/pdap/data-intake)\) for the following data:

* Actual scraped data from the agencies 
  * will be linked back to DoltHub via the `datasets`.`id` field.
* Every `data_type` will have it's own table of data that is intaken.

  
In the distant future, we are looking into migrating to PostgreSQL to maintain full control of our data. The schema will be identical to the current Dolt implementation. The other benefit is it will directly serve as the back-end for our web application, [https://app.pdap.io](https://app.pdap.io).

