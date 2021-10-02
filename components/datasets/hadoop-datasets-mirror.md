# PostgreSQL Datasets mirror

## Why would I use this?

A data scraper may not want to install DoltHub just to use the [Datasets repo](https://www.dolthub.com/repositories/pdap/datasets). DoltHub may conflict with other processes, or you may prefer to access an HDFS with Python. Accessing it as a more straightforward read-only file system is useful for some scrapers.

## How does it work?

hadoop-worker-1 is configured on a Digital Ocean droplet. It makes a mirror of the [Datasets db in Dolthub](https://www.dolthub.com/repositories/pdap/datasets/data/master/datasets) every time a merge is made.

### Read-only PostgreSQL credentials

Host: `167.71.249.20`  
Port: `5432`  
Database: `pdap_devdb`  
User: `pdap_public`  
Password: `SL$Eb+DuuZ2qv`

