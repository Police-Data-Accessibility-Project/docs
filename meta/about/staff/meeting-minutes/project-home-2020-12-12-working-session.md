# 2020-12-12 Working Session

## Attendees <a href="#id-2020-12-12workingsession-attendees" id="id-2020-12-12workingsession-attendees"></a>

* [Josh Lintag](https://pdap.atlassian.net/wiki/people/5f20c61fc9c094001c5d32ca?ref=confluence)
* [Former user (Deleted)](https://pdap.atlassian.net/wiki/people/5f8f95be40588b0077ed830a?ref=confluence)
* [Alec Akin (Unlicensed)](https://pdap.atlassian.net/wiki/people/5f1e64ee2aa25000286fc7fc?ref=confluence)
* [Richard Ji](https://pdap.atlassian.net/wiki/people/5f8f95be0e068b00766b6903?ref=confluence)
* [Zach Goulson](https://pdap.atlassian.net/wiki/people/5f1f8319ef11df0025869e21?ref=confluence)

## Goals <a href="#id-2020-12-12workingsession-goals" id="id-2020-12-12workingsession-goals"></a>

* Come up with shopping list
* Work on individual action items

## Notes <a href="#id-2020-12-12workingsession-notes" id="id-2020-12-12workingsession-notes"></a>

* Shopping List
  * [Google Workspace accounts](https://workspace.google.com/pricing.html)
  * Possibly splunk, but more likely a VPS service instead (i.e. Digital Ocean)
    * Dev/Playground server
    * Scraping server
    * Website server
    * SFTP server
    * Donation software

## Shopping List <a href="#id-2020-12-12workingsession-shoppinglist" id="id-2020-12-12workingsession-shoppinglist"></a>

| **Service**                                | **Use**                      | **Cost**      | **Cost Type**                          | **Approx. Current Predicted Cost**                                                                                                                                                             | **Approx. Post Non-Profit Predicted Cost** | **Initial Year Cost** | **Notes**                                                                                                                                                        |
| ------------------------------------------ | ---------------------------- | ------------- | -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ | --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Google Workspace Business Starter/Standard | File Management              | $6/$12        | User/month                             | $36/$72                                                                                                                                                                                        | $36/$72                                    | $720 for 10 users     |                                                                                                                                                                  |
| Duo MFA                                    | Privileged Access Management | $3            | User/month                             | $30                                                                                                                                                                                            | $30                                        | $360 for 10 users     | Nice to have, not critical yet                                                                                                                                   |
| Bitwarden Teams                            | Password Management          | $3            | User/month                             | Free/$30                                                                                                                                                                                       | $30                                        |                       | Nice to have, not critical yet                                                                                                                                   |
| Jira Standard                              | Project Management           | $7            | User/month                             | $63                                                                                                                                                                                            | $15.75                                     | $840                  |                                                                                                                                                                  |
| Confluence                                 | Project Wiki                 | $5            | User/month                             | $50                                                                                                                                                                                            | $12.5                                      | $600                  | Nice to have, not critical yet                                                                                                                                   |
| Slack                                      | Remote Comms                 | $8/$6.67      | User/month or User/month billed yearly | $17,142                                                                                                                                                                                        | $2,572                                     |                       |                                                                                                                                                                  |
| DigitalOcean                               | VPS/Hosting                  | $5            | 1 server/month                         | <ul><li>Webserver - $60/year</li><li>Scraping/util server - $240/year</li><li>TFTP server - $60/year</li><li>Splunk - $960/year *assuming self hosting</li><li>DB server - $180/year</li></ul> |                                            | $1500                 | <p>Server for each at least:</p><ul><li>Webserver - frontpage site</li><li>Scraping server</li><li>TFTP server</li><li>Splunk server</li><li>DB server</li></ul> |
| Domain Name                                | Public facing host name      | Variable; $12 | Per year                               | $12                                                                                                                                                                                            | $12                                        |                       |                                                                                                                                                                  |

## Accounting Software <a href="#id-2020-12-12workingsession-accountingsoftware" id="id-2020-12-12workingsession-accountingsoftware"></a>

| **Name**                            | **Cost /user**                             | **Cloud/Self Host** | **Pros**                      | **Cons**                                                       |
| ----------------------------------- | ------------------------------------------ | ------------------- | ----------------------------- | -------------------------------------------------------------- |
| [Akaunting](https://akaunting.com/) | **Free**, may need to purchase add-on apps | Cloud               | <ul><li>Open source</li></ul> | <ul><li>Unsure about viability for donation tracking</li></ul> |
|                                     |                                            |                     |                               |                                                                |

## HR Software <a href="#id-2020-12-12workingsession-hrsoftware" id="id-2020-12-12workingsession-hrsoftware"></a>

| **Name**                  | **Cost/user** | **Cloud/Self Host** | **Pros** | **Cons** |
| ------------------------- | ------------- | ------------------- | -------- | -------- |
| Hubspot with Integrations |               |                     |          |          |

## CRM Software <a href="#id-2020-12-12workingsession-crmsoftware" id="id-2020-12-12workingsession-crmsoftware"></a>

* [Open source options](https://crm.org/crmland/open-source-crm)

| **Name**                                                                                                                     | **Cost/User** | **Cloud/Self Host** | **Pros**                                | **Cons**                                      |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------- | ------------------- | --------------------------------------- | --------------------------------------------- |
| Hubspot                                                                                                                      |               |                     |                                         |                                               |
| [SuiteCRM](https://suitecrm.com)                                                                                             |               |                     | <ul><li>Open source</li></ul>           |                                               |
| [Insightly](https://pdap.atlassian.net/wiki/pages/resumedraft.action?draftId=218202113)                                      | $29           |                     |                                         |                                               |
| [Spreadsheet solution](https://docs.google.com/spreadsheets/d/12S3hIhJUC8O-dqwNnEHvFCMfWtnkZSzmCf04rhg92q8/edit?usp=sharing) | Free          | Cloud               | <ul><li>Available immediately</li></ul> | <ul><li>Probably not the easiest UX</li></ul> |

## Data Compliance <a href="#id-2020-12-12workingsession-datacompliance" id="id-2020-12-12workingsession-datacompliance"></a>

| **Name** | **Cost/User** | **Cloud/Self Host** | **Pros** | **Cons** |
| -------- | ------------- | ------------------- | -------- | -------- |
|          |               |                     |          |          |
|          |               |                     |          |          |
