---
description: 'https://www.dolthub.com/repositories/pdap/datasets'
---

# Datasets schema & ETL

## Overview

This describes our current [database of datasets in DoltHub](https://www.dolthub.com/repositories/pdap/datasets).



With thousands of different agencies across the United States, the information to be loaded into our central database comes in wildly different formats. A requirement for handling and presentation is to standardize it across federal, state, and municipal and university levels into one cohesive, easy-to-understand package. One problem for the scrapers is each agency delivers different amounts of data back to us to be digested.

## Problem

For City Protect Incident Reports, we get a beautiful JSON response of everything that we need to know about the agency:

```text
{
                "id": "5ce2bd6d3934cc0011eda5f2",
                "crapiId": "111439",
                "name": "Aransas County Sheriffs Office",
                "center": {
                    "coordinates": [
                        -97.053961,
                        28.025965
                    ],
                    "_id": "5ee9edad0e5b2f0013184fcb",
                    "type": "Point"
                },
                "cameraPinLat": 28.2718,
                "cameraPinLng": -97.1242,
                "updatedAt": "2021-04-13T05:11:27.000Z",
                "city": "Rockport",
                "state": "TX",
                "zip": "78382",
                "type": "Sheriff Dept",
                "email": null,
                "county": null,
                "address1": null,
                "address2": null,
                "customerId": "aransascounty.org",
                "isSandboxAgency": false,
                "sandboxAgencyName": null,
                "reports": [],
                "features": [
                    "FORMS_MANAGEMENT",
                    "TIP_SUBMIT_BASIC_CONFIGURATION",
                    "AGENCY_MAP",
                    "TIPPING",
                    "AGENCY_MAP_INCIDENTS",
                    "AGENCY_MAP_SEXOFFENDERS",
                    "AGENCY_PAGE",
                    "BULLETIN",
                    "CAMERA_REGISTRATION"
                ],
                "agencyBadgeUrl": "",
                "agencyName": "ARANSAS COUNTY SHERIFF'S OFFICE",
                "customTippingUrl": "",
                "agencyPathName": "a1f9a015-6e65-4366-a1f7-48e196f7d4e3",
                "bulkDownload": false,
                "tippingEnabled": false,
                "_id": "5ce2bd6d3934cc0011eda5f2"
            }
```

In this case, we know everything we need to ensure we have a record in the `datasets` table to connect our imported incident reports to. Next, we just need to ensure the columns from the data match our columns in the appropriate table, link the foreign keys and we are done!

Another example would be in the scrapers repo, /USA/CA/COL\_LosRiosComm found [here](https://github.com/Police-Data-Accessibility-Project/Scrapers/tree/master/USA/CA/COL_LosRiosComm). We know from the prefix, it is a college. But the data downloaded from this website is in PDF format which may not be easy to discern the rest of the details without reliance on OCR, and at most would just give us the name of the agency.

## Solution

A `schema.json` file in the root of each scraper that provides all of the information required to understand what we are dealing with. JSON is both machine-readable and human-readable format.

```text
{
    "agency_id": "73e93439e6bf4ffc8b3f931a86fa3ad0",
    "agency_info":{
        "agency_name":"Clanton Police Department",
        "agency_coords":{"lat": "32.83853", "lng":"-86.62936"},
        "agency_type" : 4,
        "city":"Clanton",
        "state": "AL",
        "zip":"35045",
        "county_fips":"01021"
    },
    "data": [
        {
            "dataset_id": "5740697099a311ebab258c8590d4a7fc",
            "url":"https://cityprotect.com/agency/540048e6ee664a6f88ae0ceb93717e50",
            "full_data_location":"data/cityprotect",
            "source_type": 3,
            "data_type": 10,
            "format_type": 2,
            "update_freq": 3,
            "last_modified": "2021-05-25 21:07:03.793049 +0000 UTC",
            "mapping":{
                "id": "__uuid__",
                "ccn":"ccn",
                "incidentDate": "date",
                ...
                "datasets_id": "__dataset_id__",
                "date_insert": "__date__"
            }
        }
    ]
}
```

### Fields

\*\*\*\*

* **agency\_id**: id of the agency in the agencies table
* **agency\_info**: This provides more information about the agency. If the ID is listed above and you change any information here, it will be automatically updated in the database if the script is ran again.
  * **`agency_name`**: name of the agency such as 'Gaston County Sheriff'
  * **`agency_coords`**: this will probably require you to search up on Google Maps. This is actually very important to ensure we pull the correct FIPS and municipal codes. Search the agency on google maps, and right click on the pin to grab the lat and long coordinates. It is okay if there are multiple districts, just grab the main district if so.
  * **`agency_type`**: the type of agency, using the codes found [here](https://www.dolthub.com/repositories/pdap/datasets/data/master/agency_types)
  * **`city`**: city of the agency \(leave blank if a county or state agency\)
  * **`state`**: two-letter state code \('IN', 'CA'\)
  * **`county_fips`**: FIPS code of the county \(can be left blank if lat and lng are filled in and it will auto search up the fips\)
* **data**: There can be multiple types of data from each agency, so this is an enumerable way to point to the different types of data stored. Store each type in a different directory such as `/incident_reports` , `/booking_reports` .etc.
  * **dataset\_id**: The ID from our list of datasets found [here](https://www.dolthub.com/repositories/pdap/datasets/data/master/datasets). If this is a new dataset not yet in our table, leave this blank and the ETL script will use the remaining information to add a record and automatically add the ID to the schema.json file.
  * **`url`**: the url of the dataset used
  * **full\_data\_location**: the location of all the data from the scraper. It will most likely just be in the `/data` directory in the same folder after the scraper has ran, just remove the first slash!
  * **source\_type**: use one of the values in the `id` column found in the source\_types table [here](https://www.dolthub.com/repositories/pdap/datasets/data/master/source_types)
  * **data\_type**: use one of the values in the `id` column found in the data\_types table [here](https://www.dolthub.com/repositories/pdap/datasets/data/master/data_types) \(such as `10` for `incident_reports` data\)
  * **format\_type**: use one of the values in the `id` column found in the format\_types table [here](https://www.dolthub.com/repositories/pdap/datasets/data/master/format_types) \(such as `2` for `cityprotect` data\)
  * **update\_freq**: use one of the values in the `id` column found in the format\_types table [here](https://www.dolthub.com/repositories/pdap/datasets/data/master/update_frequency) \(such as `3` for `quarterly` update\)
  * **last\_modified**: this will automatically be created if it does not exist. This is an important field that tells the script which data is more recent: the schema.json file or the data in the database. Whichever date is newer will be the source of truth. So if the schema.json is newer, it will use all the info in the file and update the database with it. If the datasets table is newer, it will overwrite the schema.json file on run.
  * **last\_updated**: This timestamp is important, the ETL will automatically update this from the database during merge. But if you manually edit the schema.json file, be sure to update this time!! The script will overwrite either the database or the schema.json file, whichever data is more recent takes priority and the older set will be overwritten
  * **mapping**: based off of your `data_type`, the data will be stored in a different table with different columns. This section is how your data maps to the columns in the database such as for `"table_col": "data_col"`
    * There are some magic mappings such as **\_\_uuid\_\_** , **\_\_dataset\_id\_\_** , and **\_\_date\_\_** that the ETL script will automatically generate and/or populate into the column

## Usage

With the `schema.json` file populated, we will have a library stored in `/common/etl` that will be able to use all of this information to translate the data with ease and add/locate/update the main dataset or agency to keep it in sync if anything changes. The schema file also points exactly where the output files are located, and tells the ETL library exactly how to map the files in terms of columns and the appropriate agency + dataset.



We currently have one working example for the[ /USA/CA/butte\_county/college/chico](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/tree/main/USA/CA/butte_county/college/chico) scrapers. Running the etl.py script will show how this works to clone the dolt repos, read from the schema.json, make the changes in a new branch, sync the database with the schema.json and then prepare for a commit. 

