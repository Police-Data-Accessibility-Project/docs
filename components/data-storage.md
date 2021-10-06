---
description: 'Archival, verifiable, secure.'
---

# Data Storage

## Purpose

Archival, verifiable, and secure data storage is the core of our mission.

### Three pillars

1. An **Intake Database** where data can be dropped by the public. The public may also find unprocessed data. This raw archive is the cornerstone of our ability to audit any data we publish.
2. A **Gold Standard Database**, the unified archive managed by the PDAP community. Volunteers can contribute with machine learning, ETL, and manual processing to make the source material more useful. _This is where_ [_PII is removed_](../meta/policy/pii-wip-discussion.md)_._
3. A public-facing **Data Access Point**. This is where the data collection community meets the needs of the data consumer community.

## Current state

| Intake Database | Gold Standard | Data Access point |
| :--- | :--- | :--- |
| Hadoop | WIP / See [Data Standardization](data-standardization/) | [DoltHub](../tools/dolthub.md) for tabular data |

### Why Dolt?

We don't yet have much data in permanent storage, so [Dolt](../tools/dolthub.md) fulfills our requirements until we outgrow it or need more than it offers in some critical area.

### Why Hadoop?

Dolt can't store unprocessed data, so we are going to scale by using Hadoop servers.

Servers are configured as Digital Ocean droplets. There's no user-level authentication, so we don't have an edit history yet. Only DoltHub's data should be considered auditable.

Scrapers can be run from one of our Digital Ocean boxes. We haven't solved authentication here yet.

## Future state

![](../.gitbook/assets/pdap_architecture.jpeg)



