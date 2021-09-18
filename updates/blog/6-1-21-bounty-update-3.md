# 6/1/21: Bounty Update 3

* Still waiting for when we actually start merging PRs for the bounty, Katie \(Dolt\) has a script she will use for verifying data integrity of bounty PRs \(see edit at bottom\). If good, PRs will start being merged tomorrow!
* At the time of writing this post, we have 8 open PRs for the bounty that reflect:
  * over 50,000 row updates on the `agencies` table \(populating lat/lng, city, zip, fips & homepage\_url\)!
  * 111 new datasets!
  * 4 new data types!
* The Dolt team is aware of a bug that prevents `NULL` from being inserted in the csv import and are looking into it now \(see attached\)
* As mentioned in the above thread, I removed the UNIQUE constraint on URLs

Not bounty related:

* We have a few bounty participants that are very interested in actually loading the data and is hoping for another bounty for `data-intake`
* One participant, Alexis, has a [dolthub repo here](https://www.dolthub.com/repositories/alexis-evelyn/wanted-persons) with data she has scraped from the FBI for missing persons / wanted persons along with [source code here](https://github.com/alexis-evelyn/GeneralProjects/tree/master/wanted)! An excellent addition that we will look into!

– Eric

