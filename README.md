---
description: We're making a unified archive—a source of truth—for police data.
---

# Welcome to PDAP!

## How do we work?

We're a rotating cast of volunteers with a flat organizational structure. Our goal is to collect public police data, and there's a lot of it. If you're reading this, there is still work to do.

We're a learning organization, and **we want to hear from you.** If you have questions, concerns, suggestions, or expertise, reach out in [Discord](https://discord.com/invite/cn2ZpVTdw7).

## Crash Course on our process

1. Known police agencies are added to our `agencies` table [in Dolt](https://www.dolthub.com/repositories/pdap/datasets/data/master/agencies). _For example, "St. Louis County Police Department" or "University of Cincinnati Department of Public Safety"._
2. Datasets associated with an agency are added to our `datasets` table [in Dolt](https://www.dolthub.com/repositories/pdap/datasets/data/master/datasets). _For example, an agency might have both "Crime Statistics" and "Use of Force reports". Each of these is a Dataset._
3. Volunteers write [Scrapers ](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers)for each Dataset. Often they're similar enough that Scrapers can be reused with slight modification.
4. Scraped data in table format is submitted to the `data-intake` database [in Dolt](https://www.dolthub.com/repositories/pdap/data-intake). _We're still working on support for non-tabular data._

## How to get involved

### Collect Data

We need [contributions to our library of known datasets](https://www.dolthub.com/repositories/pdap/datasets/doc/master). You can help build a database of police agencies for a community of data collectors!

If there are DoltHub Pull Requests pending, you can [run these utilities to check incoming data](https://github.com/Police-Data-Accessibility-Project/PDAP-app/blob/main/utilities/Datasets%20Submission%20Checker/README.md). Accelerate the data intake process!

### Contribute Code

Know python? [Contribute to our **Data Scrapers repo**](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/blob/master/CONTRIBUTING.md).

[Head to the GitHub Roadmap](https://github.com/orgs/Police-Data-Accessibility-Project/projects/17) to work on infrastructure issues.

### Donate to PDAP

**Donate on** [**PayPal**](https://www.paypal.com/biz/fund?id=SLS5DB8SMDC3G) **or** [**Patreon**](https://patreon.com/pdap)**,** and we'll spend it on [Data Bounties](https://docs.pdap.io/updates/blog/may-2021-dolt-bounty) and infrastructure improvements. Small recurring donations are most helpful. Stability helps us chart a path.

### Use our Data

[Our data lives in DoltHub](https://www.dolthub.com/organizations/pdap). What can you learn from it? How could it be better?

### Join the Community

Head to **\#introduce-yourself** in [our Discord server](https://discord.gg/cn2ZpVTdw7) to say hello, ask questions, and meet fellow data nerds.

