## Delete users

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/users/fb9b64dc-ea7f-42f0-97fa-2abe9842127")

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
  --url https://api.flameanalytics.com/v2/users \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/users/fb9b64dc-ea7f-42f0-97fa-2abe9842127",
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
  "data":
      {
          "id": "fb9b64dc-ea7f-42f0-97fa-2abe9842127",
          "type": "user",
          "attributes": {
              "full_name": "Example SurnameTest",
              "email": "example@gmail.com",
              "photo_url": "/defaults/user_small.png",
              "lang": "es",
              "role": "estandar",
              "organizations": [
                  "35425sjsd71123-213y6213"
              ]
          }
      },
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

Delete a user that belongs to your organization

### HTTP Request

`DELETE https://api.flameanalytics.com/v2/users/afb9b64dc-ea7f-42f0-97fa-2abe9842127`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | Indicate the id of the user


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of an organization
type | String | Type of the retrieve object
attributes | Object | Attributes of that organization
full_name | String | Full name for the user
photo_url | String | User photo that upload at application
lang | String | User lenguage configurated
role | String | Rol for the users requested
organizations | Array | List other organizations ids that the user can access.