---
description: The ability to audit our data pipeline is critical.
---

# Data Chain of Custody

This is currently managed by the [Dolt flow](https://www.dolthub.com/) itself. Dolt is built for large-scale data collaboration, and our first line of defense against corrupted data is robust version history and branch protection.

Scrapers live side-by-side with ETL files. Data is scraped to a temporary [Hadoop](https://en.wikipedia.org/wiki/Apache\_Hadoop) worker where it can be translated by the `etl.py` file to a common data schema. Since GitHub is a version control tool, we'd be able to reconstruct what a scraper or ETL file looked like at any time in the past for auditing purposes.

Learn more in [Data Standardization](broken-reference).
