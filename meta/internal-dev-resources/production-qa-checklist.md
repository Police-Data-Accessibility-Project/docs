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

## Basic Checklist

* [ ] Using Chrome, open [developer tools](https://developer.chrome.com/docs/devtools/overview) and navigate to the "Console" tab to enable visibility of client-side errors.
* [ ] Navigate to the domain and confirm the home page loads as expected without error
* [ ] Perform a search in the database using a common keyword such as "Prison" or "Pittsburgh". See that results are returned without error.
  * [ ] For a given result, click on "More Details" and see that results are loaded.
* [ ] Click on the following links and confirm they load the expected page without error:
  * [ ] "Data"
  * [ ] "About"
  * [ ] "Donate"
  * [ ] "Docs"
* [ ] Recommended: perform other unexpected behavior specific to the code being tested, to try to "break" the site. For example, entering invalid search terms or trying to navigate to URLs without proper auth. Confirm the web page handles it gracefully, documenting cases where it does not.
  * [ ] Perform the above in both the desktop version and a mobile device

## Expanded Checklist

<details>

<summary>Expand for Checklist</summary>

* [ ] Check `sign-in` page
  * [ ] Can a user successfully sign in using GitHub?
  * [ ] Can a user successfully sign in using a password?
* [ ] Check Map
  * [ ] Does the map load?
  * [ ] Are states colored more or less heavily depending on how many data sources they have?
  * [ ] Can you click on a state and have it zoom in?
    * [ ] Can you click "View All" and be taken to the appropriate search page?
    * [ ] Can you click on one of the counties viewable in the dropdown and be taken to the appropriate search page?
  * [ ] From a county level, can you zoom out and have the view revert to the state level?
  * [ ] Can you zoom out further and have the view revert to the national level?
  * [ ] Can you click the `loop` icon and have the view revert to the national level?
  * [ ] Are counties similarly colored based on how many data sources they have?
  * [ ] Can you click on a county and zoom in further to see the "pins" of different locations?
    * [ ] Can you click "View All" and be taken to the appropriate search page?
    * [ ] Can you click "Suggest missing data" and be taken to a New Request (possibly after sign-in)?
    * [ ] Can you click `Follow for updates` and get it confirmed?
    * [ ] Can you unfollow something you're following, from the map view?
    * [ ] Can you click on a locality viewable in the dropdown and be taken to the appropriate search page?
  * [ ] Search Page
    * [ ] Does the page load all data types, populating `local`, `county`, `state`, and `federal`?
      * [ ] &#x20;When clicking on any of those categories, do the searches automatically navigate to searches of those that geographic level?
    * [ ] When clicking a data source, are you taken to the appropriate `Data Source` page?
    * [ ] `Search Location` Box
      * [ ] When checking any `Types of Data` subtype and clicking `Update search`, does the page filter results to _only those_ `Types of Data` _selected_?
        * [ ] When checking one of multiple `Types of Data` checks and clicking `Update search`, does the search now update to only the `Types of Data` subtypes remaining?
      * [ ] Does the search typeahead work? Can you load new results, click on one, and be taken to a new version of the page?
  * [ ] `data-source` page
    * [ ] &#x20;When clicking `next`, are you taken to the next relevant data source?
      * [ ] "Relevant" implies that all data sources should connect first to other data sources with the same record type, then the same locality, then the same county, then the same state
    * [ ] When clicking `next` and then `prev`, are you taken to the same data source page you started at?
    * [ ] Does clicking `View Data Source` take you to the appropriate link?
    * [ ] Are all relevant data source information pages properly populated in the following boxes:
      * [ ] `Access & format`
      * [ ] `Provenance`
      * [ ] `Coverage & retention`
      * [ ] `Data Source Meta`
    * [ ] Are the following attributes properly populated?
      * [ ] `Agency`
      * [ ] `County, State`&#x20;
      * [ ] `Agency Type`
  * [ ] Home Page
    * [ ] Clicking on the profile icon should take a user to their profile
    * [ ] Additional Links
      * [ ] `About the data`
        * [ ] `"Data Source"`
        * [ ] `start with the docs!`
      * [ ] All `Recently Added Data Sources`
        * [ ] Have a functioning link
        * [ ] The question mark takes them to the relevant `Data Source` page
      * [ ] `Programs`
        * [ ] `Open a Data Request`&#x20;
        * [ ] `Sign up for an account`
      * [ ] `Take Action`
        * [ ] `docs.pdap.io`
      * [ ] `Locate sources`
        * [ ] `Help add Data Sources to our Database`
        * [ ] `Submit a source you found`
      * [ ] `Collaborate on Data Projects`
        * [ ] `Volunteer for Data Requests`
      * [ ] Good first issues
        * [ ] Each individual link takes the user to an open issue
        * [ ] `View more Good First Issues` takes the user to the appropriate view
      * [ ] `Praise for our work`
        * [ ] `Alliance for Police Accountability`
        * [ ] `Alliance, NE`
        * [ ] `Dr. Kyla Bourne`
      * [ ] `Examples`
        * [ ] `shared it in our database`&#x20;
        * [ ] `this article in Public Source`
        * [ ] web scraper `?` mark
        * [ ] `We made it open-source`
      * [ ] `Software Roadmap`
        * [ ] `sign up for data labeling here!`
      * [ ] Footer Navbar
        * [ ] `GitHub`
        * [ ] `Discord`
        * [ ] `Newsletter`
        * [ ] `Docs`
        * [ ] `Publish data`
        * [ ] `Email`
        * [ ] `Guidestar Badge`
  * [ ] Profile Page
    * [ ] A user should be able to click `Unfollow` and unfollow a given search. On refresh, that search should not appear.
    * [ ] A set of `Recent Searches` should be viewable by the user, correlating to searches the user performed.
    * [ ] The user should click `Regenerate API Key` and receive a new API key popup
    * [ ] The user should either have a `Link account with GitHub` button or an indicator that the user's account is linked with GitHub
    * [ ] Clicking the `ResetPassword` button should take the user to the `change-password` page
    * [ ] Clicking the `Sign-out` button should take the user to the `Sign-In` page
*

</details>
