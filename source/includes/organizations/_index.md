## List of organizations

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations")

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
  --url https://api.flameanalytics.com/v2/organizations \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations",
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
      "id": "a69a560e-0df7-4y6c-b0dc-751708181f1822",
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
    },
    {
      "id": "b18a39f4-1c3f-12d8-8d16-58a68187a5ddc7",
      "type": "organization",
      "attributes": {
          "name": "Test API",
          "active_modules": [
              "floors_and_zones",
              "health_and_safety"
          ]
      }
    }
  ],
  "meta": {
    "pagination": {
      "per_page": 25,
      "current_page": 1,
      "total_pages": 1,
      "total_objects": 2
    }
  }
}
```

Allows obtaining a list of the organizations that the user can access.

### HTTP Request

`GET https://api.flameanalytics.com/v2/organizations`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of an organization
type | String | Type of the retrieve object
attributes | Object | Attributes of that organization
name | String | Name of the organization
active_modules | Array | Array with the names of active modules that have the organization