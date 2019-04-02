## List users

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/users")

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
  --url https://api.flameanalytics.com/v2/users \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/users",
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
          "id": "fb9b64dc-ea7f-42f0-97fa-2abe9842127",
          "type": "user",
          "attributes": {
              "full_name": "User example",
              "photo_url": "/defaults/user_small.png",
              "lang": "es",
              "role": "estandar",
              "organizations": [
                  "e844e5ee-ccd4-49a2-9151-e3d28dd2f7c7"
              ]
          }
      },
      { ... },
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

Allows to obtain a list of the users depending on the privileges and the organizations which you belong.

### HTTP Request

`GET https://api.flameanalytics.com/v2/users`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of an users
type | String | Type of the retrieve object
attributes | Object | Attributes of that users
full_name | String | Full name for the user
photo_url | String | User photo that upload at application
lang | String | User lenguage configurated
role | String | Rol for the users requested
organizations | Array | List of organizations ids that the user can access.


