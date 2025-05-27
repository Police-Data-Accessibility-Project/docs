# 2021-04-17 Meeting notes

## 44RDCXDSDDDate <a href="#id-2021-04-17meetingnotes-44rdcxdsdddate" id="id-2021-04-17meetingnotes-44rdcxdsdddate"></a>

17 Apr 2021

## Participants <a href="#id-2021-04-17meetingnotes-participants" id="id-2021-04-17meetingnotes-participants"></a>

Mitch Miller

[Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence)

[Eric Turner](https://pdap.atlassian.net/wiki/people/6069da262b469c007014d7fa?ref=confluence)

Jeff Joskisch

[Richard Ji](https://pdap.atlassian.net/wiki/people/5f8f95be0e068b00766b6903?ref=confluence)

## Discussion topics <a href="#id-2021-04-17meetingnotes-discussiontopics" id="id-2021-04-17meetingnotes-discussiontopics"></a>

| Item                    | Notes                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dolt / Databases        | <ul><li><p>Lots of changes being made in datasets</p><ul><li>agencies</li></ul></li><li>Does Dolt support SQL COPY</li><li>Richard has MongoDB creds for anyone who would like to experiment</li><li>How slow is Dolt? Breakingly? We’re going to have ~2 million records.</li><li>We can host a mirror on our server and run an instance if people want the same data quicker / without the dolt UI</li></ul>               |
| <p>Podcast fame<br></p> | <p>Jeff was interviewed on <a href="https://www.spirion.com/privacy-please-podcast/">Privacy Please</a> releasing this week (wednesday) and mentioned PDAP<br></p>                                                                                                                                                                                                                                                           |
| OCR                     | <p>Tensorflow has been suggested</p><p>We may need a lot of training data, which we don’t have.</p><ul><li>Is there a way we could slowly start to feed this stuff to tensorflow now?</li></ul><p>Requirements:</p><ul><li>We need to be able to comma delimit things on the way in</li></ul><p>There’s no harm in the meantime with publishing unedited PDFs</p><ul><li>may inspire contributors to help with OCR</li></ul> |
| FE                      | <p>There are some folks ready to work on stuff for when we have data</p><p>For now it’s pretty small and people could clone it and run it locally</p><p>Miles is converting gatsby to JSX which will make iteration easier</p>                                                                                                                                                                                               |
| mongodb                 | We should have a template if we’re using Mongo                                                                                                                                                                                                                                                                                                                                                                               |
| Docker compose file     | Mitch is working on a docker compose file for dolt and mongo, which will be helpful as we get our ETL framework together                                                                                                                                                                                                                                                                                                     |

## Action items <a href="#id-2021-04-17meetingnotes-actionitems" id="id-2021-04-17meetingnotes-actionitems"></a>

* [Eric Turner](https://pdap.atlassian.net/wiki/people/6069da262b469c007014d7fa?ref=confluence) to ping Mitch in slack when sql-server POC is done (nearly)
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) policy / rationale for PII → docs (this is a high priority)
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) make shitty base tables from examples of other data types
* [Josh Chamberlain](https://pdap.atlassian.net/wiki/people/6068f9e790e3950069fbaaf4?ref=confluence) Do meeting notes in Docs next time so they can be shared
