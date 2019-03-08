## Update market peco

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/market_pecos/a12b3a58-118f-4d91-9d62-6fbfc88c9a15")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Put.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"identifier\": \"id\", \"mac_address\": \"ac:11:23:de:67:fa\", \"ubication\": \"none\", \"user\": \"user\", \"pass\": \"pass\" }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request PUT \
  --url https://api.flameanalytics.com/v2/market_pecos/a12b3a58-118f-4d91-9d62-6fbfc88c9a15 \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  --data '{ "identifier": "id", "mac_address": "ac:11:23:de:67:fa", "ubication": "none", "user": "user", "pass": "pass" }'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/market_pecos/a12b3a58-118f-4d91-9d62-6fbfc88c9a15",
  "method": "PUT",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  },
  "data": "{ \"identifier\": \"id\", \"mac_address\": \"ac:11:23:de:67:fa\", \"ubication\": \"none\", \"user\": \"user\", \"pass\": \"pass\" }"
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
        "type": "market_peco",
        "attributes": {
            "identifier": "id",
            "mac_address": "ac:11:23:de:67:fa",
            "ubication": "none"
        }
    }
}
```
Permits to update a market peco if the user has permissions.

### HTTP Request

`PUT https://api.flameanalytics.com/v2/market_pecos/a12b3a58-118f-4d91-9d62-6fbfc88c9a15`


### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | true | Identification of a place
identifier | false | Indicates the identifier of the market peco
mac_address | true | Indicates the mac of the market peco
ubication | false | Indicates the ubication of the object
user | false | Indicates the username for accessing the object
pass | false | Indicates the password associated with the username


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a market peco
type | String | Type of the retrieve object
attributes | Object | Attributes of that market peco
identifier | String | Identifier of the retrieve object
mac_address | String | Encrypted mac of the market peco
ubication | String | Ubication of the market peco