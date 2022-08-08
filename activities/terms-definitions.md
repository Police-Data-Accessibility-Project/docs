# Our Process

## High-level explanation

We're finding and archiving sources of police data in a giant library. As our archive grows over time, we can empower larger and more exciting analysis projects with the data we've collected.

### Why tracking Data Sources matters

Shouldn't we just be writing a bunch of web scrapers and getting down to business? The short answer is that people are already doing this—across the country, people are using whatever means they can, from Python bootcamps to machine learning processes, to analyze what data is available.

* People need to be able to find data to do anything with it. This is currently a challenge. Does your organization have a giant, unwieldy spreadsheet with URLs pasted into it? You're not alone.
* Data is next to useless without context; we need to capture information about what data is available, how it was collected, and how it relates to other data. Only then will our community be able to effectively analyze it.
* Most people don’t realize how inconsistent police data access can be. We need to communicate that many answers cannot be found publicly, and serve as a hub for transparency activists working on the problem.

### Phases of Data Accessibility

1. Collect required data about each state in the U.S.
   * Federal and state-specific rules about police data publishing and access
2. Collect required data about `90% of the Agencies` in the state.
   * Location
     * Jurisdiction
     * Parent / child relationships between Agencies
   * Homepage
3. Collect required metadata about `90% of the Data Sources` in the state.
   * What kind of data?
   * Where is it?
   * How can it be accessed?
     * Methods required
     * Skills required
     * Rules about who can access it
   * What format is it in?
4. Publish tools to normalize and combine data from different Agencies and States, once local data is solid.

## Terms & Definitions

When describing PDAP activity, these are capitalized proper nouns.

| Term                   | Definition                                                                                                                                                                                                                                                                                       |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Agency                 | A police department or organization, like "Aurora Police Department".                                                                                                                                                                                                                            |
| Data Source            | A URL pointing to a place on a police website where public records may be scraped, like "police-agency.com/arrest-reports".                                                                                                                                                                      |
| Data Source Archive    | A raw, unprocessed HTML archive of a Data Source at a specific time.                                                                                                                                                                                                                             |
| Scraper / Data Scraper | <p>A bit of code responsible for collecting an Extraction from a Data Source or Archive. Check out <a href="https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/">the GitHub repo</a>.</p><p></p><p><em>Colloquially, "scraper" may refer to a person writing a Scraper.</em></p> |
| Extraction             | The result of running a Scraper is an Extraction, usually intended to further parse or process an HTML page into more usable data.                                                                                                                                                               |
| Extraction Metadata    | Packaged with each Extraction, Metadata is information about when the Extraction was made, from which Data Source, and using which Scraper.                                                                                                                                                      |

