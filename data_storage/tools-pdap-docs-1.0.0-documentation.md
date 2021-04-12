---
description: This is how we keep our data stream safe and accurate.
---

# DoltHub

## Getting Started with Dolthub

The instructions [here](https://docs.dolthub.com/dolthub/getting-started). are excellent. Here’s our [dolt org](https://www.dolthub.com/organizations/pdap).

Generally, Dolt is used to make changes to PDAP. Anyone can create a Pull Request to be merged into the database via the SQL UI at DoltHub, [SQL editor integration](https://github.com/dolthub/docs/blob/gitbook-dev/content/integrations/sql-editors.md), command line, or Python.

### Supported statements

[https://docs.dolthub.com/interfaces/sql/sql-support/supported-statements](https://docs.dolthub.com/interfaces/sql/sql-support/supported-statements) These are limited, so dolt is not great for managing a bunch of schemas.

### Useful statements

**Spreadsheets**

Dolt has a [guide here](https://docs.dolthub.com/integrations/spreadsheets) for spreadsheets generally, including ODBC setup. Using the CLI, first ensure you’ve initialized the repo you’d like to pull from. Export a table like this:

```text
dolt table export source_types > source_types.csv
dolt table export <table_name> > <file_name>
```

Add new files

```text
dolt table import -c --pk <primary_key> <table_name> <file_name>
dolt table import -c --pk name format_types format_types.csv
```

Use dolt add . to start tracking all new files in the directory.

## Submit a new dataset

### DoltHub CLI

1. [Install Dolt](https://docs.dolthub.com/getting-started/installation).
2. Run these commands to init the project locally

```text
dolt init
dolt clone pdap/datasets && cd datasets
dolt table export datasets > datasets.csv
```

1. Open the datasets.csv file, make changes, and save.

   URL must be unique. Some fields are required.

2. Run the following commands

```text
dolt branch <branch name e.g. add-georgia-counties>
dolt checkout <your branch>
dolt table import -u datasets datasets.csv
```

_There are often errors at this stage, typically related to non-unique URLs or missing fields which must be present._

1. Run this command

```text
dolt add .
```

_The “.” is important._

1. Push the commit

```text
dolt commit -m “<message e.g. added 5 counties>”
dolt push --set-upstream origin <your branch>
```

1. Head to [https://www.dolthub.com/repositories/pdap/datasets/](https://www.dolthub.com/repositories/pdap/datasets/)
2. Create a [Pull Request](https://docs.dolthub.com/dolthub/getting-started#pull-requests) to merge your dataset into master.

