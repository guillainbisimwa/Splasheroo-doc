# Introduction

Welcome to the Splasheroo API! You can use our API to access Splasheroo API endpoints, which can get informations  in our database.

# Authentication

Our API is able to support user accounts with each user having the ability managing their own resources.
In order to get your API key (token), you need to Signup or login!

## Signup

> Signup a new user - get token from here


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/register",
  params: {},
  headers: {
    "content-type": "application/json",
    "role": "customer"
  },
  data: {
   fullName: "Test full name",
   password: "12345678",
   phone: "789456123",
   email: "test@me.com",
   postCode: "postCode",
   address : "address"
  },
};

axios
  .request(options)
  .then( (response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "token": "*******************************",
    "account": {
        "email": "test8@me.com",
        "completedProfile": false,
        "role": "customer",
        "roleData": {
            "customer": "63dc00a716439caa3a169a08"
        },
        "_id": "63dc00a716439caa3a169a08",
        "__v": 0,
        "fullName": "Test full name",
        "phone": "789456123",
        "postCode": "postCode",
        "address": "address"
    }
}
```

> Make sure that your API key is located in `auth_token`. In our our case id `*************`

Splasheroo API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint creates a new user.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/register`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| fullName              | string | Name of the user                                    |
| email                 | string | An adress mail. It's must be unique in our database |
| password              | string | A password                                          |
| phone                 | string |                                                     |
| postcode              | string |                                                     |
| address               | string |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna have your API key!
</aside>

<aside class="warning"> If you faild to signup, you'll get this validation message: <code>
```json
{    
   "success": false,
   "msg": "Account Already exist"
}
```
</code></aside>

## login

> login an existing user - get token from here

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/auth/login")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request.body = "{
    \"email\": \"guy@email.com\",
    \"password\": \"1234\"
}"

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://find-your-house-backend.herokuapp.com/auth/login",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    email: "guy@email.com",
    password: "1234",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
  "auth_token": "*************",
  "id": "1"
}
```

> Make sure that your API key is located in `auth_token`. In our our case id `*************`

FIND YOUR HOUSE API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint log in an existing user

### HTTP Request

`POST https://find-your-house-backend.herokuapp.com/auth/login`

### Query Parameters

| Parameter | Type   | Description                                         |
| --------- | ------ | --------------------------------------------------- |
| email     | string | An adress mail. It's must be unique in our database |
| password  | string | A password                                          |

<aside class="success">
Remember — if you post successfully, then you gonna have your API key!
</aside>

<aside class="warning"> If you faild to signup, you'll get this validation message: <code>&lt;"Invalid credentials"&gt;</code></aside>

## logout

> logout a connected user - use your token

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/users/sign_out")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Delete.new(url)
request["authorization"] = "*************",

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "DELETE",
  url: "https://find-your-house-backend.herokuapp.com/users/sign_out",
  headers: {
    authorization: "*************",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
{
  "status": "success",
  "message": "Signed out successfully"
}
```

> Make sure to replace `****************` with your API key.

FIND YOUR HOUSE API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint logout an user

### HTTP Request

`DELETE https://find-your-house-backend.herokuapp.com/users/sign_out`

> If you faild to logout, you'll get this message:

```json
{
  "status": "error",
  "error": "Access token is missing in the request"
}
```

# Houses

## Get all houses

> This endpoint retrieves all houses.

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/houses")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["authorization"] = "*************",

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://find-your-house-backend.herokuapp.com/houses",
  headers: {
    authorization: "*************",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 3,
    "price": 200.0,
    "details": "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
    "about": "House in Brgule, Serbia",
    "picture": "https://images.pexels.com/photos/259588/pexels-photo-259588.jpeg",
    "owner": "Pixabay",
    "created_at": "2021-05-03T09:14:30.922Z",
    "updated_at": "2021-05-03T09:14:30.922Z"
  },
  {
    "id": 5,
    "price": 800.0,
    "details": "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
    "about": "A single living house in Addis Ababa, Ethiopia",
    "picture": "https://images.pexels.com/photos/259588/pexels-photo-259588.jpeg",
    "owner": "Pixabay",
    "created_at": "2021-05-03T18:11:58.211Z",
    "updated_at": "2021-05-03T18:11:58.211Z"
  }
]
```

> Make sure to replace `****************` with your API key.

This endpoint retrieves all houses.

### HTTP Request

`GET https://find-your-house-backend.herokuapp.com/houses`

## Get a specific house

> This endpoint retrieves a specific houses.

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/houses/2")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["authorization"] = "*************",

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://find-your-house-backend.herokuapp.com/houses/2",
  headers: {
    authorization: "*************",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 2,
    "price": 200.0,
    "details": "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
    "about": "House in Brgule, Serbia",
    "picture": "https://images.pexels.com/photos/259588/pexels-photo-259588.jpeg",
    "owner": "Pixabay",
    "created_at": "2021-05-03T09:14:30.922Z",
    "updated_at": "2021-05-03T09:14:30.922Z"
  }
]
```

> Make sure to replace `****************` with your API key.

This endpoint retrieves all houses.

### HTTP Request

`GET https://find-your-house-backend.herokuapp.com/houses/<ID>`

### Url Parameters

| Parameter | Type    | Description                     |
| --------- | ------- | ------------------------------- |
| ID        | integer | The ID of the house to retrieve |

# Favorites

## Get all user favorites

> This endpoint retrieves all user favorites.

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/users/3/favourites")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["authorization"] = "*************",

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://find-your-house-backend.herokuapp.com/users/3/favourites",
  headers: {
    authorization: "*************",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "name",
    "user_id": 1,
    "house_id": 2,
    "created_at": "2021-05-09T19:35:43.347Z",
    "updated_at": "2021-05-09T19:35:43.347Z"
  }
  {
    "id": 6,
    "name": "name",
    "user_id": 1,
    "house_id": 1,
    "created_at": "2021-05-09T19:35:43.347Z",
    "updated_at": "2021-05-09T19:35:43.347Z"
  }
]
```

> Make sure to replace `****************` with your API key.

This endpoint retrieves all user favorites

### HTTP Request

`GET https://find-your-house-backend.herokuapp.com/users/<USERID>/favourites`

### Url Parameters

| Parameter | Type    | Description        |
| --------- | ------- | ------------------ |
| USERID    | integer | The ID of the user |

## Get a specific user favorite

> This endpoint retrieves a specific user favorite.

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://find-your-house-backend.herokuapp.com/users/3/favourites/1")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["authorization"] = "*************",

response = http.request(request)
puts response.read_body
```

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://find-your-house-backend.herokuapp.com/users/3/favourites/1",
  headers: {
    authorization: "*************",
  },
};

axios
  .request(options)
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.error(error);
  });
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 6,
    "name": "name",
    "user_id": 1,
    "house_id": 1,
    "created_at": "2021-05-09T19:35:43.347Z",
    "updated_at": "2021-05-09T19:35:43.347Z"
  }
]
```

> Make sure to replace `****************` with your API key.

This endpoint retrieves a specific user favorite.

### HTTP Request

`GET https://find-your-house-backend.herokuapp.com/users/<USERID>/favourites/<ID>`

### Url Parameter

| Parameter | Type    | Description                                          |
| --------- | ------- | ---------------------------------------------------- |
| ID        | integer | The ID of a specific user favorite house to retrieve |
| USERID    | integer | The ID of the user                                   |
