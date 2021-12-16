# Data Standardization

{% hint style="info" %}
Standardation and translation to a unified format is not mission-critical: we believe the simple act of collecting raw data extractions in one place will be an unprecedented resource for public good.
{% endhint %}

## Purpose

Normalize raw data into a unified format. This is part of what makes data useful at a large scale.

## Current state

We're currently translating data from some [Scrapers](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/) to a unified format in [Dolt](../../tools/dolthub.md). We're translating the data at the point of collection, in addition to saving the raw extractions.

### What are we translating to?

A unified format for each [data\_type](https://www.dolthub.com/repositories/pdap/datasets/data/master/data\_types). Each has its own table in [data-intake](https://www.dolthub.com/repositories/pdap/data-intake). For example, to get the format of Incident Reports, run this in Dolt:

```sql
DESCRIBE `incident_reports`
```

## Future state

OCR, broader data type support. Pull columns together in a unified table.
