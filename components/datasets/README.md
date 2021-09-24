---
description: 'https://www.dolthub.com/repositories/pdap/datasets'
---

# Datasets

## Purpose

The datasets database is a utility we're always maintaining. It contains **known police datasets.** Each dataset has a status, and can potentially be scraped.

## Structure

Datasets are maintained and can be easily viewed [in DoltHub](https://www.dolthub.com/repositories/pdap/datasets). The same tables are in a Hadoop [PostgreSQL mirror](../../activities/data-collection/hadoop-datasets-mirror.md), which is a better back end for Scrapers. 

### Terms & Hierarchy

1. **Country** _The United States has ~18,000 Agencies across all regions._
2. **Region** _A state, county, municipality, or other region containing multiple police agencies._
3. \*\*\*\*[**Agency**](https://www.dolthub.com/repositories/pdap/datasets/data/master/agencies) ****_A specific police organization, typically containing many Datasets._
4. \*\*\*\*[**Dataset**](https://www.dolthub.com/repositories/pdap/datasets/data/master/datasets) ****_A URL where one type of police data can be found._
5. \*\*\*\*[**Scraper**](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers) ****_A bit of code which downloads everything it can find on a Dataset._

