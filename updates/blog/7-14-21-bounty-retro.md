---
description: by Josh Chamberlain
---

# 7/14/21: Bounty Retro

## Background

Our first [Data Bounty](https://www.dolthub.com/repositories/pdap/datasets/bounties/3c259649-762e-438b-a538-b14be4d0507a) with DoltHub was intended to give data scrapers a cash reward for their submissions to public data. They funded and supported the endeavor—thank you Tim, Katie, and the rest of the DoltHub team for giving our project this huge leap forward!

## Gains

Our goal was to complete our Agencies table, which is a critical piece of infrastructure. It allows us to draw a line directly from a department's website to the processed, accessible police data that was collected from it.

* We accepted 22 PRs, for a total of 162494 cell edits. There are [~18,000 agencies by name](https://www.dolthub.com/repositories/pdap/datasets/query/master?q=select+count%28distinct+name%29+as+%22Number+of+agencies%22+from+agencies%3B%0A&active=Tables), and [~23,000 by id](https://www.dolthub.com/repositories/pdap/datasets/query/master?q=select+count%28distinct+id%29+%0Aas+%22Number+of+agencies%22+%0Afrom+agencies%3B%0A&active=Tables). That's a huge leap forward in our data holdings. Thank you to the folks who contributed!
* We learned that it's possible to rapidly scrape agency homepage data for the entire country.

## Areas to Improve

There was a burst of activity that died off as incentives dried up. How can we structure this differently in the future?

* Datasets entries are more difficult to machine scrape than Agencies; because the reward is divided based on cells edited, once the Agencies table was largely complete, there was very little financial incentive for anyone to add Datasets. **In the future, we should limit the bounty—geographically, or to just the datasets table.**
* A group of volunteers calling themselves the Bounty Hunters were trying to make a submission and blocked by our schema. Not OK! We're going to investigate why and make the necessary changes in time for the next bounty.

Next up? [Become a Patron](https://blog.pdap.io/article/patreon.com/pdap) to fund future bounties. [Contribute to our Datasets](https://www.dolthub.com/repositories/pdap/datasets). [Contribute code](https://docs.pdap.io/).

