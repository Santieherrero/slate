---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - javascript

toc_footers:
  - <a href='https://dashboard.flameanalytics.com'>Dashboard Flame</a>
  - <a href='/users/sign_out'>Sign out</a>

includes:
  - { authentication: [] }
  - { errors: [] }
  - { organizations: [search, index, create, delete]}
  - { users: [ index, show, create, update, delete]}
  - { licenses: [index, create, update]}
  - { locations: [ search, index, create, delete] }
  - { "access_points": [index, create, delete] }
  - { presence: [] }
  - { affluence: [] }
  - { sensors: [ organizations, places ] }

search: false
---

# Introduction

**Flame Analytics API** is organized around **_REST_**. Our API has predictable, resource-oriented URLs and uses HTTP response codes to indicate API successful and errors request.

We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients and developers.

We support (CORS) Cross-origin Resource Sharing, allowing you to interact securely with our API from a client-side web application as well as for app mobiles. JSON is returned by all API responses, including errors.
In all requests that require parameters such as (POST, PUT - PATCH), these must be entered using JSON format, if it is done using another format it will be specified in its description.