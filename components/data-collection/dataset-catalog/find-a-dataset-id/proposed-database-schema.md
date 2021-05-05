---
description: Specification Sheet on our DoltHub database
---

# Datasets schema

![](../../../../.gitbook/assets/image%20%285%29.png)

  
The `agencies` table prevents redundancy in `datasets` and establishes a true one-to-many relationship \(one agency may have many associated datasets\). Agencies are described primarily by their location. 

Datasets are described primarily by an agency and the URL of the data.

`update_frequency`: annual, semi-annual, quarterly, monthly, weekly, daily

`agency_types`: federal, state, municipal, university

You can also view our schema [here](https://dbdiagram.io/d/607762c7b6aeb3052d90271b), with a little more interactability.





We will also have a MongoDB database for the following data:

* Actual scraped data from the agencies 
  * will be linked back to DoltHub via the `datasets`.`id` field. 

 
* Each scraper will have a record in a collection that contains data pertaining to it's last run time, last edit time, GitHub link and another collection that will store any credentials needed \(like for APIs\)
  * will be linked back to DoltHub via the `datasets`.`scraper_id` field. 

