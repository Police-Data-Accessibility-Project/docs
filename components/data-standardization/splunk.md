# Splunk

## Overview & Setup

Splunk is an intelligence analysis tool to make sense of vast amounts of data.

* **can run python script to save sanitized snapshots** on a recurring basis
* **can make API requests** to other APIs, and has an API to make requests against
* **can save alerts** for the appearance of specific data

### **Hosted**

[Access it here](http://144.202.93.42:8000/en-US/app/launcher/home). For this iteration, there’s a shared username and password. Reach out to Alec Akin for it. This is installed on a $10 Vultr instance with 2gb ram, 55gb ssd, and 1 core.

### **Local**

If you want to install a private instance for local use, it only takes about 10 minutes to set up on Mac or Windows. [Here’s where to get started](https://www.splunk.com/en_us/download/splunk-enterprise.html?utm_campaign=google_amer_en_search_brand&utm_source=google&utm_medium=cpc&utm_content=Splunk_Enterprise_Demo&utm_term=splunk&_bk=splunk&_bt=432128662491&_bm=p&_bn=g&_bg=76270518373&device=c&gclid=Cj0KCQiAh4j-BRCsARIsAGeV12AkmyhGC7IiT6h1pQWlxvUPd3TshA5EDTDFpZ1gAyFvtp67yfMPvc0aAhloEALw_wcB).

### Example use cases

When fed a batch of 3,000,000 documents from [NIBRS](https://pdap.atlassian.net/wiki/spaces/~165665269/pages/49611252/Data+sources), it quickly revealed that the 8 days responsible for the most hate crime in the United States were those immediately following September 11. The 9th was the final day of the [Rodney King riots](https://en.wikipedia.org/wiki/1992_Los_Angeles_riots#Day_4_%E2%80%93_Saturday,_May_2). It’s also a way to power parts of the site: a front end app could consume parts of the Splunk API.

### Basic usage

Here’s how to make queries in SPL, Splunk’s proprietary searching language. 

```text
index=nibrs source="hatecrimes.csv" incident_date="12-SEP-01"
```

