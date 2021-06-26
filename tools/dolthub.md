---
description: This is how we keep our data stream safe and accurate.
---

# DoltHub

## Getting Started with Dolthub

The instructions [here](https://docs.dolthub.com/dolthub/getting-started) are excellent as an intro to Dolt's general usage. Here’s our [dolt org](https://www.dolthub.com/organizations/pdap).

There's some great [video tutorial content](https://www.youtube.com/playlist?list=PL0F4rChlR1GiXabNeh6H0kwIStyPFSZLS) for using DoltHub if you learn best that way.

Anyone can create a Pull Request to be merged into the database via the SQL UI at DoltHub, [SQL editor integration](https://github.com/dolthub/docs/blob/gitbook-dev/content/integrations/sql-editors.md), command line, or Python.

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

Use `dolt add .` to start tracking all new files in the directory.

## Run two Dolt repos with sql-server

Dolt's documentation on this is [here](https://docs.dolthub.com/interfaces/cli#dolt-sql-server).

There are two ways to run the dolt server with multiple databases served in one instance, in which you can use `use db_name` to switch databases.

### Method 1

```text
dolt sql-server -H 0.0.0.0 -P 3306 -u root -p root123 --multi-db-dir /path_to_dir_that_hosts_multi_repos/
```

### Method 2

Create a config file, example.cnf:

```text
log_level: info

behavior:
  read_only: false
  autocommit: true

user:
  name: root
  password: "root123"

listener:
  host: 0.0.0.0
  port: 3306
  max_connections: 10
  read_timeout_millis: 28800000
  write_timeout_millis: 28800000
  
databases: 
  - name: richardji_datasets
    path: /home/oracle/work/pdap/dolt/richardji_datasets
  - name: rji_test
    path: /home/oracle/work/pdap/dolt/rji_test

performance:
  query_parallelism: null
```

Then run it with:

```text
dolt sql-server --config my2.cnf
```

