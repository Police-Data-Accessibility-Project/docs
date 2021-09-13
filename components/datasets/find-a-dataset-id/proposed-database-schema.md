---
description: Specification Sheet on our DoltHub database
---

# Datasets Schema & Field Explanation

![Current datasets schema \(28 May 2021\)](../../../.gitbook/assets/image%20%2812%29.png)

##  Schema Overview

The `agencies` table prevents redundancy in `datasets` and establishes a true one-to-many relationship \(one agency may have many associated datasets\). Agencies are described primarily by their location. 

`datasets` are described primarily by an agency and the URL of the data. This is the actual data itself that we will want to acquire and ingest.  
  
You can also view an interactive database diagram [here](https://dbdiagram.io/d/607762c7b6aeb3052d90271b), it is the same one visible as an image at the top of this page.

## Datasets Table Explanation

`id`  is a UUID without hyphens. MySQL – which Dolt is built on – does not have a specific field for unique identifiers, so we use a `varchar(32)` and remove hyphens to save some space. If you leave this field blank, it will automatically generate. If you wish to generate it manually:

* In SQL: `SELECT REPLACE(uuid(), '-', '');`
* Online on DoltHub Web: [Link](https://www.dolthub.com/repositories/pdap/datasets/query/master?q=SELECT+REPLACE%28uuid%28%29%2C+%27-%27%2C+%27%27%29%3B%0A%0A&active=Tables)
* Using Python3 :

```text
import uuid
str(uuid4()).replace('-', '')
```

`url` is the web location of the data for us to obtain. It could be a directory of files, a link to an aggregator, a map of incident reports. Our [Examples & Best Practices guide](../submit-or-update-datasets/examples-best-practices.md) will help you determine what to use for the `url` as well as determining the other fields for this table

`status_id` is the current status of the dataset

1. **not started** - we just received this dataset and have not started ingesting data for it
2. **invalid URL** - this dataset has had its URL change or is no longer working. We need to find 
3. **scraping in progress** - someone is actively figuring out how to download / retrieve / scrape the data for us to store
4. **initial data scraped** - someone has successfully retrieved the data from the agency
5. **initial data loaded** - someone has taken the initially scraped data and formatted it in a way we can ingest it in our database \(and / or provide a link to the original harvested data to be viewed\)
6. **done; process automated** - we have figured out a way to do a sync with the agency, constantly refreshing with new data

`source_type_id` is where the data is sourced from

1. **court**- records coming out of an official court system
2. **direct** - records hosted by the agency themselves for consumption
3. **third-party** - records hosted by another provider \(ArcGIS\) or aggregator \(CityProtect / Crimegraphics\)

`data_types_id` is what kind of data this dataset is. Most of these are self explanatory

1. **accident\_reports** 
2. **arrest\_records**
3. **booking\_reports**
4. **calls\_for\_service**
5. **car\_GPS**
6. **court\_cases**
7. **daily\_activity\_logs**
8. **dispatch\_logs**
9. **dispatch\_recordings**
10. **incident\_reports**
11. **officer\_complaint\_records**
12. **officer\_records**
13. **personnel\_files**
14. **policy\_manuals**
15. **post\_certifications**
16. **time\_sheets**
17. **traffic\_citations**
18. **traffic\_stops**
19. **training\_logs**
20. **use\_of\_force\_reports**
21. **video\_metadata** - metadata on a specific video \(location, timestamps\)
22. **videos** - this table in `data-intake` will store a link to view the actual video
23. **crime\_statistics** - aggregated crime statistics \(like the federal UCR or department specific aggregation\)
24. **annual\_reports**  - some agencies provide annual reports over a plethora of information from the past year. Usually these are in the form of PDF documents
25. **daily\_crime\_bulletin**
26. **media\_bulletin**
27. **multi** - while we prefer to have a specific data type for each url, our current schema requiring a unique URL may not allow that. Sometimes agencies store multiple types of data on the same URL \(like Crimegraphics\). Try to use this type sparingly and fill in the notes field on what all data can be found

`format_types_id` is how the data is structured. As of writing, we do not have format types fully fledged out. There is not quite a standard to how agencies present data unless it comes from an aggregator such as CityProtect or ArcGIS. Usually scrapers will have a better idea of the format\_type. Here are our current format\_types:

1. **NIBRS** - Data from the National Incident-Based Reporting System
2. **cityprotect** - Incident Report data from CityProtect.com
3. **crimemapping** - Incident report data from Crimemapping.com
4. **opendata** - the Open Data format / initiative
5. **crimegraphics** - Data from Crimegraphics.com

`agency_id` is a relationship to the `agencies` table. It links this dataset back to a specific agency.

`update_frequency` how often the data updates \(usually the person responsible for retrieving the data will figure this out as they try to get the data\). These are self-explanatory.

1. **annually**
2. **bi-annually**
3. **quarterly**
4. **monthly**
5. **weekly**
6. **daily**

`portal_type` this is a legacy field from our original schema. If the data comes from a certain aggregator like CityProtect, Tyler Technologies, ArcGIS, you can specify that here. This field may be merged into `format_types_id` in the future.

`coverage_start` if you can find when the agency started producing the data at this link, you can record it here. Some agencies keep historical records, some agencies wipe and start fresh each day.

`scraper_id` Not yet implemented, okay to leave blank

`notes` any notes about the dataset we should know. Especially useful if the `data_types_id` is `multi` for us to at-a-glance figure out what all it may comprise of.

`can_scrape` some agencies – and some states – have laws expressly forbidding scraping. We absolutely need to know if we are banned from scraping. Let us know that by setting this value to `0` if scraping is not allowed and `1` if there is no language indicating scraping is prohibited.

`date_insert` automatically generates when a new dataset is added

`last_modified` auto generates on insert, will need to be manually updated when you modify

`machine_readable` not fully implemented. If the dataset contains machine readable output like an API endpoint, JSON, CSV or XLSX files, we consider that machine readable. It is very easy to transform and load into a database, so that would be `1`. If the output of the datasets is in PDF, DOCX format that is not easily parsable, it would be considered not machine readable so `0`



## Agencies Table Explanation

`id`  is identical to the `datasets`.`id`:  a UUID without hyphens. MySQL – which Dolt is built on – does not have a specific field for unique identifiers, so we use a `varchar(32)` and remove hyphens to save some space. If you leave this field blank, it will automatically generate. If you wish to generate it manually:

* In SQL: `SELECT REPLACE(uuid(), '-', '');`
* Online on DoltHub Web: [Link](https://www.dolthub.com/repositories/pdap/datasets/query/master?q=SELECT+REPLACE%28uuid%28%29%2C+%27-%27%2C+%27%27%29%3B%0A%0A&active=Tables)
* Using Python3 :

```text
import uuid
str(uuid4()).replace('-', '')
```

`name` is the name of the agency such as "California Highway Patrol" or "Greenwood County Sheriff's" Office

`agency_type` is pretty self explanatory:

1. **federal** - the big leagues, like FBI, CIA level 
2. **state** - agencies for an entire state
3. **county** - agencies for a specific county
4. **city** - agencies for a specific city
5. **university** - agencies that only serve a campus 
6. **defunct** - this agency no longer exists, it could have been merged with another local agency or completely disbanded for one reason or another

`state_iso` a link to our [states](https://www.dolthub.com/repositories/pdap/datasets/data/master/states) table. A two-digit code representing the state / province the agency is a part of

`city` is the city the agency is a part of \(will not apply to federal / state / county agencies\)

`zip` is the postal code of the agency, may not always apply

`county_fips` is the Federal Information Processing System code for US counties. The full FIPS is 13 characters long and unique to each geographic area. The first 2 digits are state, and the following 3 digits are county specific. You can use the [FCC API](https://geo.fcc.gov/api/census/#!/area/get_area) with the `lat` and `lng` to find the FIPS code.

`lat` is the latitude of the main HQ of this particular agency \(provided some agencies have multiple districts\)

`lng` is the longitude of the main HQ of this particular agency \(provided some agencies have multiple districts\)

`date_insert` automatically generated on insert

`data_policy` we can store a link to Terms and Conditions or a Data Policy page from an agency. Very useful if they expressly forbid scraping

`country` should always be `US` for now, but is here in case we decided to start exploring other countries

`homepage_url` this is the agencies homepage that may be of interest if the dataset URLs break, we may be able to search their homepage again to see if we can find updated information







We will also have a separate DoltHub repository \([pdap/data-intake](https://www.dolthub.com/repositories/pdap/data-intake)\) for the following data:

* Actual scraped data from the agencies 
  * will be linked back to DoltHub via the `datasets`.`id` field.
* Every `data_type` will have it's own table of data that is ingested.

  
In the distant future, we are looking into having a sync with our Dolt instance to PostgreSQL to maintain our own copy of our data. The schema will be identical to the current Dolt implementation. The other benefit is it will directly serve as the back-end for our web application, [https://app.pdap.io](https://app.pdap.io).

