## Create access points

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/access_points")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"started_at\": \"2019-01-09T0000\", \"ended_at\": \"2019-01-11T0000\", \"devices_number\": 5, \"serial_number\": \"00-77777-000000\" }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/access_points \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  -d '{ "started_at": "2019-01-09T0000", "ended_at": "2019-01-11T0000", "devices_number": 5, "serial_number": "00-77777-000000" }'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/access_points",
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD"
  },
  "data": "{ \"started_at\": \"2019-01-09T0000\", \"ended_at\": \"2019-01-11T0000\", \"devices_number\": 5, \"serial_number\": \"00-77777-000000\" }"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "5c1cdad1b7b3a15622e8bd26",
        "type": "access_point",
        "attributes": {
            "ap_mac": "00:11:22:33:11:22",
            "name": "Test API",
            "ubication": "Madrid",
            "active": true,
            "serial_number": "00-77777-000000"
        }
    }
}
```

Permits create a access point for the organization that you are pointing and if the user has access to it.

### HTTP Request

`POST https://api.flameanalytics.com/v2/places/:place_id/access_points`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | true | Identifier of an organization you are targeting
ap_mac |true | Unique mac number of the device
name | true |  Name for that access point
ubication | false | Ubication for that access point
active | false | Indicates if the access point it's active. Default: false
serial_number |false | Serial number of the device


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