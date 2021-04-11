# Legal Restrictions for Data Volunteers

### Data scraping for an ethical source of truth

#### Questions to ask before you begin:

> * Is the material I intend to scrape protected by copyright?
> * Does the website I intend to scrape require authentication?
> * Will the scraping compromise individual privacy?
> * Will scraping reduce the value of the original data?
> * Am I in violation of the terms of use/service of the website I intend to scrape?
> * Will my scraping activity overload, damage, or otherwise adversely affect a server?

**The answers to all of these questions should be “no”.** If you cannot answer the question, or are unsure, you should not proceed. Further discussion on each of these questions can be found below.

**Is the material I intend to scrape protected by copyright?**

Copyright, a form of intellectual property law, protects original works of authorship including literary, dramatic, musical, and artistic works, such as poetry, novels, movies, songs, computer software, and architecture. Copyright does not protect facts, ideas, systems, or methods of operation, although it may protect the way these things are expressed, for example, the creative arrangement of otherwise non-copyrightable facts. The [U.S. Copyright Office](https://www.copyright.gov/help/faq/faq-protect.html) provides additional information on the scope of copyright protection. When scraping data, you should limit scraping to only non-copyrightable facts, and should only collect parts of pages required for the purpose.

**Does the website I intend to scrape require authentication?**

Scraping should be strictly limited to information that is presumptively accessible to the general public, and which does not require authentication to access such as a username and password. If a website requires authentication to access data, that data should not be scraped. For further reading on this issue, the U.S. Court of Appeals for the Ninth Circuit’s 2019 decision in [hiQ Labs, Inc. v. LinkedIn Corp.](https://law.justia.com/cases/federal/appellate-courts/ca9/17-16783/17-16783-2019-09-09.html) provides a helpful analysis.

**Will the scraping compromise individual privacy?**

While information available in public records is public by its nature, be aware if the information being scraped reveals personal data that is generally understood to be private, such as social security numbers and bank or credit card information. This may also include personal data that can identify an individual person, such as name, email, phone number, and address. If in doubt, omit such personal data from the scope of the scrape.

**Will scraping reduce the value of the original data?**

Again, scraping should be strictly limited to information that is presumptively accessible to the general public. This limitation is important to ensure that original data being scraped is not diminished in value as a result of it being scraped.

**Am I in violation of the terms of use/service of the website I intend to scrape?**

When you login \(e.g., through a username and password\) and/or expressly agree to the terms of use/serve of a website, you are entering into a contract with the website owner, thereby agreeing to their rules. These rules may explicitly state that data may not be scraped from the website, and failing to adhere to such terms may put you in breach of that contract. As noted, however, your scraping should be strictly limited to information that is presumptively accessible to the general public, and which does not require authentication.

**Will my scraping activity overload, damage, or otherwise adversely affect a server?**

Do not harm the website you are scraping. This includes, for example, using a reasonable crawl rate and assuring that the volume and frequency of queries you make so not burden the website’s servers or interfere with the website’s normal operations. Respect the delay that crawlers should wait between requests by following the crawl-delay directive outlined in the robots.txt file. Where possible, strive to limit scraping to a time of day when the website is unlikely to be experiencing heavy traffic, for example, early in the morning or night. All PDAP scrapers and crawlers must also abide by State and Federal computer crimes statutes, including those collected [here](../legal.md).

