# Submit Data Sources

## Introduction

Every police agency has one or many Data Sources, or URLs which hold data about the agency.

### Quick start

1. Head to the [Data Sources repo](https://www.dolthub.com/repositories/pdap/data\_sources) to see which datasets we already have.&#x20;
2. Find a web page on the agency site with potentially useful data.
3. Add your Data Source to the database with [web tools](submit-datasets-with-web-tools.md) or the [CLI](submit-datasets-with-cli.md).

&#x20;For example, take Alameda, California:

* The `agencies.homepage_url` is [https://www.alamedaca.gov/Departments/Police-Department](https://www.alamedaca.gov/Departments/Police-Department)
* One possible `data_sources.url` is [https://www.alamedaca.gov/Departments/Police-Department/Annual-Arrest-Traffic-Statistics](https://www.alamedaca.gov/Departments/Police-Department/Annual-Arrest-Traffic-Statistics)

### Lists of Datasets

This is a little meta: some Data Sources are lists of other Data Sources. They often [look like this](https://data.wprdc.org/organization/9ecaff80-fb4a-457b-8141-e53f7c991890?q=police\&organization=city-of-pittsburgh\&sort=score+desc%2C+metadata\_modified+desc).&#x20;

![](<../../../.gitbook/assets/Screen Shot 2022-01-22 at 2.57.53 PM.png>)

These have a Data Type of "list\_of\_data\_sources". This may be a good place to start when looking to add every dataset to a particular city.

### Agency with Multiple Different Data Types

The best case is when we get a link that is usually a directory or listing of files, a map with data on it, or a HTML table with data on it.\
\
First we need to pick an agency from the `agencies` table.

Let's see Alameda, California.  First we need to grab the agency id (either from the [web](https://www.dolthub.com/repositories/pdap/datasets/query/master?q=SELECT+\*%0AFROM+%60agencies%60%0Awhere+name+like+%27Alameda+Police%25%27+and+state\_iso+%3D+%27CA%27%0A%0A\&active=Tables) or sql) for later use\


![We will use the Police Department.](<../../../.gitbook/assets/image (2).png>)

So `5c2d0726d183487ba746402872573f42` is our agency id! Now we perform a google search for Alameda Police Department CA, and we find their [homepage](https://www.alamedaca.gov/Departments/Police-Department). We can also see in the above table that `homepage_url` is blank, so we can run a quick update to store this homepage!

```sql
UPDATE agencies SET homepage_url = 'https://www.alamedaca.gov/Departments/Police-Department' where id = '5c2d0726d183487ba746402872573f42';
```

\


![](<../../../.gitbook/assets/image (9).png>)

On the sidebar they have a button to **Review Crime Activity**! Perfect! Let's click on that!

![5 different types of data!](<../../../.gitbook/assets/image (10).png>)

Awesome! This particular link gives us 5 different types of data! We will want to capture each different [data type](https://www.dolthub.com/repositories/pdap/datasets/data/master/data\_types) in its own `data source` record, as the scraper for each data type will most likely be a bit different and the table the data goes into will also be different. So let's start cross-referencing the data-types with what we see on the page to build to our Data Sources!\


### Data Source Enumeration

Let's just go down the list of the 5 types we have for this agency.

#### Alameda Crime Graphics

![Crime Graphics](<../../../.gitbook/assets/image (11).png>)

The first accordion of this page has a link for crime graphics. When we click the button here, it takes us to a brand new link with incident reports, arrest logs, missing persons, daily bulletins and more! Unfortunately, this website does not change the URL when you click any of the links on the sidebar. So that means this data\_type is a `multi`, which we can find on our [data types reference list](https://www.dolthub.com/repositories/pdap/datasets/data/master/data\_types) as id `27` . This data being housed on an external source, makes it a `third party` source type, which [looking that up](https://www.dolthub.com/repositories/pdap/datasets/data/master/source\_types) is `3`. It's also a good idea to leave a note for a `multi` data type. The `status_id` for our purposes will always be `1` because you are just adding the dataset but not scraping it. Scrapers will update this column to show the status of each dataset later!\
\
We have many other columns we can fill out for a dataset, but most of which will be used by [data scrapers](broken-reference) in their task, so it's not completely necessary to do now, unless you really want to!

\
The `datasets` table will automatically generate the `id` for you if you do not specify it. However, if you really wish to specify it yourself: you can use the sql function `REPLACE(uuid(), '-', '')` (which can be found via this [link](https://www.dolthub.com/repositories/pdap/datasets/query/master?q=SELECT+REPLACE%28uuid%28%29%2C+%27-%27%2C+%27%27%29%3B%0A%0A\&active=Tables)). This will always be a random string of letters and numbers, so for me I received `c813aab6ba3d11ebb082927cb9e1207c`. You also would need to specify it in the statement below such as `INSERT INTO  datasets (id, url ...)`.

```
INSERT INTO datasets 
(url, status_id, data_types_id, source_type_id, agency_id, notes)
VALUES
(
    'https://alameda.crimegraphics.com/2013/default.aspx',
    1,
    27,
    3,
    '5c2d0726d183487ba746402872573f42',
    'CrimeGraphics: Incident Reports, Arrest Logs, Missing Persons, Daily Bulletins'
);
```

#### Alameda Crime Statistics

Just like above, let's go to the next accordion menu of Crime Statistics:

![](<../../../.gitbook/assets/image (8).png>)

This provides us with another link, but this time the link is still on the official agency webpage. Looking back at our source types page: we would now use `2` for a `direct` source type. Now we look again at the data types and we find `24` which is `annual_reports`. And we are ready to insert!

```
INSERT INTO datasets 
(url, status_id, data_types_id, source_type_id, agency_id)
VALUES
(
    'https://www.alamedaca.gov/Departments/Police-Department/Annual-Crime-Stats',
    1,
    24,
    2,
    '5c2d0726d183487ba746402872573f42'
);
```

#### PDFs

The final example I wanted to touch is a `multi` data type for PDFs. We can see the 3rd and 5th accordion: Monthly Crime Statistics and Policty and Hate Crimes Reports. The `url` in the `datasets` table must be unique, so we cannot simply paste the url twice for both datatypes. In this case we need to use data type `27` again for `multi`, we can use `2` for a `direct` source type again, and gen a new id. The difference for this is I will leave a note of what the `multi` entails.

```
INSERT INTO datasets 
(url, status_id, data_types_id, source_type_id, agency_id, notes)
VALUES
(
    'https://www.alamedaca.gov/Departments/Police-Department/Crime-Activity',
    1,
    27,
    2,
    '5c2d0726d183487ba746402872573f42',
    'PDFs for Crime Stats (23), Policy & Hate Crimes Reports'
);
```

We just need to do the 4th accordion, and then we can push our data in a PR or we can start back over and pick another agency!\
\
You can also verify the records you added in your sql instance where you're working:\
`select * from datasets where agency_id='5c2d0726d183487ba746402872573f42' and date_insert >= '2021-05-21'` it will grab all of the records for the current agency, and the `date_insert` will help in case the agency you are working with already had a previous record added but you found more!

