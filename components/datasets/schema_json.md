---
description: Connecting Scrapers and Datasets.
---

# Scraper Schemas

## Overview

Scrapers are best understood by the Dataset they are scraping. The Datasets database is normalized, so it's not easy to tell at a glance what properties a dataset has \(unless you have memorized what `agency_id = 73e93439e6bf4ffc8b3f931a86fa3ad0` or `data_type = 4` means.

The `schema.json` file in the root of each Scraper folder gives us two things:

1. Human- and machine-readable information about each Scraper.
2. The ability for data collectors to quickly update the [Datasets database](./) while submitting or updating Scraper code.

## Usage

With the `schema.json` file populated, we can keep Dataset and Agency information in sync without forcing volunteers to use DoltHub. The schema file also points exactly where the output files are located, and tells the ETL library how to map tabular data.

We currently have one working example for the[ /USA/CA/butte\_county/college/chico](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/tree/main/USA/CA/butte_county/college/chico) scrapers. Running the `etl.py` script will clone the DoltHub repos, read from the `schema.json`, make the changes in a new branch, sync the database with the `schema.json` and prepare for a commit.

## Schema example & definitions

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

| Field | Description |
| :--- | :--- |
| `agency_id` | The `agencies.id` column |
| `agency_info` | Information changed here will be updated in the datasets table the next time the ETL script is run. |
| `agency_name` | The `agencies.name` column. |
| `agency_coords` | The latitude and longitude coordinates from the main agency building. |
| `city` | Not applicable for county or state agencies. |
| `state` | Two-letter ISO code \(e.g. "IN" or "CA"\) |
| `county_fips` | If `agency_coords` is populated, this will be populated automatically. You can also look it up manually from the `counties` table. |
| `data` | Most agencies have multiple [Datasets](./). |
| `dataset_id` | If you're scraping an existing dataset, add the id here. |
| `url` | The `datasets_url` column. |
| `full_data_location` | The location of the scraper Extraction. This is typically the `data` directory at the top level of the Scraper. |
| `source_type` | The `source_types.id` column. |
| `data_type` | The `data_types.id` column. |
| `update_freq` | The `update_frequency.id` column. |
| `last_modified` | In most cases, leave this blank and it will be filled in automatically. The script will update either the `schema.json` file or the `datasets` db if the value in the other location is more recent. |
| `mapping` | If you're scraping tabular data with a `data_type` that exists in the `data_intake` database, use these fields to map columns in your Extraction to columns in `data_intake`.`__uuid__` , `__dataset_id__` , and `__date__` will be automatically overwritten by the script.  |

