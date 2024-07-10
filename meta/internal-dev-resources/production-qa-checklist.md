---
description: >-
  A checklist of basic manual tests to be performed immediately prior to and
  after the release of changes to production
---

# ☑️ Production QA Checklist

## Overview

This is a checklist of basic sanity checks to validate functionality of the web app immediately prior to and following a release of changes to production.&#x20;

This checklist is designed to be completed within 10 minutes or less -- it is not a substitute for more substantial automated testing as much as a way to manually validate critical functionality quickly.

## How To Use

1. Run through this checklist in the dev environment as a final precondition to releasing changes to production.&#x20;
2. Run through the checklist _again_ on the production domain immediately afterwards to confirm nothing has broken.&#x20;

## Checklist

* [ ] Using Chrome, open [developer tools](https://developer.chrome.com/docs/devtools/overview) and navigate to the "Console" tab to enable visibility of client-side errors.
* [ ] Navigate to the domain and confirm the home page loads as expected without error
* [ ] Perform a search in the database using a common keyword such as "Prison" or "Pittsburgh". See that results are returned without error.
  * [ ] For a given result, click on "More Details" and see that results are loaded.
* [ ] Click on the following links and confirm they load the expected page without error:
  * [ ] "Search"
  * [ ] "Data"
  * [ ] "Community"
  * [ ] "About"
  * [ ] "Donate"
  * [ ] "Docs"
* [ ] Recommended: perform other unexpected behavior specific to the code being tested, to try to "break" the site. For example, entering invalid search terms or trying to navigate to URLs without proper auth. Confirm the web page handles it gracefully, documenting cases where it does not.
  * [ ] Perform the above in both the desktop version and a mobile device
