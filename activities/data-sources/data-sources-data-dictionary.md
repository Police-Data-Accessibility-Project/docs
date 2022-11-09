# Data Sources data dictionary

{% hint style="info" %}
To see which options are available for select fields, consult the [submission form](https://airtable.com/shrJafakrcmTxHU2i).
{% endhint %}

## What & Where

| Property           | Type                          | Description                                                                                                                                                                                                                                |
| ------------------ | ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| name               | formula                       | Uses `submitted_name` if present or concatenates `record_type` + `" for "` + `agency_described`                                                                                                                                            |
| record\_type       | select                        | What kind of data is accessible from this source?                                                                                                                                                                                          |
| description        | long text (string)            | Information to give clarity and confidence about what this source is, how it was processed, and whether the person reading the description might want to use it. Especially important if the source is difficult to preview or categorize. |
| source\_url        | url (string)                  | A link where these records can be found or are referenced.                                                                                                                                                                                 |
| agency\_described  | link to agencies table        | Which criminal justice agency is covered by this Data Source?                                                                                                                                                                              |
| state              | 2-character ISO code (string) | Looked up via `agency_described`                                                                                                                                                                                                           |
| county             | string                        | Looked up via `agency_described`                                                                                                                                                                                                           |
| municipality       | string                        | Looked up via `agency_described`                                                                                                                                                                                                           |
| agency\_type       | select                        | Looked up via `agency_described`                                                                                                                                                                                                           |
| jurisdiction\_type | select                        | Looked up via `agency_described`                                                                                                                                                                                                           |

## Provenance

| Property                | Type               | Description                                                                                                                                                                                                           |
| ----------------------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| agency\_supplied        | select (yes/no)    | Is the relevant agency also the entity supplying the data? This may be "no" if the agency or local government contracted with a third party to publish this data, or if a third party was the original record-keeper. |
| supplying\_entity       | long text (string) | If the agency didn't publish this, who did?                                                                                                                                                                           |
| agency\_originated      | select (yes/no)    | <p>Is the relevant agency also the original record-keeper? This is usually "yes", unless a third party collected data about a police agency.<br></p>                                                                  |
| originating\_entity     | long text (string) | If the agency was not the original record-keeper, who was?                                                                                                                                                            |
| community\_data\_source | boolean (checkbox) | Checked when a source of public records is supplied directly by a member of our community [via this form](contribute-data-sources.md#submit-data-youve-collected).                                                    |

## Access & Format

| Property                           | Type                | Description                                                                                      |
| ---------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------ |
| access\_type                       | multi-select        | How can the data be acquired?                                                                    |
| record\_format                     | multi-select        | What format(s) are the records in natively?                                                      |
| record\_download\_option\_provided | boolean (checkbox)  | There is a function available to download or export records.                                     |
| aggregation\_type                  | select              | Are there individual records, or does the data include aggregated totals?                        |
| size                               | short text (string) | The file size on disk of all the data at this source, if downloaded.                             |
| data\_portal\_type                 | select              | Some data is published via a standard third-party portal, typically named somewhere on the page. |
| access\_restrictions               | select              | Is anything special required to access the data?                                                 |
| access\_restrictions\_notes        | long text (string)  | Additional information about any access restrictions.                                            |

## Coverage & Retention

| Property                       | Type                | Description                                                                                                                               |
| ------------------------------ | ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| coverage\_start                | date                | The earliest date covered by this source.                                                                                                 |
| coverage\_end                  | date                | The date at which updates stop.                                                                                                           |
| source\_last_\__updated        | date                | The date this source was last updated.                                                                                                    |
| update\_frequency              | short text (string) | How often is this data source updated?                                                                                                    |
| update\_method                 | select              | How are new records added to this Data Source?                                                                                            |
| sort\_method                   | select              | When new records are added, how are they sorted?                                                                                          |
| retention\_schedule            | short text (string) | How long are records kept? Are there published guidelines regarding how long important information must remain accessible for future use? |
| number\_of\_records\_available | integer             | How many similar pieces of information are available at this source?                                                                      |

## Meta & Utility

| Property               | Type                            | Description                                                        |
| ---------------------- | ------------------------------- | ------------------------------------------------------------------ |
| scraper\_url           | url (string)                    | Link to any web scraping efforts associated with this Data Source. |
| data\_source\_created  | datetime                        | The date this source was first created in our database.            |
| agency\_described\_uid | Airtable-generated UID (string) | Looked up via `agency_described`                                   |
| airtable\_uid          | Airtable-generated UID (string) | Use this when exporting and importing updated data sources.        |

