# PDAP Access

## General

| Tier      | Description                                                                                                                                                                                                                          | Team / Access                                                                                                                                      |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Admin     | <p>Higher-context contributors who require write access to do their work.<br><br>Members are granted access by Organizers.</p>                                                                                                       | <ul><li>GitHub repo write as needed</li><li>Discord PDAP Staff role</li><li>@pdap.io email if needed</li></ul>                                     |
| Organizer | <p>Keeping the lights on and making sure we're able to operate and access resources if one or two people leave. </p><p></p><p>Members are the board, staff, and people appointed to the PDAP nonprofit corporation by the board.</p> | <ul><li>GitHub team admin</li><li>Keybase</li><li>LastPass</li><li>Crypto wallet</li><li>Finances</li><li>All Admin items</li><li>GSuite</li></ul> |

## Data Sources form

#### Some known risks

* Spam: someone uses the form or API to submit way too much stuff in an attempt to overload us
* Sabotage: someone uses the form or API to submit data that is rude or harmful to our mission

#### Some options

* Require auth with email address (manually or with an app)
* Require auth with something fancier like Keybase
* Manually approve all entries before they're made public

#### Current solution

The risks aren't a problem, yet. In the meantime we're going to:

* Collect email addresses on the form, optionally
* Set up a moderation queue to approve submissions before they are made public
* Not embed the form into a live site, only sharing the link with individuals who ask by contacting staff in any way (explaining this process in the docs)
