# PII \(WIP / Discussion\)

## Problem

We want people to feel sound ethically and legally when they contribute to PDAP. To that end, we need to do these things: 

1. Draw a “bright line” between the source material and the published data; i.e. “we are not changing the data, we are a mirror”. **\[a\]** 
2. Avoid aggregating already-public PII in a way that would make it more public than it already is **\[b\]**.
3. Strive for our stated mission **\[c\]** of being a complete source of truth. i.e. “we could not be accused of editorializing by omission”. Our current policy is that we're allowed to collect PII **\[d\]** . 

Our existing policy about _accepting_ PII is legally the right one but we do need to discuss how we _aggregate_ and _omit_. Discuss in the thread for the next 3 days, then we'll do a survey or something. 

### How sure are we that omitting PII is against the rules?

We have a policy that allows PII, **do we need to require it? Do we need to allow censorship?**

**Is PDAP the one doing the scraping, or the scraper community?**

We can always get a second opinion. Maybe we need to define what PII is?

**How can we prevent PDAP from being mugshots.com?**

**Can we choose which data we aggregate?** Sounds reasonable to Eddie.

Richard says there could be a security/`know-your-user` layer—make it more difficult than a search bar. Require people to register, know your user.

PDAP could be considered a wikipedia-like source of good sources.

## Actions

We could make PII unavailable via the API.

We could keep PII out of any queryable database.

We could only show it when referencing unedited source material.

We could restrict data usage to non-commercial.

We could still aggregate data on whether a field is included.

~~We could restrict data access to verified users.~~ Not considered possible.

## References

\[a\] [https://docs.pdap.io/meta/legal/legal-data-scraping](https://docs.pdap.io/meta/legal/legal-data-scraping)

> \[...private data\] may also include personal data that can identify an individual person, such as name, email, phone number, and address. If in doubt, omit such personal data from the scope of the scrape.

\[b\] [https://papers.ssrn.com/sol3/papers.cfm?abstract\_id=2678420](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2678420)   
\[c\] [https://pdap.io/](https://pdap.io/)   
\[d\] [https://docs.pdap.io/meta/legal/personally-identifiable-information](https://docs.pdap.io/meta/legal/personally-identifiable-information)  
\[e\] [https://www.whitepages.com/terms-of-service](https://www.whitepages.com/terms-of-service)

## Ideas

* No commercial use
* Don't make PII searchable
  * Don't put it in DoltHub
  * Don't extract it from the source at all, leave it in the PDF

