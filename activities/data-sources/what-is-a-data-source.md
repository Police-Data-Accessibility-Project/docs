# What is a Data Source?

## What is a Data Source?

A web page, file, database, or filing cabinet somewhere which contains records about a criminal justice agency (law enforcement, courts, corrections). Often, this is published by the agency itself.

#### Example

Data Sources are records describing an agency's activities, like `arrest records` or `hiring policies`.

Agencies are criminal justice organizations, like the `Pittsburgh Bureau of Police` or `Allegheny County Jail`.

{% hint style="info" %}
To contribute Data Sources, [start here](contribute-data-sources.md)!
{% endhint %}

## Why is this important?

People need to be able to find data to do anything with it. The foundation of our work is creating a common system for classifying and tracking public data. Does your organization have a giant, unwieldy spreadsheet tracking FOIA requests and web sites? [You're not alone](contribute-data-sources.md#spreadsheet-of-data-sources).

### Things we can build using a Data Sources database

* **Automatic archives** of each URL, creating a lasting resource for future research and web scraping. As it stands, information is lost to time due to data retention policies.
* **A classification system** using metadata about which records are available, how it was collected, and how it relates to other records. This is the path to doing big, complicated aggregation projects.
* **Better transparency.** We can improve transparency by being a hub for people who are using what's already there, finding its limits, and addressing them one by one.
* **Shared tools.** When someone finds a Data Source in our database, they will also be able to see associated scrapers, extractions, and archives.

### What kinds of Data Sources are best?

{% hint style="info" %}
Finding all the Data Sources for your hometown is a human-sized project that can make a real impact.
{% endhint %}

If it's about a criminal justice agency, we want to track it. This includes FOIA'd documents, web URLs, and independently scraped records.

#### We're working region by region, not type by type.

Because most data is consumed by local users—and because context is everything—we're focusing on helping people access as much information about their local municipality, county, or state as possible.

## Public Records Accessibility

### What are public records?

Some information is required by law to be public. Governments keep several types of public records, and make them available to different degrees—sometimes on a web page, sometimes behind a "records request" process like the Freedom of Information or Right to Know requests. Our goal is to track these Data Sources in one place, and work to make each of them as accessible as possible.

#### Degrees of access for public records

1. The source should exist, but we have no known path to access
2. Someone has previously made an extraction or records request for this source
3. We have custody of an archive or can point to direct access

## Data custody

It's important to know who collected and published the data.&#x20;

`agency_described` (which agency is the data about?)

↓

`originating_entity` (who generated the records?)

↓

`supplying`\_`entity` (who is publishing the records?)

Sometimes these are all the same entity; sometimes they are all different. No matter what, we want to track the Data Source.
