## Search organizations

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations?q=Cosmetic&fields=name")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'

response = http.request(request)
puts response.read_body
```

```shell
curl --request GET \
  --url https://api.flameanalytics.com/v2/organizations?q=Cosmetic&fields=name \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations?q=Cosmetic&fields=name",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Response example:

```json
{
  "data": [
    {
      "id": "a69a560e-0df7-4y67c-b0dc-75081811f1822",
      "type": "organization",
      "attributes": {
          "name": "Cosmetic One",
          "active_modules": [
              "affluence",
              "presence",
              "sales",
              "maps",
              "captive_portals",
              "queues",
              "floors_and_zones",
              "occupation_in_zones",
              "occupation",
              "lanes",
              "marketing",
              "dashboard",
              "places"
          ]
      }
    }
  ],
  "meta": {
    "pagination": {
      "per_page": 25,
      "current_page": 1,
      "total_pages": 1,
      "total_objects": 1
    }
  }
}
```

Allows obtaining a list of the organizations that the user can access and search with the necessary params for query the search

### HTTP Request

`GET https://api.flameanalytics.com/v2/organizations?q=Cosmetic&fields=name`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
q | false | Text query to search
fields | false | Columns for search at database level, only permit this columns: **'name', 'external_id'**
page | false | Indicates the number page of list
per_page | false | Indicates de number of objets per page


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of an organization
type | String | Type of the retrieve object
attributes | Object | Attributes of that organization
name | String | Name of the organization
active_modules | Array | Array with the names of active modules that have the organization
