# 2021-03-27 database working session

## Date <a id="id-2021-03-27databaseworkingsession-Date"></a>

27 Mar 2021

## Participants <a id="id-2021-03-27databaseworkingsession-Participants"></a>

* [Eddie Brown \(Unlicensed\)](https://pdap.atlassian.net/wiki/people/5fd63e354d2179006ecbcb80?ref=confluence)
* [Alec Akin](https://pdap.atlassian.net/wiki/people/60319bf02a42cc0069af9ac8?ref=confluence)
* Mitch Miller
* [Josh Lintag](https://pdap.atlassian.net/wiki/people/5f20c61fc9c094001c5d32ca?ref=confluence)
* Kristin Tynski
* Jeff Jockisch
* [Richard Ji](https://pdap.atlassian.net/wiki/people/5f8f95be0e068b00766b6903?ref=confluence)
* [Former user \(Deleted\)](https://pdap.atlassian.net/wiki/people/5f8f95be40588b0077ed830a?ref=confluence)

## Goals <a id="id-2021-03-27databaseworkingsession-Goals"></a>

## Discussion topics <a id="id-2021-03-27databaseworkingsession-Discussiontopics"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Item</th>
      <th style="text-align:left">Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>dolt</p>
        <ul>
          <li>Review the DoltHub proof of concept for <a href="https://www.dolthub.com/repositories/pdap/datasets">dataset catalogue</a>
            <ul>
              <li>does not yet include sources from @stabs or form submissions</li>
              <li>still need to remove the form and point people to dolthub, if this proof
                of concept looks good</li>
            </ul>
          </li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>why is dolt better than a daily backup?</li>
          <li>lowers barrier to entry &#x2192; can work without much automation or maintenance.</li>
          <li>documents chain of custody.</li>
          <li>overhead&#x2014;how much time do people spend managing commits and PRs
            vs. <b>actually scraping</b>?</li>
          <li><b>ease of use for contributors</b> is a primary objective if we&#x2019;re
            going to scale</li>
          <li>scale&#x2014;we&#x2019;re building a unique database of databases in addition
            to scraped data</li>
          <li>free</li>
          <li>dolt can be used to identify &amp; track sources &#x2192; the translated
            data could be sent to</li>
          <li>bounties only work for data, not scrapers/infrastructure.</li>
          <li>bounties allow people to contribute with minimal social engagement.</li>
          <li>Using Dolt as a POC for storing data in a version controlled fashion</li>
          <li>How do we scale this?</li>
          <li>Resolving version control may slow things down</li>
          <li>Automatic scrapers pushing into a branch to merge to master becomes a
            bottleneck; not applicable atm</li>
          <li>Edit history is tracked</li>
          <li>Why dolt instead of daily backups? Or our own history tables?</li>
          <li>Dolt can be used as a little more than an audit log for data sources</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Do we need a global table for <code>unique_data_properties</code> &#x2192;
            we make SQL <code>INDEX</code>es of that based on <code>data_types</code>?
            Or are we better off creating <b>tables</b> for each <code>data_type</code>?
            How do we decide?</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>We should identify which data points are most consistently available across
            data sources &#x2192; this gives us targets to hit.</li>
          <li>metadata fields always need to be added in data discovery
            <ul>
              <li>parent child relationship between types and properties</li>
              <li>the query will be ugly but this is how it&#x2019;s best designed for large
                code</li>
            </ul>
          </li>
          <li>mongodb may work as a metadata repository
            <ul>
              <li>we&#x2019;d need something to talk to both</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Define the next steps for keeping structure parity between Datasets, Data,
            and Scrapers
            <ul>
              <li>How should these structures relate to one another?</li>
            </ul>
          </li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li><b>Scrapers need a config file for where they&#x2019;re sending data</b>
          </li>
          <li><b>Dolt repos may need a path back to the scraper</b>
          </li>
          <li>dolthub &#x2260; where people provide scraper code</li>
          <li>Tiered approach for data properties: 1. NIBRS 2. Store CSV&#x2026;anything
            in between?</li>
          <li>We can decide which tiers we&#x2019;re actively ingesting based on how
            often they&#x2019;re available.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Enterprise features / structure down the road</td>
      <td style="text-align:left">
        <ul>
          <li>Risk: github or dolthub fails</li>
          <li>We&#x2019;ll want a backup DB, then an API.</li>
          <li>Sooner rather than later we need to back up our data for better disaster
            recovery.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Documentation: read the docs vs confluence</td>
      <td style="text-align:left">
        <ul>
          <li>Richard is writing documentation for backend design &amp; workflows</li>
          <li>it&#x2019;s in markdown</li>
          <li>Confluence is a stopgap for collaborating and getting on the same page</li>
          <li>What does implementation look like?</li>
          <li><a href="https://readthedocs.org/">https://readthedocs.org/</a>
            <ul>
              <li>Does it work for open source?</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">People bringing drop-in scrapers</td>
      <td style="text-align:left">
        <ul>
          <li>Scrapers (the humans) often bring their own scraper library with them
            &#x2192; we should enable them to slot in to the extent it&#x2019;s possible</li>
          <li>Messaging scrapers: <b>what are we targeting</b>?
            <ul>
              <li>We need to make sure we&#x2019;re clear about the breadth / scope of data.</li>
            </ul>
          </li>
          <li>Fragmenting the target makes it hard for us to progress. We want to focus
            on NIBRS format data to validate it against what&#x2019;s available from
            the FBI &amp; broaden context</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">data to not collect</td>
      <td style="text-align:left">
        <p>At one point this was our list, is it accurate?</p>
        <ul>
          <li>CaseNum</li>
          <li>FirstName</li>
          <li>MiddleName</li>
          <li>LastName</li>
          <li>DOB</li>
          <li>DefenseAttorney</li>
          <li>PublicDefender</li>
          <li>Judge</li>
          <li>ArrestingOfficer</li>
          <li>ArrestingOfficerBadgeNumber</li>
        </ul>
        <p><b>Consider:</b> not collecting data we don&#x2019;t know is legal to have.</p>
        <ul>
          <li>the government made the data public. If it&#x2019;s public, it&#x2019;s
            not considered personal.</li>
          <li>We need to be careful <b>which source</b> the data is coming from. If it&#x2019;s
            not a direct source, we may be subject to different restrictions. Will
            third party aggregators have</li>
          <li>With the bounty program we can mandate that they include certain proofs
            in their submission</li>
        </ul>
        <p><em>Whenever we decide on a property to collect, we need to justify it / provide rationale for the decision</em>
        </p>
        <ul>
          <li><a href="https://www.lawfareblog.com/understanding-supreme-courts-carpenter-decision">https://www.lawfareblog.com/understanding-supreme-courts-carpenter-decision</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Are we collecting data aggregated by third parties?</td>
      <td style="text-align:left">
        <ul>
          <li>Each aggregator has their own format</li>
          <li>Do we want to throw it away?</li>
          <li>Discrepancies in the data aren&#x2019;t necessarily &#x201C;red flags&#x201D;;
            agency&#x2019;s maybe aggregating according to different criteria so there
            maybe discrepancies according to that unknown criteria</li>
          <li>We do want aggregate level data for validating the record level data that
            is being returned to us</li>
          <li>For now these are stored as <code>source_type = &#x201C;third_party&#x201D;</code>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Data types to prioritize</td>
      <td style="text-align:left">
        <ul>
          <li>arrest reports</li>
          <li>traffic stops</li>
          <li>incident reports</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Scraper approval</td>
      <td style="text-align:left">
        <ul>
          <li>Multi-tier approval is possible with github</li>
          <li>How does wikipedia do it?</li>
          <li>Base scraper approval is most urgent</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ETL framework</td>
      <td style="text-align:left">
        <ul>
          <li>Should extraction / ETL be a required part of a scraper?</li>
          <li>Mitch Miller is using python to create a framework which should be flexible
            enough to meet our needs</li>
          <li>ETL should not go directly into the scraper, but it does need to be closely
            related.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Action items <a id="id-2021-03-27databaseworkingsession-Actionitems"></a>

* [Former user \(Deleted\)](https://pdap.atlassian.net/wiki/people/5f8f95be40588b0077ed830a?ref=confluence) find out how much overhead \(time\) is involved in an end to end dolt scrape → public
* [Former user \(Deleted\)](https://pdap.atlassian.net/wiki/people/5f8f95be40588b0077ed830a?ref=confluence) add data format \(NIBRS\) column to dataset catalogue
* [Former user \(Deleted\)](https://pdap.atlassian.net/wiki/people/5f8f95be40588b0077ed830a?ref=confluence) Identify minimum data properties to meet NIBRS data format, has this somewhere already[https://pdap.atlassian.net/browse/PDAP-118](https://pdap.atlassian.net/browse/PDAP-118)
* [Former user \(Deleted\)](https://pdap.atlassian.net/wiki/people/5f8f95be40588b0077ed830a?ref=confluence) Document data\_types priority [in scrapers readme](https://github.com/Police-Data-Accessibility-Project/Scrapers/pull/43). Arrest Reports, Traffic Stops, Incident reports. What’s most available. What most easily paints the full picture. Tiers. [https://pdap.atlassian.net/browse/PDAP-119](https://pdap.atlassian.net/browse/PDAP-119)
* [Former user \(Deleted\)](https://pdap.atlassian.net/wiki/people/5f8f95be40588b0077ed830a?ref=confluence) validate workflow: **localized, raw data is stored in dolt → it could be aggregated / ETL’d to a centralized server.** dolt is the audit/transparency.
* [Former user \(Deleted\)](https://pdap.atlassian.net/wiki/people/5f8f95be40588b0077ed830a?ref=confluence) Expose basic roadmap in documentation with backup DB → API
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) Draft a policy and rationale for “fields not to collect” → **A&P**
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) Draft a policy and rationale for mirroring dataset websites → **A&P**
* [Former user \(Deleted\)](https://pdap.atlassian.net/wiki/people/5f8f95be40588b0077ed830a?ref=confluence) import dataset catalogue [form submissions](https://docs.google.com/spreadsheets/d/176f0pTxlIyvBWqXmJCPPlh2zRrcMZNgojB2fJOBBhGw/edit#gid=901781374) and deprecate form
* [Richard Ji](https://pdap.atlassian.net/wiki/people/5f8f95be0e068b00766b6903?ref=confluence) Get @stabs [base scraper](https://github.com/Police-Data-Accessibility-Project/Scrapers/pull/38/files) approved

**Mitch Miller** is making an ETL framework

[https://pdap.atlassian.net/browse/PDAP-113](https://pdap.atlassian.net/browse/PDAP-113)

[https://pdap.atlassian.net/browse/PDAP-114](https://pdap.atlassian.net/browse/PDAP-114)

## Decisions <a id="id-2021-03-27databaseworkingsession-Decisions"></a>

* @stabs need to be recognized. Let’s be sure to celebrate their hard work

