## Show camera

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/cameras/a12b3a58-118f-4d91-9d62-6fbfc88c9a15")

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
  --url https://api.flameanalytics.com/v2/cameras/a12b3a58-118f-4d91-9d62-6fbfc88c9a15 \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/cameras/a12b3a58-118f-4d91-9d62-6fbfc88c9a15",
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
    "data": {
        "id": "a12b3a58-118f-4d91-9d62-6fbfc88c9a15",
        "type": "camera",
        "attributes": {
            "name": "ident",
            "mac_address": "ac:11:23:de:67:fa",
            "ubication": "exit"
        }
    }
}
```

Allows obtaining a camera if the user has permissions.


### HTTP Request

`GET https://api.flameanalytics.com/v2/cameras/a12b3a58-118f-4d91-9d62-6fbfc88c9a15`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | Indicates the market peco identifier


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a camera
type | String | Type of the retrieve object
attributes | Object | Attributes of that camera
name | String | Name of the retrieve object
mac_address | String | Encrypted mac of the camera
ubication | String | Ubication of the camera
