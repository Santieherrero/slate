## Create camera

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/cameras")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"identifier\": \"name\", \"mac_address\": \"ac:11:23:de:67:fa\", \"ubication\": \"exit\" }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/cameras \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  --data '{ "identifier": "name", "mac_address": "ac:11:23:de:67:fa", "ubication": "exit" }'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/cameras",
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  },
   "data": "{ \"identifier\": \"name\", \"mac_address\": \"ac:11:23:de:67:fa\", \"ubication\": \"exit\" }"
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
            "name": "name",
            "mac_address": "ac:11:23:de:67:fa",
            "ubication": "exit"
        }
    }
}
```
Allows creating a camera if the user has permissions.

### HTTP Request

`POST https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/cameras`


### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | true | Identification of a place
identifier | false | Indicates the identifier of the camera
mac_address | true | Indicates the mac of the camera
ubication | false | Indicates the ubication of the object


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a camera
type | String | Type of the retrieve object
attributes | Object | Attributes of that camera
name | String | Name of the retrieve object
mac_address | String | Encrypted mac of the camera
ubication | String | Ubication of the camera