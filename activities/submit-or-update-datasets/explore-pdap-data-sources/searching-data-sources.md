# Searching Data Sources in DoltHub

You can enter these queries into DoltHub or any other SQL browser to locate Agencies and Data Sources.

## Find Agency IDs

```sql
--find agencies by city name
SELECT * FROM `agencies` WHERE `city` like "%Juneau%"

--find agencies by state
SELECT * FROM `agencies` WHERE `state_iso` = "NJ"

--find agencies by county
SELECT * FROM `agencies`
JOIN counties ON agencies.county_fips=counties.fips
WHERE `counties.name` LIKE "%Bibb%"
```

## Find Data Sources by Agency

```sql
--find data_source id by city
SELECT *
FROM `data_sources` 
JOIN `agencies` ON agencies.id = data_sources.agency_id
WHERE agencies.city LIKE "%Antioch%"

--find data_source id by state
SELECT *
FROM `data_sources` 
JOIN `agencies` ON agencies.id = data_sources.agency_id
WHERE agencies.state_iso = "MD"

--find data_source id by county name
SELECT *
FROM `data_sources`
JOIN `agencies` ON agencies.id = data_sources.agency_id
JOIN `counties` ON counties.fips = agencies.county_fips
WHERE counties.name LIKE "%Bibb%"

--find data_source by agency id
SELECT *
FROM `data_sources`
WHERE `agency_id` = "b27ae147ba004dec875eeaa5259ebb57"
```
