---
description: This happens the first time we accept data for a given type.
---

# Create a new data\_type

The first time we accept data for a new data\_type, we need to create the schema. Run this in Dolt and then make a Pull Request.

1. Create the Schema in [data-intake](https://www.dolthub.com/repositories/pdap/data-intake).

   ```sql
   CREATE TABLE `table_name` (
   --these fields are required:
     `id` varchar(32) NOT NULL DEFAULT (replace(UUID(), "-", "")),
     `datasets_id` varchar(32),
     `date_insert` datetime DEFAULT NOW(),
   --add the rest of the columns here:
     `exampleField` varchar(255),
     PRIMARY KEY (`id`)
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4
   ```

2. Add it to the `data_types` table [in the Datasets repo](https://www.dolthub.com/repositories/pdap/datasets/data/master/data_types).

   ```sql
   INSERT INTO data_types
   VALUES (30, "data_type_name", "This is a human-readable explanation.")
   ```

