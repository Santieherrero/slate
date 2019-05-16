## Update tag

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/tags/a12b3a58-118f-4d91-9d62-6fbfc88c9a15")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Put.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"name\": \"New tag name\" }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request PUT \
  --url https://api.flameanalytics.com/v2/tags/a12b3a58-118f-4d91-9d62-6fbfc88c9a15 \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  --data '{ "name": "New tag name" }'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/tags/a12b3a58-118f-4d91-9d62-6fbfc88c9a15",
  "method": "PUT",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  },
  "data": "{ \"name\": \"New tag name\" }"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Response example:

```json
{
    "data": {
        "id": "b22b3a58-118f-4d91-9d62-6fbfc88c9a26",
        "type": "tag",
        "attributes": {
            "name": "New tag name"
        }
    }
}
```
Allows to update a tag if the user has permissions for it.

### HTTP Request

`PUT https://api.flameanalytics.com/v2/tags/:id`


### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | Indicates the tag identifier


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of the updated tag
type | String | Type of the retrieve object
attributes | Object | Attributes of that place
name | String |  Name for the updated tag