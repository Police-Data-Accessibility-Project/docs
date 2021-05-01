# Data Standardization

We're currently translating data from our [Scrapers](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/) to a unified format in [Dolt](../../tools/dolthub.md). We're translating the data at the point of collection.

## Current state

### Do I need to know how to write an ETL to help?

No, but someone will need to add one for us to use your data. If you need help, reach out in the \#scrapers slack channel.

### What are we translating to?

A unified format for each [data\_type](https://www.dolthub.com/repositories/pdap/datasets/data/master/data_types). Each has its own table in [data-intake](https://www.dolthub.com/repositories/pdap/data-intake). For example, to get the format of Incident Reports, run this in Dolt:

```sql
DESCRIBE `incident_reports`
```

## Future state

OCR, broader data type support. Pull columns together in a unified table.

