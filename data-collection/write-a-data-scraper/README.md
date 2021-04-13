---
description: >-
  Data can be found from a vast array of sources. Scrapers automate manual human
  effort.
---

# Write a data scraper

## Overview

You’re going to program a [legal data scraper](../../meta/legal-1/legal-data-scraping.md) and process a sample data file. For example, you could be using Python to turn a PDF of police activities into JSON, or making recurring API calls to pull down files.

### Find a dataset to scrape.

Navigate to our [Dataset Catalog](https://www.dolthub.com/repositories/pdap/datasets) and find a source to scrape, or add your own. If this is your first time using Dolt, you can [reference our primer](../../data-storage/dolthub.md).

### Get set up locally.

Clone the [Scrapers repo](https://github.com/Police-Data-Accessibility-Project/Scrapers). Make a copy of the `template` folder in the appropriate jurisdiction folder.

### Code your scraper.

The most important thing here is that your scraper is grabbing public police data, and is [legal](../../meta/legal-1/legal-data-scraping.md).

#### Scraper requirements

1. It's [legal](../../meta/legal-1/state-computer-crimes-laws.md).
2. The config file appropriately references a dataset.
3. Include a truncated version of some sample data so we understand what is generated.

Your submission doesn't need to be set up to recur. We can handle that when we run it periodically!

#### Scalability

Check the `common` folder for helpful assets, and be sure to add your own as you work to keep things scalable. Try not to repeat yourself—but keep in mind that we can always refactor your work later if necessary.

#### Readme

The best way to be a good PDAP citizen is to populate the readme for your scraper with as much helpful information as you can!

#### Structure

Stick to the format of `USA/$STATE/$COUNTY/$RECORD_TYPE`. If there are state-level records being scraped, use `USA/$STATE/_State/$RECORD_TYPE`. Use underscores rather than spaces or dashes.

### Submit your work.

Make a PR and request approval from the \#scrapers Slack channel!

## Approving Scrapers

Anyone is welcome to approve scrapers. Your approval means you think the scraper is legal. Style suggestions are welcome, but the reality is that we're aiming at a moving target: a working scraper can be broken at any moment by changes made in a jurisdiction. **Approve legal scrapers.**

1. Review the scraper for [legal risk](https://pdap-docs.readthedocs.io/en/latest/volunteers/resources/legal_restrictions.html). This is the most important approval criteria.
2. Does the sample data look sane and accurate? Is it legal? If so, approve it!
3. Make a comment if you have style or scale suggestions. Better, share your skills by making a PR to improve the work of someone else!

## Scraper FAQ

> What kind of data are we scraping?

Police data that's already made public by a government jurisdiction.

> What languages are allowed?

Python is preferred. If you use another language, we may not be able to easily fold it into our infrastructure.

