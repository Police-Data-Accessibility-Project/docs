# Datasets schema

![Overview of the Proposed Schema in DoltHub](../../.gitbook/assets/image.png)

The `agencies` table prevents redundancy in `datasets` and establishes a true one-to-many relationship \(one agency may have many associated datasets\). Agencies are described by their location and whether the

* remove hard-coded `update_frequency` column from `datasets` table and create a normalized link to `update_frequency` table
* creation of a new `agency_types` table to enforce normalization
  * remove hard-coded `aggregation_type`column from `datasets`, migrated to `agencies` table as `agency_type` and created a link to `agency_types` table
* * `update_frequency`: annual, semi-annual, quarterly, monthly, weekly, daily
* `agency_types`: federal, state, municipal, university

