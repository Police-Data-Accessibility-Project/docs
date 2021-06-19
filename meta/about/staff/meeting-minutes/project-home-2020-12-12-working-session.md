# 2020-12-12 Working Session

## Attendees <a id="id-2020-12-12WorkingSession-Attendees"></a>

* [Josh Lintag](https://pdap.atlassian.net/wiki/people/5f20c61fc9c094001c5d32ca?ref=confluence)
* [Former user \(Deleted\)](https://pdap.atlassian.net/wiki/people/5f8f95be40588b0077ed830a?ref=confluence)
* [Alec Akin \(Unlicensed\)](https://pdap.atlassian.net/wiki/people/5f1e64ee2aa25000286fc7fc?ref=confluence)
* [Richard Ji](https://pdap.atlassian.net/wiki/people/5f8f95be0e068b00766b6903?ref=confluence)
* [Zach Goulson](https://pdap.atlassian.net/wiki/people/5f1f8319ef11df0025869e21?ref=confluence)

## Goals <a id="id-2020-12-12WorkingSession-Goals"></a>

* Come up with shopping list
* Work on individual action items

## Notes <a id="id-2020-12-12WorkingSession-Notes"></a>

* Shopping List
  * [Google Workspace accounts](https://workspace.google.com/pricing.html)
  * Possibly splunk, but more likely a VPS service instead \(i.e. Digital Ocean\)
    * Dev/Playground server
    * Scraping server
    * Website server
    * SFTP server
    * Donation software

## Shopping List <a id="id-2020-12-12WorkingSession-ShoppingList"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Service</b>
      </th>
      <th style="text-align:left"><b>Use</b>
      </th>
      <th style="text-align:left"><b>Cost</b>
      </th>
      <th style="text-align:left"><b>Cost Type</b>
      </th>
      <th style="text-align:left"><b>Approx. Current Predicted Cost</b>
      </th>
      <th style="text-align:left"><b>Approx. Post Non-Profit Predicted Cost</b>
      </th>
      <th style="text-align:left"><b>Initial Year Cost</b>
      </th>
      <th style="text-align:left"><b>Notes</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Google Workspace Business Starter/Standard</td>
      <td style="text-align:left">File Management</td>
      <td style="text-align:left">$6/$12</td>
      <td style="text-align:left">User/month</td>
      <td style="text-align:left">$36/$72</td>
      <td style="text-align:left">$36/$72</td>
      <td style="text-align:left">$720 for 10 users</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Duo MFA</td>
      <td style="text-align:left">Privileged Access Management</td>
      <td style="text-align:left">$3</td>
      <td style="text-align:left">User/month</td>
      <td style="text-align:left">$30</td>
      <td style="text-align:left">$30</td>
      <td style="text-align:left">$360 for 10 users</td>
      <td style="text-align:left">Nice to have, not critical yet</td>
    </tr>
    <tr>
      <td style="text-align:left">Bitwarden Teams</td>
      <td style="text-align:left">Password Management</td>
      <td style="text-align:left">$3</td>
      <td style="text-align:left">User/month</td>
      <td style="text-align:left">Free/$30</td>
      <td style="text-align:left">$30</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Nice to have, not critical yet</td>
    </tr>
    <tr>
      <td style="text-align:left">Jira Standard</td>
      <td style="text-align:left">Project Management</td>
      <td style="text-align:left">$7</td>
      <td style="text-align:left">User/month</td>
      <td style="text-align:left">$63</td>
      <td style="text-align:left">$15.75</td>
      <td style="text-align:left">$840</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Confluence</td>
      <td style="text-align:left">Project Wiki</td>
      <td style="text-align:left">$5</td>
      <td style="text-align:left">User/month</td>
      <td style="text-align:left">$50</td>
      <td style="text-align:left">$12.5</td>
      <td style="text-align:left">$600</td>
      <td style="text-align:left">Nice to have, not critical yet</td>
    </tr>
    <tr>
      <td style="text-align:left">Slack</td>
      <td style="text-align:left">Remote Comms</td>
      <td style="text-align:left">$8/$6.67</td>
      <td style="text-align:left">User/month or User/month billed yearly</td>
      <td style="text-align:left">$17,142</td>
      <td style="text-align:left">$2,572</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">DigitalOcean</td>
      <td style="text-align:left">VPS/Hosting</td>
      <td style="text-align:left">$5</td>
      <td style="text-align:left">1 server/month</td>
      <td style="text-align:left">
        <ul>
          <li>Webserver - $60/year</li>
          <li>Scraping/util server - $240/year</li>
          <li>TFTP server - $60/year</li>
          <li>Splunk - $960/year *assuming self hosting</li>
          <li>DB server - $180/year</li>
        </ul>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left">$1500</td>
      <td style="text-align:left">
        <p>Server for each at least:</p>
        <ul>
          <li>Webserver - frontpage site</li>
          <li>Scraping server</li>
          <li>TFTP server</li>
          <li>Splunk server</li>
          <li>DB server</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Domain Name</td>
      <td style="text-align:left">Public facing host name</td>
      <td style="text-align:left">Variable; $12</td>
      <td style="text-align:left">Per year</td>
      <td style="text-align:left">$12</td>
      <td style="text-align:left">$12</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

## Accounting Software <a id="id-2020-12-12WorkingSession-AccountingSoftware"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Name</b>
      </th>
      <th style="text-align:left"><b>Cost /user</b>
      </th>
      <th style="text-align:left"><b>Cloud/Self Host</b>
      </th>
      <th style="text-align:left"><b>Pros</b>
      </th>
      <th style="text-align:left"><b>Cons</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><a href="https://akaunting.com/">Akaunting</a>
      </td>
      <td style="text-align:left"><b>Free</b>, may need to purchase add-on apps</td>
      <td style="text-align:left">Cloud</td>
      <td style="text-align:left">
        <ul>
          <li>Open source</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Unsure about viability for donation tracking</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

## HR Software <a id="id-2020-12-12WorkingSession-HRSoftware"></a>

| **Name** | **Cost/user** | **Cloud/Self Host** | **Pros** | **Cons** |
| :--- | :--- | :--- | :--- | :--- |
| Hubspot with Integrations |  |  |  |  |

## CRM Software <a id="id-2020-12-12WorkingSession-CRMSoftware"></a>

* [Open source options](https://crm.org/crmland/open-source-crm)

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Name</b>
      </th>
      <th style="text-align:left"><b>Cost/User</b>
      </th>
      <th style="text-align:left"><b>Cloud/Self Host</b>
      </th>
      <th style="text-align:left"><b>Pros</b>
      </th>
      <th style="text-align:left"><b>Cons</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Hubspot</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://suitecrm.com">SuiteCRM</a>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <ul>
          <li>Open source</li>
        </ul>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://pdap.atlassian.net/wiki/pages/resumedraft.action?draftId=218202113">Insightly</a>
      </td>
      <td style="text-align:left">$29</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://docs.google.com/spreadsheets/d/12S3hIhJUC8O-dqwNnEHvFCMfWtnkZSzmCf04rhg92q8/edit?usp=sharing">Spreadsheet solution</a>
      </td>
      <td style="text-align:left">Free</td>
      <td style="text-align:left">Cloud</td>
      <td style="text-align:left">
        <ul>
          <li>Available immediately</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Probably not the easiest UX</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Data Compliance <a id="id-2020-12-12WorkingSession-DataCompliance"></a>

| **Name** | **Cost/User** | **Cloud/Self Host** | **Pros** | **Cons** |
| :--- | :--- | :--- | :--- | :--- |
|  |  |  |  |  |
|  |  |  |  |  |

