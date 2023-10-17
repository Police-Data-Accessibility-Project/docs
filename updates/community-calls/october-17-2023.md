# October 17, 2023

Context: We're professionalizing our front end: design system, component library, tailwindUI.

Agenda:

* what's the vision for how our front end should be structured relative to our API and users? (capturing tasks / ideas)
* what's been done so far?
* what's up next?
* are there open questions?

### Goals

* dev environment: branch in github auto-deploying&#x20;
  * has its own environment variables
  * def FE → dev API
* set a standard for secrets / environments
  * as needed access&#x20;
* don't expose tokens in the front end / repos
  * JWT validated by the API against a secret key in DO
  * refresh tokens prevent access
  * token ⭤ user ID pair
    * what about public front end views (no auth)?
  * API can use permissions to prevent access/action (roles)
  * the FE client can use its own `client` token
  * logged in user credentials would override `client` token
  * local, dev, prod all use same methodology
* consider an isolated back end service for users/OAuth
  * better security, separation of concerns
  * [https://oauth.net/2/](https://oauth.net/2/)
  * let's not use Supabase auth to database, it should be the API

### To Do

* [ ] research OAuth to estimate time / more specifically plan
* [ ] set up refresh tokens
* [ ] sketch roles/permissions
