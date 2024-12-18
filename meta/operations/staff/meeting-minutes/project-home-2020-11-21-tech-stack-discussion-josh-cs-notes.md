# 2020 11-21 Tech Stack discussion

Broad strokes: we determined that the MVP fulfills the pieces not currently achieved by Splunk—which could serve as the entire front end at very small scale. This means **data integrity** and **depth** are the core of the value added by PDAP.

## Parts <a href="#id-202011-21techstackdiscussion-joshcsnotes-parts" id="id-202011-21techstackdiscussion-joshcsnotes-parts"></a>

**Ingestion** → **Archival Storage** → **Search & analysis**

## Core principles, aka value add <a href="#id-202011-21techstackdiscussion-joshcsnotes-coreprinciples-akavalueadd" id="id-202011-21techstackdiscussion-joshcsnotes-coreprinciples-akavalueadd"></a>

Data stewardship

Transparency

Discipline

“Librarian”

## Insights <a href="#id-202011-21techstackdiscussion-joshcsnotes-insights" id="id-202011-21techstackdiscussion-joshcsnotes-insights"></a>

"I want police data."

Make a query → **get information**

Enter search via UI (selects) or code → present specific data

api (json), chart, csv

"I want to be able to analyze the police data I found."

Analysis tools or analysis that is done for you

_Find extremes in the data automatically_

"PDAP needs to verify data."

* Guard the submissions process
* Credibility score for each type of data

"PDAP needs to be like a librarian."

* Nonintrusive
* **Pedigree**
  * Legally captured?
  * Multiple sources?
  * Anonymity?

"What does it mean to verify data?"

"We need to be able to get data out of cold storage."

* Eventually it'll be too much data for Splunk

## Workflows powered by Splunk <a href="#id-202011-21techstackdiscussion-joshcsnotes-workflowspoweredbysplunk" id="id-202011-21techstackdiscussion-joshcsnotes-workflowspoweredbysplunk"></a>

**Query data → Analyze data → Export insights**

_**Upload data**_ **→ Analyze data\***\
\*_The user agrees that we can keep the data, and provides information or verification about it._

**Save an Analysis → Share the Analysis with someone else**

**Save an Analysis → Revisit it with updated data**\
&#xNAN;_&#x41;lert user if an analysis changes based on updated information_

### Specific abilities granted by Splunk <a href="#id-202011-21techstackdiscussion-joshcsnotes-specificabilitiesgrantedbysplunk" id="id-202011-21techstackdiscussion-joshcsnotes-specificabilitiesgrantedbysplunk"></a>

* easily write regex
* accept any type of data
  * oddly / non-delimited
  * many file types
* faster analysis / searching on the server rather than locally
* automatically find "interesting fields"
* search
* analysis

## Workflows not supported yet <a href="#id-202011-21techstackdiscussion-joshcsnotes-workflowsnotsupportedyet" id="id-202011-21techstackdiscussion-joshcsnotes-workflowsnotsupportedyet"></a>

**Supply data to PDAP by volunteering or other sources**

**Verify submitted data → Request more info from a submitter**

**Provide an unprecedented breadth of data**

**Safely archive historic data for the foreseeable future**

**Understand the categorization structure**\
&#xNAN;_&#x57;e need to make sure the structure is future-proof, and establish policies for sortation that cannot easily be corrupted._
