# Writing about PDAP

## Goals

### Be a source of truth.

Our reputation for accuracy and integrity must be unimpeachable. If you can't say something with certainty—say less!

### Have maintainable, future-proof messaging.

When something changes, it can be a pain—or impossible—to update links all over the place. If you're **filling out a profile,** link to language on [https://pdap.io](http://pdap.io/) rather than repeating it. If you'd like to tell people **where to contribute,** link to [https://pdap.io/contribute.html](https://pdap.io/contribute.html) rather than sharing PayPal or GitHub links.

## Terms & Definitions

When describing PDAP activity, these are capitalized proper nouns.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Term</th>
      <th style="text-align:left">Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><a href="../../../components/datasets/">Dataset</a>
      </td>
      <td style="text-align:left">A URL pointing to a place on a police website where public records may
        be scraped. Each Dataset needs a Scraper.</td>
    </tr>
    <tr>
      <td style="text-align:left">Scraper / Data Scraper</td>
      <td style="text-align:left">
        <p>A bit of Python code responsible for collecting public records from an
          agency website within our <a href="../../legal/legal-data-scraping.md">legal requirements</a>.
          Some of the code is &quot;common,&quot; shared between Scrapers. The starting
          point for information about Scrapers is <a href="https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/">the GitHub repo</a>.</p>
        <p></p>
        <p><em>Colloquially, &quot;scraper&quot; may refer to a person writing a Scraper.</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Extraction</td>
      <td style="text-align:left">The result of running a Scraper is an Extraction, which represents all
        the records found at a given Dataset at the time the Scraper was run.</td>
    </tr>
    <tr>
      <td style="text-align:left">Data Integrity</td>
      <td style="text-align:left">By observing the requirements for <a href="../../../components/data-intake.md">Data Intake</a>,
        we can be sure that every record has an auditable history and passes the
        &quot;bright-line&quot; test for tracing data back to its origin. This
        is how we prove we aren&apos;t inventing data&#x2014;we&apos;re surfacing
        what&apos;s already public, and we can prove it.</td>
    </tr>
  </tbody>
</table>

