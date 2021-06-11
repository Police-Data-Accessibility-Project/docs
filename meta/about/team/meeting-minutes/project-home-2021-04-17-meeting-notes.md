# 2021-04-17 Meeting notes

## 44RDCXDSDDDate <a id="id-2021-04-17Meetingnotes-44RDCXDSDDDate"></a>

17 Apr 2021

## Participants <a id="id-2021-04-17Meetingnotes-Participants"></a>

Mitch Miller

[Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence)

[Eric Turner](https://pdap.atlassian.net/wiki/people/6069da262b469c007014d7fa?ref=confluence)

Jeff Joskisch

[Richard Ji](https://pdap.atlassian.net/wiki/people/5f8f95be0e068b00766b6903?ref=confluence)

## Discussion topics <a id="id-2021-04-17Meetingnotes-Discussiontopics"></a>

<table>
  <thead>
    <tr>
      <th style="text-align:left">Item</th>
      <th style="text-align:left">Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Dolt / Databases</td>
      <td style="text-align:left">
        <ul>
          <li>Lots of changes being made in datasets
            <ul>
              <li>agencies</li>
            </ul>
          </li>
          <li>Does Dolt support SQL COPY</li>
          <li>Richard has MongoDB creds for anyone who would like to experiment</li>
          <li>How slow is Dolt? Breakingly? We&#x2019;re going to have ~2 million records.</li>
          <li>We can host a mirror on our server and run an instance if people want
            the same data quicker / without the dolt UI</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Podcast fame
        <br />
      </td>
      <td style="text-align:left">Jeff was interviewed on <a href="https://www.spirion.com/privacy-please-podcast/">Privacy Please</a> releasing
        this week (wednesday) and mentioned PDAP
        <br />
      </td>
    </tr>
    <tr>
      <td style="text-align:left">OCR</td>
      <td style="text-align:left">
        <p>Tensorflow has been suggested</p>
        <p>We may need a lot of training data, which we don&#x2019;t have.</p>
        <ul>
          <li>Is there a way we could slowly start to feed this stuff to tensorflow
            now?</li>
        </ul>
        <p>Requirements:</p>
        <ul>
          <li>We need to be able to comma delimit things on the way in</li>
        </ul>
        <p>There&#x2019;s no harm in the meantime with publishing unedited PDFs</p>
        <ul>
          <li>may inspire contributors to help with OCR</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">FE</td>
      <td style="text-align:left">
        <p>There are some folks ready to work on stuff for when we have data</p>
        <p>For now it&#x2019;s pretty small and people could clone it and run it
          locally</p>
        <p>Miles is converting gatsby to JSX which will make iteration easier</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">mongodb</td>
      <td style="text-align:left">We should have a template if we&#x2019;re using Mongo</td>
    </tr>
    <tr>
      <td style="text-align:left">Docker compose file</td>
      <td style="text-align:left">Mitch is working on a docker compose file for dolt and mongo, which will
        be helpful as we get our ETL framework together</td>
    </tr>
  </tbody>
</table>

## Action items <a id="id-2021-04-17Meetingnotes-Actionitems"></a>

* [Eric Turner](https://pdap.atlassian.net/wiki/people/6069da262b469c007014d7fa?ref=confluence) to ping Mitch in slack when sql-server POC is done \(nearly\)
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) policy / rationale for PII → docs \(this is a high priority\)
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) make shitty base tables from examples of other data types
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) Do meeting notes in Docs next time so they can be shared

