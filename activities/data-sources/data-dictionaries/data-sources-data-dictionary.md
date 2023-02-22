# Data Sources data dictionary

{% hint style="info" %}
To see which options are available for select fields, consult the [submission form](https://airtable.com/shrJafakrcmTxHU2i).
{% endhint %}

### Required properties for submission

`submitted_name`, `submitter_contact_info`, `record_type`, `agency_supplied` (+ other "[provenance](data-sources-data-dictionary.md#provenance)" properties, if "no")

## What is it?

| Property        | Type              | Description                                                                                                                                                                                                                                |
| --------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| name            | string            | Uses `submitted_name` if present or concatenates `record_type` + `" for "` + `agency_described`; can get weird when one or both are not present                                                                                            |
| submitted\_name | string            | Required for individual Data Source submissions for clarity.                                                                                                                                                                               |
| record\_type    | string            | What kind of data is accessible from this source? For more info, see the [Record Types taxonomy](record-types-taxonomy.md).                                                                                                                |
| tags            | array             | Are there any keyword descriptors which might help people find this in a search? Try to limit tags to information which can't be contained in other properties.                                                                            |
| description     | string (textarea) | Information to give clarity and confidence about what this source is, how it was processed, and whether the person reading the description might want to use it. Especially important if the source is difficult to preview or categorize. |

## Agency

| Property            | Type                                                       | Description                                                                                                                                             |
| ------------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| agency\_described   | array (foreignkey based on an agency's ID within Airtable) | To which criminal legal system agency or agencies does this Data Source refer?                                                                          |
| agency\_aggregation | array                                                      | If present, the Data Source describes multiple agencies. Can be an item like `local` or `county`.                                                       |
| state               | string                                                     | 2-character ISO code, related to the associated Agency object, if present.                                                                              |
| county              | string                                                     | Related to the associated Agency object, if present.                                                                                                    |
| municipality        | string                                                     | Related to the associated Agency object, if present.                                                                                                    |
| agency\_type        | string                                                     | Related to the associated Agency object, if present.                                                                                                    |
| jurisdiction\_type  | array                                                      | Related to the associated Agency object, if present. What is the highest level of jurisdiction for the agency? Can be an item like `local` or `county`. |

## Provenance

_Where did it come from?_

| Property                | Type    | Description                                                                                                                                                                                                           |
| ----------------------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| agency\_supplied        | boolean | Is the relevant Agency also the entity supplying the data? This may be "no" if the Agency or local government contracted with a third party to publish this data, or if a third party was the original record-keeper. |
| supplying\_entity       | string  | If the Agency didn't publish this, who did?                                                                                                                                                                           |
| agency\_originated      | boolean | <p>Is the relevant Agency also the original record-keeper? This is usually "yes", unless a third party collected data about a police Agency.<br></p>                                                                  |
| originating\_entity     | string  | If the Agency was not the original record-keeper, who was?                                                                                                                                                            |
| community\_data\_source | boolean | True when a source of public records is supplied directly by a member of our community [via this form](../../share-data/contribute-data-sources.md#submit-data-youve-collected).                                      |

## Access & format

| Property                           | Type              | Description                                                                                                                                 |
| ---------------------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| source\_url                        | string            | A URL where these records can be found or are referenced.                                                                                   |
| readme\_url                        | string            | A URL where supplementary information about the source is published.                                                                        |
| access\_type                       | array             | Array items can have values such as `Web page` or `API`                                                                                     |
| record\_format                     | array             | What format(s) are the records in natively? Array items can have values such as `CSV`, `JSON`, `XML`, `RDF`, `RSS`, `HTML table` and others |
| detail\_level                      | array             | Is this an individual record, an aggregated set of records, or a summary without underlying data?                                           |
| record\_download\_option\_provided | boolean           | There is a function available to download or export records.                                                                                |
| size                               | string            | The file size on disk of all the data at this source, if downloaded.                                                                        |
| data\_portal\_type                 | string            | Some data is published via a standard third-party portal, typically named somewhere on the page.                                            |
| access\_restrictions               | string            | Is anything special required to access the data?                                                                                            |
| access\_restrictions\_notes        | string (textarea) | Additional information about any access restrictions.                                                                                       |
| records\_not\_online               | boolean           | Someone has checked for these records on the internet, and has not located them.                                                            |

## Coverage & retention

| Property                       | Type    | Description                                                                                                                               |
| ------------------------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| coverage\_start                | date    | The earliest date covered by this source, if known, in the format YYYY-DD-MM.                                                             |
| coverage\_end                  | date    | The date at which updates stop, in the format YYYY-DD-MM.                                                                                 |
| source\_last\_\_\_updated      | date    | The date this source was last updated, in the format YYYY-DD-MM.                                                                          |
| update\_frequency              | string  | How often is this data source updated?                                                                                                    |
| update\_method                 | string  | How are new records added to this Data Source?                                                                                            |
| sort\_method                   | string  | When new records are added, how are they sorted?                                                                                          |
| retention\_schedule            | string  | How long are records kept? Are there published guidelines regarding how long important information must remain accessible for future use? |
| number\_of\_records\_available | integer | How many similar pieces of information are available at this source?                                                                      |

## Meta & utility

| Property                       | Type     | Description                                                           |
| ------------------------------ | -------- | --------------------------------------------------------------------- |
| scraper\_url                   | string   | The url of any web scraping efforts associated with this Data Source. |
| data\_source\_created          | datetime | The date this source was first created in our database.               |
| agency\_described\_linked\_uid | string   | The Airtable-generated UID of an associated Agency                    |
| airtable\_uid                  | string   | The Airtable-generated UID of this particular data source             |
