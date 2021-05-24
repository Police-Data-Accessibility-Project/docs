---
description: >-
  If you're scraping a Dataset we don't yet know about, it needs to exist in
  this table first.
---

# Submit or update Datasets

## Dolt SQL Editor

You can use SQL statements to add new datasets right in Dolt. It's possible to generate these Insert statements from spreadsheets or write them manually.

### Using spreadsheets

1. Make a copy of the [Dataset Submission Template](https://docs.google.com/spreadsheets/d/1qh-6pb6KoIFSQ9qyyzd_bZIOosD74Sg21VPjbOQ5j3g/edit#gid=494854000) and populate information about new datasets as you work.
2. Use the [Dataset Properties](find-a-dataset-id/) guide to find the appropriate IDs.
3. Navigate to the Query table and note that each row generates a new SQL query.
4. Fork the [DoltHub Datasets repo](https://www.dolthub.com/repositories/pdap/datasets). If you don't yet have an account, sign up [here](https://www.dolthub.com/signin).
5. Paste the queries individually into your fork's SQL console and run them.
6. When you're done, [create a new Pull Request](https://www.dolthub.com/repositories/pdap/datasets/pulls/new) against our repository by selecting your fork as the from repository.
7. Join [Dolt's Discord](https://discord.gg/Zpu8x4JA) and ask in the \#data-bounties channel for someone to approve it.

![](../../../.gitbook/assets/screen-shot-2021-05-02-at-12.10.13-am.png)

## CLI

> This process is currently tricky due to column defaults. If you can improve these docs, click the link in the upper right to Edit on GitHub.

1. [Install Dolt](https://docs.dolthub.com/getting-started/installation).
2. Fork the project to your DoltHub account (you will need to [create an account](https://www.dolthub.com/signin) if you don't have one).
3. Clone down your copy of the repository.

   ```text
   dolt clone <your account name>/datasets && cd datasets
   dolt table export datasets > datasets.csv
   ```

4. Open the `datasets.csv` file, make changes, and save. Leave `id` blank—UUIDs are generated automatically. Make sure you're not adding a URL that already exists.

   ```text
   dolt branch <branch name e.g. add-CA-counties>
   dolt checkout <your branch>
   dolt table import -u datasets datasets.csv
   ```

5. Run this command to add your csv to your checked out branch.

   ```text
   dolt add .
   ```

6. Push the commit.

   ```text
   dolt commit -m “<message e.g. added 5 Alameda County datasets>”
   dolt push --set-upstream origin <your branch>
   ```

7. Head to [https://www.dolthub.com/repositories/pdap/datasets/](https://www.dolthub.com/repositories/pdap/datasets/).
8. Create a [new Pull Request](https://www.dolthub.com/repositories/pdap/datasets/pulls/new) to merge your dataset into `master`. Select your fork as the from repository, and then your branch will appear as an option. Read more about DoltHub Pull Requests [here](https://docs.dolthub.com/dolthub/getting-started#pull-requests).
