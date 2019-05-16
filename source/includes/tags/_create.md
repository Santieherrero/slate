## Create tag

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/tags")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"name\": \"Tag name\" }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/tags \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  -d '{ "name": "Tag name" }'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/places/58805c2e-b96c-41a5-8542-fa11198556b3/tags",
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD"
  },
  "data": "{ \"name\": \"Tag name\" }"
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

Allows creating a new tag for a concrete place if the user has permissions for it.

### HTTP Request

`POST https://api.flameanalytics.com/v2/places/:place_id/tags`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | true | Identifier of the place you are targeting
name | true |  Name for the tag


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of the created tag
type | String | Type of the retrieve object
attributes | Object | Attributes of that place
name | String |  Name for the created tag