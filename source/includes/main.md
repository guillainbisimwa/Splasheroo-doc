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
> If you faild to signup, you'll get this :

```json
{    
   "success": false,
   "msg": "Account Already exist"
}
```

> Make sure that your API key is located in `token`. In our our case id `*************`

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
"msg": "Account Already exist"
</code></aside>

## login

> login an existing user - get token from here

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/login",
  params: {},
  headers: {
    "content-type": "application/json",
    "role": "customer"
  },
  data: {
   password: "12345678",
   email: "test@me.com",
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
   "token": "*****************************",
   "account": {
      "roleData": {
         "customer": "63dbf013d61a9eaaffb4e47f"
      },
      "_id": "63dbf013d61a9eaaffb4e47f",
      "email": "test@me.com",
      "completedProfile": false,
      "role": "customer",
      "__v": 0,
      "fullName": "Test full name",
      "phone": "789456123",
      "postCode": "postCode",
      "address": "address"
}
```

> Make sure that your API key is located in `token`. In our our case id `*************`

Splasheroo API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: *************`

This endpoint log in an existing user

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/login`

### Query Parameters

| Parameter | Type   | Description                                         |
| --------- | ------ | --------------------------------------------------- |
| email     | string | An adress mail. It's must be unique in our database |
| password  | string | A password                                          |

<aside class="success">
Remember — if you post successfully, then you gonna have your API key!
</aside>

<aside class="warning"> If you faild to signup, you'll get this validation message: <code>"msg": "Password Invalid"</code></aside>
