# Organizations

## List of organizations

```ruby
require 'uri'
require 'net/http'

url = URI("https://pull.flameanalytics.com/api/v1/organizations")

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
  --url https://pull.flameanalytics.com/api/v1/organizations \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://pull.flameanalytics.com/api/v1/organizations",
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
  "organizations": [
    {
      "id": 11,
      "name": "Organization 1",
      "active_modules": [
        "presence",
        "captive_portals",
        "marketing",
        "dashboard",
        "places"
      ]
    },
    {
      "id": 34,
      "name": "Organization 2",
      "active_modules": [
        "affluence",
        "presence",
        "sales",
        "dashboard",
        "places"
      ]
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

`GET https://pull.flameanalytics.com/api/v1/organizations`


### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of an organization
name | String | Name of organization
active_modules | Array | Array with the name of active modules that have the organization
