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
Remember — if you post successfully, then you gonna receive an email, if not please check the Spam folder
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
    "msg": "Email not validated"
}
```

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/status`

### Query Parameters

| Parameter | Type   | Description                                         |
| --------- | ------ | --------------------------------------------------- |
| email     | string | An adress mail. It's must be unique in our database |


# CAR WASH SERVICES

We have only two type of services. Outside & Inside wash @ GBP 25.30 and Outside wash only @ GBP 20.30

## Add a service

> Post a sevice and save it in our database, 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/servie/add",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    serviceName: "Outside wash only",
    price: "20.30",
    startTimeOfDays: "08:00:00",
    endTimeOfDays: "20:00:00",
    duration: "45",
    contact: "+243841550213", 
    address: "10 Downing street"
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
    "msg": "Service added successfuly!"
}
```

This endpoint will add a service.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/service/add`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| serviceName           | string |                                                     |
| price                 | number |                                                     |
| startTimeOfDays       | string |                                                     |
| endTimeOfDays         | string |                                                     |
| duration              | number |                                                     |
| contact               | string |                                                     |
| address               | string |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>


## Get all services

> Get all sevices saved in our database, 


```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/servie/all",
  params: {},
  headers: {
    "content-type": "application/json",
  }
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
    "msg": "Service fetched successfully",
    "services": [
        {
            "_id": "63e00d434969108cb5bc1794",
            "serviceName": "Outside wash only",
            "price": 20.3,
            "duration": 45,
            "contact": "+243841550213",
            "address": "10 Downing street",
            "__v": 0
        },
        {
            "_id": "63e014aa4969108cb5bc1797",
            "serviceName": "Outside & Inside",
            "price": 25.3,
            "duration": 60,
            "contact": "+243841550213",
            "address": "10 Downing street",
            "__v": 0
        }
    ]
}
```

This endpoint will fetch all services.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/service/all`

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>


## Get single service

> Get a single service by it's ID, 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/servie/find",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    id: "63e00d434969108cb5bc1794"
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
    "msg": "Service found",
    "service": [
        {
            "_id": "63e00d434969108cb5bc1794",
            "serviceName": "Outside wash only",
            "price": 20.3,
            "duration": 45,
            "contact": "+243841550213",
            "address": "10 Downing street",
            "__v": 0
        }
    ]
}
```

This endpoint will fecth a single service.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/service/find`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and a service ojbect
</aside>


# RIDERS

Riders management

## Add a rider

> Post a rider and save in our database, 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/rider/add",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    name: "James Bond", 
    idNumber: "124578", 
    gsmId: "321654987", 
    address: "10 Downing street", 
    email: "james@test.me", 
    emergencyContact: "+243841550213"
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
    "msg": "Rider added successfuly!"
}
```

This endpoint will add a service.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/rider/add`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| name                  | string |                                                     |
| idNumber              | number |                                                     |
| gsmId                 | string |                                                     |
| address               | string |                                                     |
| email                 | number |                                                     |
| emergencyContact      | string |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>


## Get all riders

> Get all sevices saved in our database, 

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/rider/all",
  params: {},
  headers: {
    "content-type": "application/json",
  }
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
    "msg": "Rider fetched successfully",
    "riders": [
        {
            "_id": "63e01b1d747fbe40578423db",
            "name": "James Bond",
            "activate": false,
            "idNumber": "124578",
            "gsmId": "321654987",
            "address": "10 Downing street",
            "email": "james@test.me",
            "emergencyContact": "+243841550213",
            "timestamp": "2023-02-05T20:56:12.077Z",
            "__v": 0
        }
    ]
}
```

This endpoint will fetch all riders.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/rider/all`

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>


## Get single rider

> Get a single rider by it's ID, 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/rider/find",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    id: "63e01b1d747fbe40578423db"
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
    "msg": "Rider found",
    "rider": [
        {
            "_id": "63e01b1d747fbe40578423db",
            "name": "James Bond",
            "activate": false,
            "idNumber": "124578",
            "gsmId": "321654987",
            "address": "10 Downing street",
            "email": "james@test.me",
            "emergencyContact": "+243841550213",
            "timestamp": "2023-02-05T20:56:12.077Z",
            "__v": 0
        }
    ]
}
```

This endpoint will fecth a single service.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/rider/find`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and a rider ojbect
</aside>
