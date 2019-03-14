## Create mac blacklist

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/mac_blacklist")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"name\": \"MAC test\", \"mac\": \"1a:11:a7:67:8f:ce\"}"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/mac_blacklist \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  -d '{ "name": "MAC test", "mac": "1a:11:a7:67:8f:ce" }'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/mac_blacklist",
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  },
  "data": "{ \"name\": \"MAC test\", \"mac\": \"1a:11:a7:67:8f:ce\"}"
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
        "type": "mac_blacklist",
        "attributes": {
            "mac": "1a:2e:70:be:88:a9"
        }
    }
}
```
Permits create a mac blacklist if the user have permissions.

### HTTP Request

`POST https://api.flameanalytics.com/v2/places/:place_id/mac_blacklist`


### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | String | Identification of a place
name | false | Indicates the mac blacklist name
mac | true | Indicates the mac of the mac blacklist


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a mac blacklist
type | String | Type of the retrieve object
attributes | Object | Attributes of that mac blacklist
mac | String | Encrypted mac of the mac blacklist