---
description: Powering pdap.io
---

# PDAP front page

## Project Overview

#### We're here to build a front-end foundation that can scale.

[Here's the GitHub repo](https://github.com/Police-Data-Accessibility-Project/gatsby-pdap-frontpage) for the front end.

We're currently using Gatsby, and pages are written in MDAST Syntax Tree format. Down the road, we may migrate to a headless CMS like Strapi—we're also interested in more accessible languages like JSX.

Gatsby offers a vast plugin ecosystem and can consume content from many sources. PDAP is open source, so React components written for this Gatsby site can be used in future projects.

In a perfect world we'd be using a more vanilla Gatsby configuration without markdown or mdast—just javascript and html!

## Info for Developers

### Tech

This site is built with Gatsby, a React-based static site generator that utilizes GraphQL to query content.

If you are new to these frameworks you can familiarize yourself via their docs:

* [React](https://reactjs.org/docs/getting-started.html)
* [Gatsby](https://www.gatsbyjs.org/docs/)
* [GraphQL](https://graphql.org/code/#javascript)
* [Remark](https://remark.js.org/) is used to parse files from .md to HTML.

### Etiquette

Head to [\#copywriting](https://policeaccessibility.slack.com/archives/C01KW4N1V4Z) in Slack if you'd like to collect feedback from the wider group.

Test your changes **locally first**, if possible. Include **screenshots with your PR** if you're changing something visual.

### Background

Markdown files in the top level `content` directory are sourced via the [gatsby-source-filesystem](https://www.gatsbyjs.org/packages/gatsby-source-filesystem/?=file) plugin and parsed via the [gatsby-transformer-remark](https://www.gatsbyjs.org/packages/gatsby-transformer-remark/?=markd) plugin. The content is fed as props to the React templates via [GraphQL page queries](https://www.gatsbyjs.org/docs/page-query/).

The static site content is hosted on [Github Pages](https://pages.github.com/) from the gh-pages branch. The static files are built and deployed to this branch automatically via [GitHub Actions](https://github.com/features/actions) whenever changes are merged to the master branch.

### Setup

1. Clone the repository

   `git clone https://github.com/Police-Data-Accessibility-Project/gatsby-pdap-frontpage.git`

2. Install dependencies

   `npm install`

3. Start the development server

   `npm start`

The development preview can be accessed at [localhost:8000](http://localhost:8000) The GraphQL playground can be accessed at [localhost:8000/\_\_\_playground](http://localhost:8000/___playground)

### Testing

Testing is configured according to Gatsby's [Unit Testing](https://www.gatsbyjs.org/docs/unit-testing/) docs.

You can run tests via the `npm test` command

### Staging

Merge into the `dev` branch and visit pdap.dev.

