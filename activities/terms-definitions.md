# Our Process

## High-level explanation

We're finding and archiving sources of police data in a giant library. As our archive grows over time, we can empower larger and more exciting analysis projects with the data we've collected.

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

