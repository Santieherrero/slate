## List of access points

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/access_points")

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
  --url https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/access_points \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/access_points",
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
  "data": [
        {
            "id": "5c1cdad1b7b3a1735622e8bd26",
            "type": "access_point",
            "attributes": {
                "ap_mac": "00:11:22:33:11:22",
                "name": "Test API",
                "ubication": "Madrid",
                "active": true,
                "serial_number": "00-15554-000000"
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

Allows obtaining all the access points for the organization that you are pointing and if the user has access to it.

### HTTP Request

`GET https://api.flameanalytics.com/v2/places/:place_id/access_points`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | true | Identifier of a organization
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page

### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of the access point
type | String | Type of the retrieve object
attributes | Object | Attributes of that place
ap_mac | String | Unique mac number of the device
name | String |  Name for that access point
ubication | String | Ubication for that access point
active | Boolean | Indicates if the access point it's active
serial_number | String | Serial number of the device