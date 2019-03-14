## Delete mac blacklists

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/mac_blacklist/a12b3a58-118f-4d91-9d62-6fbfc88c9a15")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Delete.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'

response = http.request(request)
puts response.read_body
```

```shell
curl --request DELETE \
  --url https://api.flameanalytics.com/v2/mac_blacklist/a12b3a58-118f-4d91-9d62-6fbfc88c9a15 \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/mac_blacklist/a12b3a58-118f-4d91-9d62-6fbfc88c9a15",
  "method": "DELETE",
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
        "type": "mac_blacklist",
        "attributes": {
            "mac": "1a:2e:70:be:88:a9"
        }
    }
}
```

Permits delete a mack blacklist if the user have permissions.

### HTTP Request

`DELETE https://api.flameanalytics.com/v2/mac_blacklist/:place_id`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | Indicate the mac blacklist identifier


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a mac blacklist
type | String | Type of the retrieve object
attributes | Object | Attributes of that mac blacklist
mac | String | Encrypted mac of the mac blacklist