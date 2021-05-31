---
description: Scrapers and ETLs
---

# Data Collection

## Purpose

Code automated scrapers or follow processes to manually collect data.

* Automated data scrapers regularly consolidate public police information. 
* Humans operate semi-automated processes to gather public information
* Facilitate data sharing by good-faith police organizations.

## Current state

The first batch of data into Dolt was uploaded manually. [Dolt does have an API](https://github.com/dolthub/doltpy).

We use Python to scrape data into a Hadoop server, long enough that it can be translated to the [submission format](https://www.dolthub.com/repositories/pdap/data-intake).

## Future state

Scrapers in [the PDAP-Scrapers repo](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers) are run on a schedule dictated by how often they're refreshed. People could also donate time and computing power to run them locally.

