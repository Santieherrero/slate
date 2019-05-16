## List of tags

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/tags")

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
  --url https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/tags \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/tags",
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
    "data": {
        "id": "a12b3a58-118f-4d91-9d62-6fbfc88c9a15",
        "type": "tag",
        "attributes": {
            "name": "Tag name"
        }
    }
}
```

Allows obtaining all the tags for the place that you are pointing and if the user has access to it.

### HTTP Request

`GET https://api.flameanalytics.com/v2/places/:place_id/tags`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | true | Identifier of a organization

### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of the tag
type | String | Type of the retrieve object
attributes | Object | Attributes of that place
name | String |  Name for the tag