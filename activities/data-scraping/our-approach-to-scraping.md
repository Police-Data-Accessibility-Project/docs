# Our approach to scraping

## Philosophy

Scraping can turn cumbersome records into useful data. When someone wants to use records but they're in a difficult format, scraping is often the answer.

### Where the community fits in

Our target users are the thousands of people already using police data. We can support their work by connecting the community of PDAP volunteer scrapers with real, impactful projects. If you don't have your own ideas about what to scrape, find local groups working on the criminal legal system. They probably have data woes!

## Which data are we scraping?

TL;DR: Public records about the criminal legal system.

Coding is real work—typically, it's only worth writing a scraper if you have a use case for the data already. What are you trying to learn? PDAP exists to help people find police data. If it's about a police agency, there's a good chance someone in that jurisdiction has a use for it. To find projects in need of scraping help, you can head to the [#data-exchange Discord channel](https://discord.com/channels/828274060034965575/1006564024894378106).

We are also interested in meta information about the police system itself. Which agencies have jurisdiction about any particular street corner? Who should you contact for public records access? How do agencies nest within each other?

If you just want to write web scrapers, but don't have a use case in mind—that's OK! We're here to support you. Check out our [database of Data Sources](../data-sources/explore-data-sources.md), especially those in HTML table or PDF format, for candidates of records which may be tricky to access. If your strategy for scraping is successful, we'll share it as a case study to help people working on similar projects.

## Immediate goals

After hundreds of hours of user research, we have determined that these are how we will add value in the police data landscape.

* **Track independently scraped data** in our [Data Sources database](../data-sources/). Prevent duplication of effort by showing people what's already out there. To submit data you've scraped, [start here](../share-data/contribute-data-sources.md).
* **Connect people** with web scraping skills to community members trying to make better use of police data without technical expertise. This happens in the [#data-exchange Discord channel](https://discord.com/channels/828274060034965575/1006564024894378106).
* **Build open-source tools** in the [Scrapers repo](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers) to make running a scraper on-demand easier for people who don't know what "CLI" means.
* **Scrape data sources** and agency metadata to populate the [Data Sources database](../data-sources/).

## Not immediate priorities

#### Aggregation and hosting of scraped data

* In our experience, if you can find someone interested in using the data, storage typically takes care of itself.
* It's not an immediate priority to make a big database to store scraped data in the same format. The main reason this isn't a priority: _this is not what our users are asking us for._ It's almost everyone's first thought when they hear about our project (us too). Our research tells us access, organization, and communication are the bottleneck for people using the data.
* Aggregation is incredibly complex, and involves more than just mapping properties. So much context is needed before data from two departments can be compared.
* Publishing and vouching for extracted data, and documenting its provenance so it can be audited, is a big project. We only want to undertake this work for data we _know will be useful._

#### Automated scraper farms

* It's not an immediate priority to automate the running of all the scrapers in our shared repo. The main reason: _this is not what our users are asking us for._ We plan to archive the sources, and facilitate sharing of scraper code. If we have a stable archive, scraping can be done on-demand.

#### Scrape all the data!

* Scraping is hard work, and there are hundreds of thousands of potential data sources out there. For many applications, data doesn't even need to be processed to be useful—it just needs to be findable. We don't need to scrape things unless it's clearly adding value.

## Current status

We're still in the iteration and case study phase. If you want to learn something about the police, you can write a scraper to parse, normalize, or get deeper information from our Data Sources.

If you don't have scraping skills, you can use the [#data-exchange channel in Discord](https://discord.com/channels/828274060034965575/1006564024894378106) to find someone who may be able to help.

1. Run a Scraper you wrote, or one from the [Scrapers Repo](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers), to get an extraction.
2. Share your extraction and what you learned in Discord.
3. We'll all learn about the criminal legal system from the experience, and brainstorm ways our tools could better facilitate your work.
4. Repeat!
