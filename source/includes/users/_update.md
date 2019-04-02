## Update users

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/users")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Put.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{\"name\": \"Change\",\"lang\": \"en\",
                 \"organizations\": [\"35425sjsd71123-213y6213\", \"95425sjsd7658a-623yx8213\"] }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request PUT \
  --url https://api.flameanalytics.com/v2/users \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  -d '{"name": "Change","lang": "en", "organizations": ["35425sjsd71123-213y6213", "95425sjsd7658a-623yx8213"] }'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/users",
  "method": "PUT",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  },
  "data": "{\"name\": \"Change\",\"lang\": \"en\",
            \"organizations\": [\"35425sjsd71123-213y6213\", \"95425sjsd7658a-623yx8213\"] }"
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
              "full_name": "Change SurnameTest",
              "email": "example@gmail.com",
              "photo_url": "/defaults/user_small.png",
              "lang": "en",
              "role": "estandar",
              "organizations": [
                  "35425sjsd71123-213y6213",
                  "95425sjsd7658a-623yx8213"
              ]
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

Permits update a user

### Password
The password **it's not required for logged partner and admin users** at update a user, but it's require for standard users.

### Authorizations
You can update authorization to a organization/s if you set a array list of organization/s id at the body request

**Important:**  If you add a list of organizations, this not add or update more for existing authorizations at the user, **always recreate that authorizations**

### HTTP Request

`PUT https://api.flameanalytics.com/v2/users`


### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
name | true | Indicates the name name
surname | true | Surname for the user
password | true | Password for the user, **this is not required for partner users logged**
password_confirmation | true | Password confirmation
rol | false | Role for the user that will be created. Default: 'standard', this can be 'standard' or 'admin'
lang | false | Language for the user, Default: 'es'
organizations | Array | List other organizations ids that the user can access.


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