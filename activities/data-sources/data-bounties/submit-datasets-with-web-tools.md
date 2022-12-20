---
description: >-
  Use this if you'd like to manually enter Data Sources for any reason or don't
  know much about the command line. This is quicker than setting up DoltHub
  locally.
---

# Submit Data Sources with web tools for a Data Bounty

## Dolt SQL Editor

You can use SQL statements to add new Data Sources right in Dolt. It's possible to generate these Insert statements from spreadsheets or write them manually.

> Note: CSV uploads via the DoltHub UI are not working well for this process. Use at your own risk.

### SQL INSERT statement generator

1. Make a copy of [this google spreadsheet](https://docs.google.com/spreadsheets/d/1qh-6pb6KoIFSQ9qyyzd\_bZIOosD74Sg21VPjbOQ5j3g/edit?usp=sharing). **Your goal is to fill in the grey columns for each row!**
2. Use the [Data Sources Properties](broken-reference) guide to find the appropriate IDs. You can also keep another DoltHub tab open for reference.
3. **Navigate to the Query tab.** Each row generates a new SQL query!
4. Head to the [DoltHub Data Sources repo](https://www.dolthub.com/repositories/pdap/data\_sources). If you don't yet have an account, sign up [here](https://www.dolthub.com/signin).
5. Paste the queries individually into the SQL console and run them.
6. When you're done, [create a new Pull Request](https://www.dolthub.com/repositories/pdap/data\_sources/pulls/new) against our repo.
7. Join [our Discord](https://discord.gg/wMqex8nKZJ) and ask in the #data-sources channel for someone to approve it!

![](../../../.gitbook/assets/screen-shot-2021-05-02-at-12.10.13-am.png)

