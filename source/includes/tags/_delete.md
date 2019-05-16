## Delete tag

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/tags/a12b3a58-118f-4d91-9d62-6fbfc88c9a15")

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
  --url https://api.flameanalytics.com/v2/tags/a12b3a58-118f-4d91-9d62-6fbfc88c9a15 \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/tags/a12b3a58-118f-4d91-9d62-6fbfc88c9a15",
  "method": "DELETE",
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

Permits deleting a tag if the user has permissions for it.

### HTTP Request

`DELETE https://api.flameanalytics.com/v2/tags/:id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | Indicates the tag identifier

### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of the deleted tag
type | String | Type of the retrieve object
attributes | Object | Attributes of that place
name | String |  Name for the deleted tag