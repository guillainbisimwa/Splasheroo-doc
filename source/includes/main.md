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

<aside class="warning">If you faild to login, you'll get this validation message: <code>"msg": "Password Invalid"</code></aside>

## Check if Email exists

> Check if email exists

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/checkEmail",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
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
    "msg": "Email exists"
}
```

> If the email doesn't exist, you'll get this message

```json
{
    "success": false,
    "msg": "Invalid Email"
}
```

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/checkEmail`

### Query Parameters

| Parameter | Type   | Description                                         |
| --------- | ------ | --------------------------------------------------- |
| email     | string | An adress mail. It's must be unique in our database |


# Vehicle

Add vehicle manually or retrieve from https://panel.ukvehicledata.co.uk/

## Add

> Add manualy


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/vehicle/add",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    id : "63dc00a716439caa3a169a08",
    RegistrationPlate : "RP2",
    licence : true,
    model : "Model",
    make : "Make",
    coulor : "red"
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
    "msg": "Vehicle added successfully"
}
```

This endpoint creates a vehicle.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/vehicle/add`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string | Id returned when sign up or sign in                 |
| RegistrationPlate     | string |                                                     |
| licence               | boolean|                                                     |
| model                 | string |                                                     |
| make                  | string |                                                     |
| coulor                | string |                                                     |

## Get 

> vehicle data from ukvehicledata

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/vehicle/getUKVD",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    registrationPlate: "KM12AKK"
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
  "success": false,
  "msg": "Vehicle found",
  "VehicleDetails": {
    "Colour": "Grey",
    "FuelType": "Diesel",
    "Make": "VOLKSWAGEN",
    "Model": "SHARAN",
    "DateFirstRegistered": "15/06/2012"
  },
}
```

> If the vehicle doesn't exist, you'll get this message

```json
{
    "success": false,
    "msg": "Vehicle not found"
}
```

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/vehicle/getUKVD`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| registrationPlate     | string |                                                     |

# Email

To verify the email address

## Email validation

> Validate an email, 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/email/send",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    email:"test@me.com",
    date: "2/10/2023",
    name: "Full name",
    id: "8464542165578654"
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
    "msg": "Email sent successfuly!"
}
```

> If faild to send an Email, you'll get this message

```json
{
    "success": false,
    "msg": "Faild to send an Email!"
}
```

This endpoint will send an email.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/email/send`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string | Id returned when sign up or sign in                 |
| email                 | string |                                                     |
| date                  | string |                                                     |
| name                  | string |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna receive an email, if not please check the Span folder
</aside>

## Check if Email is validate

> Check if email is already validate

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/email/status",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
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
    "msg": "Email is validate"
}
```

> If the email doesn't exist, you'll get this message

```json
{
    "success": false,
    "msg": "Invalid Email"
}
```

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/status`

### Query Parameters

| Parameter | Type   | Description                                         |
| --------- | ------ | --------------------------------------------------- |
| email     | string | An adress mail. It's must be unique in our database |
