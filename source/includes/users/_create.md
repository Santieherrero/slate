## Create users

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/users")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'
request.body = "{\"email\": \"example@gmail.com\", \"name\": \"Example\", \"surname\": \"SurnameTest\",
                \n \"password\": \"example!99test\", \"password_confirmation\": \"example!99test\", \"lang\": \"es\",
                \n \"role\": \"standard\", \"organizations\": [\"35425sjsd71123-213y6213\"] }"

response = http.request(request)
puts response.read_body
```

```shell
curl --request POST \
  --url https://api.flameanalytics.com/v2/users \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
  -d '{"email": "example@gmail.com", "name": "Example", "surname": "SurnameTest",
       "password": "example!99test", "password_confirmation": "example!99test",
       "lang": "es", "role": "standard", "organizations": ["35425sjsd71123-213y6213"] }'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/users",
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  },
  "data": "{\"email\": \"example@gmail.com\", \"name\": \"Example\", \"surname\": \"SurnameTest\",
          \n \"password\": \"example!99test\", \"password_confirmation\": \"example!99test\", \"lang\": \"es\",
          \n \"role\": \"standard\", \"organizations\": [\"35425sjsd71123-213y6213\"] }"
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
              "full_name": "Example SurnameTest",
              "email": "example@gmail.com",
              "photo_url": "/defaults/user_small.png",
              "lang": "es",
              "role": "estandar",
              "organizations": [
                  "35425sjsd71123-213y6213"
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

Permits create a user if the current user have permissions

### Password
The password **it's not required for logged partner users**, if you don't set the password at request, this be generated automatically with a random password.

### Authorizations
You can add authorization to a organization/s if you set a array list of organization/s id at the body request

**Important:**  If you add a list of organizations, this not add or update more for existing authorizations at the user, **always recreate that authorizations**

### HTTP Request

`POST https://api.flameanalytics.com/v2/users`


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