# 2021-04-10 Meeting notes

## Date <a id="id-2021-04-10Meetingnotes-Date"></a>

10 Apr 2021

## Participants <a id="id-2021-04-10Meetingnotes-Participants"></a>

* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence)
* Eddie Brown
* Alec Akin
* Eric Turner
* Stabs

## Goals <a id="id-2021-04-10Meetingnotes-Goals"></a>

* Answer schema questions to unblock [dolt implementation](https://pdap.atlassian.net/browse/PDAP-60).
* Decide whether tableplus or DBeaver would be useful in the dolt pipeline \([discussion here](https://policeaccessibility.slack.com/archives/C014Q3ZT2GG/p1617822153049800)\).

## Discussion topics <a id="id-2021-04-10Meetingnotes-Discussiontopics"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Item</th>
      <th style="text-align:left">Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Datasets</td>
      <td style="text-align:left">
        <ul>
          <li>UUIDs have been added in dolt</li>
          <li>may want to remove hyphens to save space (currently mysql built in)</li>
          <li>Once things are more stable it&#x2019;s probably worth doing some views</li>
          <li>Eric wrote a script to keep CityProtect datasets up to date as well as
            commit the dataset to the dolt db
            <ul>
              <li>Fork then merge is a necessity</li>
              <li>We could put these on a chron job or just manually one them&#x2014;once
                for each portal type</li>
              <li>These update quarterly, so automating that is not our biggest problem.</li>
              <li>355 agencies in cityprotect for bulk downloading, avg 10 CSV files</li>
            </ul>
          </li>
          <li>We&#x2019;ll need to get <code>data</code> out of <code>datasets</code>
          </li>
          <li>Clones and forks become problematic just to make simple additions</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Dolt x Scale</td>
      <td style="text-align:left">
        <p>Alternative for down the road: <a href="https://www.esri.com/en-us/arcgis/products/arcgis-open-data">https://www.esri.com/en-us/arcgis/products/arcgis-open-data</a>
        </p>
        <p>Risk: dolt is young and missing advanced SQL features. Dolt is not our
          advanced analytics tool. Dolt is not our deep storage layer.</p>
        <p>Databases can&#x2019;t currently reference each other, and repos are 1:1
          with databases.</p>
        <p>Data is unlimited but current technical cap is ~200gb</p>
        <p>Can Dolt be an intake tool and not grow?</p>
        <p>This may not even be our presentation layer because of the low amount
          of data it can store</p>
        <ul>
          <li>one way around this might be checking data out of one dolt repo into another,
            preserving paper trail. does dolt support this / is it reasonable?</li>
          <li>Otherwise priority &#x2191; for <a href="https://pdap.atlassian.net/browse/PDAP-80">https://pdap.atlassian.net/browse/PDAP-80</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Where are we storing our data properties?</td>
      <td style="text-align:left">
        <p>Is breadth an issue in Dolt? Would this table be prohibitively gigantic?</p>
        <p>SQL column limit ~1000, mysql 4000. we should be good.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Hosting</td>
      <td style="text-align:left">If we went with mongodb directly we could bolt it into our DigitalOcean</td>
    </tr>
    <tr>
      <td style="text-align:left">Tableplus / DBeaver</td>
      <td style="text-align:left">
        <p><a href="https://policeaccessibility.slack.com/archives/C014Q3ZT2GG/p1617822153049800">context</a>
        </p>
        <p>Tableplus free has some limitations (open tabs)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Scrapers</td>
      <td style="text-align:left">For now&#x2014;people should write whatever they want / is most convenient
        for them. If we want to refactor, we can figure out what the priority is
        on it + do it later.</td>
    </tr>
    <tr>
      <td style="text-align:left">Server access</td>
      <td style="text-align:left">We don&#x2019;t use passwords, just keys&#x2014;send it to Alec if you
        need access.</td>
    </tr>
    <tr>
      <td style="text-align:left">OCR</td>
      <td style="text-align:left">Stabs tried ~5 different ones and none of them worked well enough. Alec&#x2019;s
        tried tensorflow</td>
    </tr>
  </tbody>
</table>

## Action items <a id="id-2021-04-10Meetingnotes-Actionitems"></a>

* proof of concept for separate dolt DB \(check whether DBs can easily reference one another\) [![](https://pdap.atlassian.net/secure/viewavatar?size=medium&avatarId=10318&avatarType=issuetype)PDAP-144](https://pdap.atlassian.net/browse/PDAP-144) Done
* proof of concept for `global_properties` table referenced by data\_types views [PDAP-121](https://pdap.atlassian.net/browse/PDAP-121?src=confmacro) - JIRA project doesn't exist or you don't have permission to view it.
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) to make request in dolthub discord for one:many repos:dbs
* [Alec Akin](https://pdap.atlassian.net/wiki/people/60319bf02a42cc0069af9ac8?ref=confluence) reach out to 3 major cloud providers + mongodb for sponsorships
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) Point database volunteers in the direction of [Dolt SQL viewer integrations](https://github.com/dolthub/docs/tree/gitbook-dev/content/integrations)
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) add scraper philosophies to readme \(do what you want, we can always refactor later\)

## Decisions <a id="id-2021-04-10Meetingnotes-Decisions"></a>

* Dolt is not our advanced analytics tool. Dolt is not our deep storage layer.

