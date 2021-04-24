---
description: Scrapers and ETLs
---

# Data Collection

## Current state

The first batch of data into Dolt was uploaded manually. [Dolt does have an API](https://github.com/dolthub/doltpy).

We use Python to scrape data into a Hadoop server, long enough that it can be translated to the [submission format](https://www.dolthub.com/repositories/pdap/data-intake).

## Future state

Scrapers in [the PDAP-Scrapers repo](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers) are run on a schedule dictated by how often they're refreshed.

