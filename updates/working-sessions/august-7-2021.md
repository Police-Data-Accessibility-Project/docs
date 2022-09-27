# August 7, 2021

### [Support for unprocessed data](https://github.com/Police-Data-Accessibility-Project/PDAP-Scrapers/issues/80)

Richard got hadoop up and running

Dolt [datasets](https://www.dolthub.com/repositories/pdap/datasets) could be stored there

We should not run scrapers on the hadoop box because there's no authentication right now, they should be run on digitalocean if anywhere.&#x20;

![](<../../.gitbook/assets/Screen Shot 2021-08-07 at 7.33.19 PM.png>)

VPN access info is available for gsuite folks

Dev is in New York, Production is in San Francisco. They can't talk to each other at the moment without a VPN. Keeping our infrastructure in one place may be worth looking at in the future :shrug:

_We could use Lambda, maybe not worth considering a change at the moment._

### Stabs x Pythonidaer working session

Generated a `scraper.py` file, success!

We need to explain the path to Hadoop when it exists

Scrapers can contribute to documentation as they learn

### Random

Zenhub is nice

Feedback welcome on the front page (pdap.io)

Main site is down, moving to simpler HTML/CSS for the two pages: Home and FAQ

Could be CMS driven / as accessible as possible

[Josh to try Webflow → HTML quick prototype](https://github.com/Police-Data-Accessibility-Project/PDAP.io/issues/37)

### Miner pool

[Distributed mining pool](https://www.investopedia.com/terms/m/mining-pool.asp) is a good metaphor to think about—our scrapers could run like that. People could use their compute power. Like reverse torrenting. Or something.

Data itself could be stored as NFT

### Volunteer / Community Management

We don't have anyone to do this. We should better get to know our volunteers, and keep in touch with people in a meaningful way.

Right now the only place is Discord, how can we be more inclusive there / tie GitHub / DoltHub contributions to Discord in some way. Be clear about who's contributing!

**How can we make it clear that there's always a seat at the table for new people?**

Stabs to make "how many people made PRs in github and dolthub this month" show up in Discord somehow via web scraping?!

On the front page rewrite, Josh + team to write copy letting people know they're welcome

* [x] Stabs and Josh to change each other's discord server settings

Lots of updates made to the readmes.&#x20;

