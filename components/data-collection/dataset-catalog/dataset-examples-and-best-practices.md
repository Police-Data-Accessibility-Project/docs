---
description: What exactly constitutes a 'dataset' ?
---

# Dataset Examples & Best Practices

## Introduction

You may be wanting to [submit a new dataset](submit-or-update-datasets.md) to scrape, but are unsure of some of the fields needed. Or perhaps what URL do you use? This guide is for you!



## Useful Links & SQL

This tutorial will refer to several tables or dolthub links. Here are the common tables you will be either querying in SQL or referencing on the website in one place:

* data\_types: [Online](https://www.dolthub.com/repositories/pdap/datasets/data/master/data_types) or `select * from data_types` 
* source\_types: [Online](https://www.dolthub.com/repositories/pdap/datasets/data/master/source_types) or `select * from source_types`
* id generator: [Online](https://www.dolthub.com/repositories/pdap/datasets/query/master?q=SELECT+REPLACE%28uuid%28%29%2C+%27-%27%2C+%27%27%29%3B%0A%0A&active=Tables) or `SELECT REPLACE(uuid(), '-', '');`
  * Note, you can also generate one from python shell, using the uuid v4 generator \(which is better than SQLs default gen\):

```text
~/ > python3

Python 3.9.4 (default, Apr  5 2021, 01:50:46)
>>> from uuid import uuid4
>>> str(uuid4()).replace('-', '')
'adaf2c5b17404300a5fb5a6501567f61'
```



## Tutorial - Agency with Multiple Different Data Types

The best case is when we get a link that is usually a directory or listing of files, a map with data on it, or a HTML table with data on it.  
  
First we need to pick an agency from the `agencies` table.

Let's see Alameda, California.  First we need to grab the agency id \(either from the [web](https://www.dolthub.com/repositories/pdap/datasets/query/master?q=SELECT+*%0AFROM+%60agencies%60%0Awhere+name+like+%27Alameda+Police%25%27+and+state_iso+%3D+%27CA%27%0A%0A&active=Tables) or sql\) for later use  


![We want the Police Department in this case](../../../.gitbook/assets/image%20%287%29.png)

So `5c2d0726d183487ba746402872573f42` is our agency id! Now we perform a google search for Alameda Police Department CA, and we find their [homepage](https://www.alamedaca.gov/Departments/Police-Department).  


![](../../../.gitbook/assets/image%20%289%29.png)

We see on the sidebar they have a button to **Review Crime Activity**! Perfect! Let's click on that!

![5 different types of data!](../../../.gitbook/assets/image%20%2810%29.png)

Awesome! This particular link gives us 5 different types of data! We will want to capture each different [data type](https://www.dolthub.com/repositories/pdap/datasets/data/master/data_types) in its own `dataset` record, as the scraper for each data type will most likely be a bit different and the table the data goes into will also be different. So let's start cross-referencing the data-types with what we see on the page to build to our datasets!  


### Dataset Enumeration

Let's just go down the list of the 5 types we have for this agency.

#### Alameda Crime Graphics

![Crime Graphics](../../../.gitbook/assets/image%20%2811%29.png)

The first accordion of this page has a link for crime graphics. When we click the button here, it takes us to a brand new link with incident reports, arrest logs, missing persons, daily bulletins and more! Unfortunately, this website does not change the URL when you click any of the links on the sidebar. So that means this data\_type is a `multi`, which we can find on our [data types reference list](https://www.dolthub.com/repositories/pdap/datasets/data/master/data_types) as id `27` . This data being housed on an external source, makes it a `third party` source type, which [looking that up](https://www.dolthub.com/repositories/pdap/datasets/data/master/source_types) is `3`. It's also a good idea to leave a note for a `multi` data type. We have many other columns we can fill out for a dataset, but most of which will be used by [data scrapers](../resources-for-scrapers/) in their task, so it's not completely necessary to do now, unless you really want to!

One final step is to generate ourselves a new `id` to use. We can use the sql function `REPLACE(uuid(), '-', '')` \(which can be found via this [link](https://www.dolthub.com/repositories/pdap/datasets/query/master?q=SELECT+REPLACE%28uuid%28%29%2C+%27-%27%2C+%27%27%29%3B%0A%0A&active=Tables)\). This will always be a random string of letters and numbers, so for me I received `c813aab6ba3d11ebb082927cb9e1207c`. Now we are ready to insert!

```text
INSERT INTO datasets 
(id, url, data_types_id, source_type_id, agency_id, notes)
VALUES
(
    'c813aab6ba3d11ebb082927cb9e1207c',
    'https://alameda.crimegraphics.com/2013/default.aspx',
    27,
    3,
    '5c2d0726d183487ba746402872573f42',
    'CrimeGraphics: Incident Reports, Arrest Logs, Missing Persons, Daily Bulletins'
);
```

#### Alameda Crime Statistics

Just like above, let's go to the next accordion menu of Crime Statistics:

![](../../../.gitbook/assets/image%20%288%29.png)

This provides us with another link, but this time the link is still on the official agency webpage. Looking back at our source types page: we would now use `2` for a `direct` source type. Now we look again at the data types and we find `24` which is `annual_reports`. Finally, we generate a new id again: `adaf2c5b17404300a5fb5a6501567f61`. And we are ready to insert!

```text
INSERT INTO datasets 
(id, url, data_types_id, source_type_id, agency_id)
VALUES
(
    'adaf2c5b17404300a5fb5a6501567f61',
    'https://www.alamedaca.gov/Departments/Police-Department/Annual-Crime-Stats',
    24,
    2,
    '5c2d0726d183487ba746402872573f42'
);
```

#### PDFs

The final example I wanted to touch is a `multi` data type for PDFs. We can see the 3rd and 5th accordion: Monthly Crime Statistics and Policty and Hate Crimes Reports. The `url` in the `datasets` table must be unique, so we cannot simply paste the url twice for both datatypes. In this case we need to use data type `27` again for `multi`, we can use `2` for a `direct` source type again, and gen a new id. The difference for this is I will leave a note of what the `multi` entails.

```text
INSERT INTO datasets 
(id, url, data_types_id, source_type_id, agency_id, notes)
VALUES
(
    'af6e5cb9929347719867b0559f6e56cb',
    'https://www.alamedaca.gov/Departments/Police-Department/Crime-Activity',
    27,
    2,
    '5c2d0726d183487ba746402872573f42',
    'PDFs for Crime Stats (23), Policy & Hate Crimes Reports'
);
```

We just need to do the 4th accordion, and then we can push our data in a PR or we can start back over and pick another agency!  
  
You can also verify the records you added in your sql instance where you're working:  
`select * from datasets where agency_id='5c2d0726d183487ba746402872573f42' and date_insert >= '2021-05-21'` it will grab all of the records for the current agency, and the `date_insert` will help in case the agency you are working with already had a previous record added but you found more!



