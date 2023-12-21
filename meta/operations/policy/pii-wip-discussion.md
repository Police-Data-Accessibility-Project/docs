---
description: Also known as PII
---

# Personally Identifiable Information

## Defining PII

#### [2 CFR § 200.79](https://www.law.cornell.edu/cfr/text/2/200.79)

> \[...] for example, first and last name, address, work telephone number, email address, home telephone number, and general educational credentials. The definition of PII is not anchored to any single category of information or technology. Rather, it requires a case-by-case assessment of the specific risk that an individual can be identified. Non-PII can become PII whenever additional information is made publicly available, in any medium and from any source, that, when combined with other available information, could be used to identify an individual.

This definition of public data is also supported in [HiQ Labs v. LinkedIn](https://en.wikipedia.org/wiki/HiQ\_Labs\_v.\_LinkedIn#cite\_note-1).

## Goals

We want people to feel sound ethically and legally when they contribute to PDAP. To that end, these are our goals:

1. Draw a “[bright line](https://en.wikipedia.org/wiki/Bright-line\_rule)” from our [Data Sources Database](../../../activities/data-dictionaries/data-sources-database.md) to the source material. We are not altering public records, we are helping people find them.
2. Avoid aggregating already-public PII in a way that would make it more usable (e.g. turning arrests from different jurisdictions into a unified database). [Citation](https://papers.ssrn.com/sol3/papers.cfm?abstract\_id=2678420).
   * We don't want to become or facilitate a database of people impacted by the legal system.
3. Strive for completion, and not be accused of editorializing by omission.&#x20;
   * The board decided [submitting PII is allowed](../staff/board-resolutions/personally-identifiable-information.md).
   * We can track whether a given Data Source contains PII.&#x20;
   * PII collection is not required. If we aggregate data, we can choose to omit PII like `name` and `address` because those properties do not become statistically useful in aggregate, only dangerous.
4. Transparency in our published resources and information.
   * Our open-source tools are transparent in how they work.
   * Documentation about published data and tools should be clear about any properties which are collected—or left behind—and why the decision was made.
