---
description: https://www.dolthub.com/repositories/pdap/data_sources
---

# What are Data Sources?

## Purpose

The Data Sources database is the critical foundation of the rest of our work. It helps us understand which data is available, and which is not.

Scrapers are designed to collect information from one or many Data Sources.

## Structure

Data Sources are maintained and can be easily viewed [in DoltHub](https://www.dolthub.com/repositories/pdap/data\_sources).

### Hierarchy

1. **Country**\
   ****_The United States has \~18,000 Agencies across all regions._
2. **Region**\
   ****_A state, county, municipality, or other region containing multiple police agencies._
3. **Agency**\
   ****_A specific police organization, typically containing many Data Sources._
4. **Data Source**\
   ****_A URL where one type of police data can be found._
5. **Scraper**\
   ****_A bit of code which downloads everything it can find on at least one Data Source._
