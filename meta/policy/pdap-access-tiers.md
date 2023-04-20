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

**Sharing un-approved Data Sources, sometimes**

When we share a public view [like this one](https://airtable.com/shrZgN3ZWviwXpPjx) with a specific user, we will show un-approved sources which fit into the existing filter set. The goal is to help people see the results of their submissions immediately. There is some risk of vandalism, and in general we don't but it's mitigated by these factors:

* To the rest of the world (on our public view), it looks like we only show approved data sources, so the incentive for vandalism is low.
* We're sharing these geographic-specific views with people who we think are serious users, and they may share it with their network; not many people will see these un-approved data sources.
* We're still listing them as "not approved", so we are not misrepresenting them.
* In the future we'll be able to further restrict who is able to view un-approved Data Sources; maybe they can opt in, only see sources submitted by themselves or others in their community, etc.

### GitHub Actions

We often use GitHub Actions to automate tasks. The pattern for new volunteer-submitted automated utilities is that we:

1. Create a new repository where the code will live, or a new directory in an existing repo
2. Ask the volunteer to submit their code to the new repo, without worrying about automation
3. Wire up the automation ourselves, once we ensure the code meets the standard
