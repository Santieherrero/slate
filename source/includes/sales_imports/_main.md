# Sales imports

## Create sales imports

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/sales_imports")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{ \"description\": \"Description\", \"sales\": [{\"date\":1514761200,\"amount\":252.4,\"quantity\":2}] }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/sales_imports \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  --data '{ "description": "Description", "sales": [{"date":1514761200,"amount":252.4,"quantity":2}] }'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/sales_imports",
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  },
   "data": "{ \"description\": \"Description\", \"sales\": [{\"date\":1514761200,\"amount\":252.4,\"quantity\":2}] }"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Response example:

```json

```

Allows creating sales imports. 
Authorization token regarding place organization.

### HTTP Request

`POST https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/sales_imports`


### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | true | Identification of a place

