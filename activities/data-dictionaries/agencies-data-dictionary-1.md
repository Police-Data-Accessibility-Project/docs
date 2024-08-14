# Requests data dictionary

{% hint style="info" %}
To see which options are available for select fields, consult the [submission form](https://airtable.com/shrzxLdSsYmBvIWMH).
{% endhint %}

### Required properties for submission

`submitter_contact_info`, `request_notes`, `location_described`

## Form submission

| Property            | Type              | Description                                                                                                                                                                                      |
| ------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| coverage\_range     | string            | A range of dates or years covered by this request                                                                                                                                                |
| data\_requirements  | string            | Details the data must have, like "case numbers" or "incident location".                                                                                                                          |
| location\_described | string            | Is your research focused on a specific department? Are you comparing two counties or cities?                                                                                                     |
| submission\_notes   | string (textarea) | What are you trying to learn? Are you trying to answer a specific question, or complete a specific project? Is there anything you've already tried?                                              |
| submitter\_email    | string            | How should we contact you to respond to this request? We won't share this with volunteers without your permission. We will never display it publicly or with volunteers without your permission. |
| target\_date        | string            | When would you like to see this request filled? Are you working on a deadline?                                                                                                                   |

## Management & display

| Property                    | Type                     | Description                                                                                              |
| --------------------------- | ------------------------ | -------------------------------------------------------------------------------------------------------- |
| archive\_reason             | string                   | Why was this archived?                                                                                   |
| data\_sources               | link to `data sources`   | Airtable link to relevant sources by airtable ID                                                         |
| date\_created               | datetime                 | When this was created                                                                                    |
| date\_status\_last\_changed | datetime                 | When the value of `request_status` last changed                                                          |
| github\_issue\_url          | string                   | Link to the GitHub issue associated with this request. Added manually in Airtable, by integration in v2. |
| id                          | autonumber               | Used for display in Airtable.                                                                            |
| internal\_notes             | string                   | Internal notes by PDAP staff about the request.                                                          |
| pdap\_response              | string                   | Public notes by PDAP about the request.                                                                  |
| record\_types\_required     | array                    | Multi-select from our [taxonomy](record-types-taxonomy.md).                                              |
| related\_requests           | link to other `requests` | Manually linked. Will be deprecated in favor of GitHub.                                                  |
| request\_status             | array                    | Will be migrated to GitHub Project status and Issue status.                                              |
| withdrawal\_reason          | array                    | Describe why issues were withdrawn, for metrics tracking.                                                |
| work\_required              | array                    | Types of work that might be needed to respond to the request, such as "data location" or "web scraping"  |

