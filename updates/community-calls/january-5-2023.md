# January 5, 2023

## Updates from PDAP

* The new [https://pdap.io](https://static1.squarespace.com/static/627c29c0bcb7f5543e9f8ed1/t/627d35687db3d00c1c66b432/1652372841540/072621\_2020\_PMP\_report.pdf) front page points people to the new "request data" workflow.
  * We've been doing this informally already—we'd like to get more requests, so we can better understand the kinds of things people are looking for and make more of an impact.
* We're making good progress on turning our Airtable tools into a home-grown app. There's now a [public repo](https://github.com/Police-Data-Accessibility-Project/data-sources-mirror) which mirrors our Data Sources database as CSV and JSON.
* We're working on ways to identify URLs en masse.
  * GitHub issue: [https://github.com/Police-Data-Accessibility-Project/planning/issues/196](https://github.com/Police-Data-Accessibility-Project/planning/issues/196)
  * A volunteer wrote a sitemap scraper, which locates potentially useful URLs given a list. It's an open PR still under review. We want to get it merged soon: [https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/pull/195/files](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/pull/195/files)
  * We did a Doccano labeling exercise in an attempt to train a machine learning algorithm to identify content based on URL. We still need to experiment in order to close the loop on this.

## Call notes

* Stocking's regex script
  * "linklabel" (C++) scans massive amounts of URLs for keywords
  * early bottleneck: commoncrawl URL database is \~4TB
  * to do:
    * publish the script + regex library
    * generate lists of URLs
    * get a good list of regex keywords set in advance
    * crunch through the URLs
    * ???
* Elasticsearch
  * Supports [stemming](https://www.elastic.co/guide/en/elasticsearch/reference/current/stemming.html)
* Commoncrawl storage
  * craeft offered to spin up a 4-5TB linux server to hold mass amounts of URLs
