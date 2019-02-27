## Organization sensors

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/sensors")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request = Net::HTTP::Get.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'

response = http.request(request)
puts response.read_body
```

```shell
curl --request GET \
  --url https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/sensors \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/sensors",
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

> Response example:

```json
{
    "data": [
        {
            "id": "acc57a6b-7d86-4843-b5c2-128e128fa680",
            "type": "sensor",
            "attributes": {
                "name": "ac:cc:8e:a9:46:b4",
                "type": "camera",
                "ap_mac": "ac:cc:8e:a9:46:b4",
                "last_seen": "2019-02-06T09:28:56.592Z",
                "sensor_health": "error",
                "organization_id": "7b85c755-aeba-482b-a07a-f375375c33e4"
            }
        },
        {
            "id": "127e128f-7d86-4843-b5c2-128e128fa680",
            "type": "sensor",
            "attributes": {
                "name": "Axis-ACCC8E0F7B4B",
                "type": "affluence",
                "ap_mac": "AC:CC:6E:1F:7B:4B",
                "last_seen": "2019-02-27T12:28:56.592Z",
                "sensor_health": "ok",
                "organization_id": "7b85c755-aeba-482b-a07a-f375375c33e4"
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

Allows obtaining a list of sensors per organization which the user can access.

### HTTP Request

`GET https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/sensors`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a sensor
type | String | Type of the retrieve object
attributes | Object | Attributes of that sensor
name | String | Name of the sensor
type | String | Concrete type of the sensor
ap_mac | String | Mac of the retrieve object
last_seen | String | **ISO 8601**, last seen active date and hours
sensor_health | String | Health of the retireve sensor
organization_id | String | Identification of organization
