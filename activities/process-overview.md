# Process overview

We're constantly iterating on each of these components, and there's always work to do. If you have ideas, reach out in Discord!

## Structure

These terms are [defined here](terms-definitions.md).

```
Agencies
  Data Sources
    Scrapers
      Extractions      
```

**Agencies** can contain many **Datasets**; each dataset has one **Scraper**; each time a scraper is run, it generates an **Extraction**.

## Data lifecycle

There's [a flowchart here](https://pdap.invisionapp.com/freehand/Data-intake-flow-Q01qjpCvN) which covers the end-to-end data submission process.

### Scraping

The [process for writing Data Scrapers is here](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/blob/main/CONTRIBUTING.md). Writing a data scraper typically takes a handful of hours, but can be accelerated to just a few minutes by using common code to gather similar records.
