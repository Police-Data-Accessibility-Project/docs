---
description: by Eric Turner
---

# 5/26/21: ETL Prototype

The GitHub PR is [here](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/pull/113).

The data that was loaded is from the USA/CA/butte\_county/college/chico scraper. I chose this as a starting point because it has two different types of data, with two differing formats. This allowed me to verify the library reads from the schema.json properly and can load and map no matter the data output. You can find that PR [here](https://www.dolthub.com/repositories/pdap/data-intake/pulls/7/compare). It also created 2 new datasets [here](https://www.dolthub.com/repositories/pdap/datasets/pulls/39).

We currently have it set to not auto-commit so someone reviews before committing each time. But it does load data from files, use the schema.json file and \(mostly\) works!

Current Process:

1. Call the `/common/etl` library from a specific scraped agency dir, pass the `schema.json` file to it.
2. The library will locally clone the `pdap/datasets` and `pdap/data-intake` repos
3. Then it will verify the `agency_id` exists and will grab the appropriate record from the database
4. Next it will enumerate over the `data` items in the `schema.json`. It will create any datasets where the id is null, otherwise it will find an existing dataset and sync the data from the table with the `schema.json`. Whichever source has the most recent `last_modified` time will be the “Source of Truth” and that’s the data that will be used to sync.
5. It will do the same for the `data`.`mapping` object, it will search for a table in `pdap/data-intake` with the exact name of the `data_type` and then sync the columns so they are there. If a new column is in the database but not the schema.json file, it will add the missing column with a `__skip__` value.
6. Once everything has been synced, it will finally enumerate over the `mapping` object and insert the data into `pdap/data-intake`. Erroneous records are skipped a message displayed to the console.
7. The schema.json is overwritten in the directory with the synced changes from the database.

