## List of mac blacklists

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/mac_blacklist")

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
  --url https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/mac_blacklist \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/mac_blacklist",
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
    "data": [
        {
            "id": "a12b3a58-118f-4d91-9d62-6fbfc88c9a15",
            "type": "mac_blacklist",
            "attributes": {
                "mac": "1a:2e:70:be:88:a9"
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

Allows obtaining a list of mac blacklists which the user can access.

### HTTP Request

`GET https://api.flameanalytics.com/v2/places/:place_id/mac_blacklist`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | String | Identification of a place
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a mac blacklist
type | String | Type of the retrieve object
attributes | Object | Attributes of that mac blacklist
mac | String | Encrypted mac of the mac blacklist