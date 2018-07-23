# Places

## List of places

```ruby
require 'uri'
require 'net/http'

url = URI("https://pull.flameanalytics.com/api/v1/organizations/1/places/")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'

response = http.request(request)
puts response.read_body
```

```shell
curl --request GET \
  --url https://pull.flameanalytics.com/api/v1/organizations/1/places/ \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://pull.flameanalytics.com/api/v1/organizations/1/places/",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
  "places": [
    {
      "id": 33,
      "name": "Organization 1"
    },
    {
      "id": 34,
      "name": "Organization 2"
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

This endpoint retrieves all places.

### HTTP Request

`GET https://pull.flameanalytics.com/api/v1/organizations/33/places`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
organization_id | true | Identifier of an organization
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page
