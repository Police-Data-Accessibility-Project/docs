---
description: by Eric Turner
layout: editorial
---

# 5/28/21: Dolt → PostgreSQL

Richard was hard at work and created a foreign data wrapper (FDW) to access a cloned dolt instance and copy the data into our own [PostgreSQL instance](../../activities/data-sources/explore-pdap-data-sources/hadoop-datasets-mirror.md) that our applications run on.

The current implementation is that Dolt fires information over a webhook when a branch is pushed / merged. We can use this information to see exactly when a PR is merged into master and trigger a `dolt pull` and restart of our `dolt sql-server` instance. Then, a stored procedure will activate to load the new data into our PostgreSQL instance so we always have a stable, up-to-date, local copy.
