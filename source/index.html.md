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
  - { pagination: [] }
  - { legend: "Core resources"}
  - { users: [ index, show, create, update, delete]}
  - { organizations: [search, index, create, delete]}
  - { locations: [ search, index, create, delete] }
  - { licenses: [index, create, update]}
  - { legend: "analytics"}
  - { "presence": [ index ] }
  - { "affluence": [ index ] }
  - { "conversion": [] }
  - { legend: "Guest wifi"}
  - { "wifi_experience": [index, show] }
  - { "wifi_users": [search, index] }
  - { "vouchers": [index, create, update, delete] }
  - { legend: "devices"}
  - { "access_points": [index, create, delete] }
  - { counters: [index, create, update, delete] }
  - { cameras: [index, show, create, delete] }
  - { legend: "Tools"}
  - { sensors: [ organizations, places ] }
  - { "sales_imports": [] }
  - { "mac_blacklists": [index, create, delete] }
  - { "tags": [index, show, create, update, delete]}
  - { legend: "legacy"}
  - { "presence_legacy": [] }
  - { "affluence_legacy": [] }


search: false
---

# Introduction

**Flame Analytics API** is organized around **_REST_**. Our API has predictable, resource-oriented URLs and uses HTTP response codes to indicate API successful and errors request.

We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients and developers.

We support (CORS) Cross-origin Resource Sharing, allowing you to interact securely with our API from a client-side web application as well as for app mobiles. JSON is returned by all API responses, including errors.
In all requests that require parameters such as (POST, PUT - PATCH), these must be entered using JSON format, if it is done using another format it will be specified in its description.