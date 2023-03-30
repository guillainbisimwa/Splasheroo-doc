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
      "address": "address",  
      "stripeCustomerId": "",
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

# Customer

Get customer's Details

## Get Customer By ID

> Get single Customer By ID


```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/customer/434343a34df34a3s4asf",
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
    "msg": "Customer Details for 63e8b4ce428e36c929691f64 fetched successfully",
    "customer": {
        "customer": [
            {
                "location": {
                    "coordinates": []
                },
                "_id": "63e8b4ce428e36c929691f64",
                "fullName": "John",
                "phone": "789456123",
                "postCode": "postCode",
                "address": "address",
                "stripeCustomerId": "",
                "__v": 0
            }
        ],
        "account": [
            {
                "roleData": {
                    "customer": "63e8b4ce428e36c929691f64"
                },
                "_id": "63e8b4cd428e36c929691f62",
                "email": "test15@me.com",
                "completedProfile": false,
                "role": "customer",
                "__v": 0
            }
        ]
    }
}
```

This endpoint will fecth a single CUSTOMER.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/customer/:id`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string |  Passed as params                                   |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and a customer ojbect
</aside>

## Get Customer By Email

> Get single Customer By email


```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/customer/getByEmail/asif@liorra.io",
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
    "msg": "Customer Details for asif@liorra.io fetched successfully",
    "customer": {
        "customer": [],
        "account": {
            "roleData": {
                "customer": "6411772d79745016c53abfb3"
            },
            "_id": "6411772d79745016c53abfb1",
            "email": "asif@liorra.io",
            "completedProfile": true,
            "role": "customer",
            "__v": 0
        }
    }
}
```

This endpoint will fecth a single CUSTOMER.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/customer/getByEmail/:email`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| email                 | string |  Passed as params                                   |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and a customer ojbect
</aside>

## Delete a customer

> Delete the customer's associated data


```javascript
import axios from "axios";

const options = {
  method: "DELETE",
  url: "https://splasheroo-backend.herokuapp.com/api/customer/434343a34df34a3s4asf",
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
    "msg": "Account deleted",
}
```

This endpoint will delete a single CUSTOMER.

### HTTP Request

`DELETE https://splasheroo-backend.herokuapp.com/api/customer/:id`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string |  Passed as params                                   |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and a customer ojbect
</aside>

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

## Get Vehicle info from UKVD

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


## Get Vehicle 

> vehicle data from ukvehicledata

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/vehicle/get",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    id: "63dc00a716439caa3a169a08"
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
    "msg": "Vehicle fetched successfully!",
    "vehicle": [
        {
            "_id": "63dcde4dfb6a27a947f255a1",
            "RegistrationPlate": "RP",
            "model": "Model",
            "make": "make",
            "coulor": "red",
            "customer": "63dc00a716439caa3a169a08",
            "__v": 0
        },
        {
            "_id": "63dce56ebdace4978ef94131",
            "RegistrationPlate": "RP2",
            "licence": true,
            "model": "Model",
            "make": "make",
            "coulor": "red",
            "customer": "63dc00a716439caa3a169a08",
            "__v": 0
        },
        {
            "_id": "63dce961351de7dd046c49f6",
            "RegistrationPlate": "RP2",
            "licence": true,
            "model": "Model",
            "make": "make",
            "coulor": "red",
            "customer": "63dc00a716439caa3a169a08",
            "__v": 0
        }
    ]
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

`POST https://splasheroo-backend.herokuapp.com/api/vehicle/get`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string | Customer's ID                                       |


## Update Vehicle

> Update vehicle

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/vehicle/update",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    id : "63e0c60d62c9e9978212d600",
    RegistrationPlate : "RP2",
    licence : true,
    model : "Model2",
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
    "msg": "Vehicle updated successfully!",
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

`POST https://splasheroo-backend.herokuapp.com/api/vehicle/update`

### Query Parameters


| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string | Vecicle ID                                          |
| RegistrationPlate     | string |                                                     |
| licence               | boolean|                                                     |
| model                 | string |                                                     |
| make                  | string |                                                     |
| coulor                | string |                                                     |

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

## Reset Password

> Reset password, 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/email/reset",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    email:"test@me.com",
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

`POST https://splasheroo-backend.herokuapp.com/api/email/reset`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| email                 | string |                                                     |

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


# Car Wash Service

We have only two type of services. Outside & Inside wash @ GBP 25.30 and Outside wash only @ GBP 20.30

## Add a service

> Post a sevice and save it in our database, 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/service/add",
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
    allService : ["Exterior Bodywork", "Exterior Glass", "Exterior Trim", "Alloys", "Tyre Shine"],
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
| allService            | array  | An array of string                                                |


<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>


## Get all services

> Get all sevices saved in our database, 


```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/service/all",
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
            "_id": "63e75fef580c7eb24880c99b",
            "serviceName": "Exterior & Interior",
            "allService": [
                "Exterior Bodywork",
                "Exterior Glass",
                "Exterior Trim ",
                "Alloys",
                "Tyre Shine",
                "Door Shuts",
                "Interior Vacuum",
                "Dashboard Wipe",
                "Center Console Wiped",
                "Anti-bacterial Treatment"
            ],
            "price": 25,
            "duration": 60,
            "contact": "+243841550213",
            "__v": 0
        },
        {
            "_id": "63e76037580c7eb24880c99e",
            "serviceName": "Exterior Only",
            "allService": [
                "Exterior Bodywork",
                "Exterior Glass",
                "Exterior Trim",
                "Alloys",
                "Tyre Shine"
            ],
            "price": 20,
            "duration": 60,
            "contact": "+243841550213",
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
  url: "https://splasheroo-backend.herokuapp.com/api/service/find",
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
            "_id": "63e76037580c7eb24880c99e",
            "serviceName": "Exterior Only",
            "allService": [
                "Exterior Bodywork",
                "Exterior Glass",
                "Exterior Trim",
                "Alloys",
                "Tyre Shine"
            ],
            "price": 20,
            "duration": 60,
            "contact": "+243841550213",
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


# Riders

Riders management

## Add a rider

> Post a rider and save in Gsmtasks, 

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
    first_name: "Guy",
    last_name: "Simons",
    email: "guy@test.me",
    phone: "+47123456789",
    //password: "123456",
    raw_address: "Prime Minister & First Lord of the Treasury",
    formatted_address: "10 Downing street",
    longitude: 51.503038,
    latitude: -0.128371,
    google_place_id: "",
    point_of_interest: "",
    street: "",
    house_number: "",
    apartment_number: "",
    city: "",
    state: "",
    postal_code: "",
    country: "",
    country_code: ""
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
| first_name            | string |                                                     |
| last_name             | number |                                                     |
| email                 | string |                                                     |
| phone                 | string |                                                     |
| raw_address           | number |                                                     |
| longitude             | number |                                                     |
| latitude              | number |                                                     |
| formatted_address     | string |                                                     |
| google_place_id       | string |                                                     |
| point_of_interest     | string |                                                     |
| street                | string |                                                     |
| house_number          | number |                                                     |
| apartment_number      | string |                                                     |
| city                  | string |                                                     |
| state                 | string |                                                     |
| postal_code           | string |                                                     |
| country               | string |                                                     |
| country_code          | string |                                                     |

<aside class="success">
Remember — if you post successfully, then the rider will receive an Email from GSMTASK team to confirm his 
account Creation
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
    "msg": "Riders fetched successfully",
    "fullRiders": [
        {
            "_id": "6401e6f5475aa38bb675e8dd",
            "email": "armel2@test.me",
            "gsmTaskUrl": "https://api.gsmtasks.com/users/73228f67-d005-49d7-9d44-d1dd92768512/",
            "activate": false,
            "timestamp": "2023-03-03T12:12:18.743Z",
            "__v": 0,
            "id": "73228f67-d005-49d7-9d44-d1dd92768512",
            "url": "https://api.gsmtasks.com/users/73228f67-d005-49d7-9d44-d1dd92768512/",
            "first_name": "Armel2",
            "last_name": "Bent2",
            "display_name": "Armel2 Bent2",
            "phone": "+2345678978",
            "intercom_hash": "8b7663d96308a98b6875804ec2ed47b48dabee38f8deff64458ea3dea272d1c1",
            "signature_image": null
        },
        {
            "_id": "6401e82e11943a90f9f028b5",
            "email": "omar@test.me",
            "gsmTaskUrl": "https://api.gsmtasks.com/users/9e248c26-5202-4639-9718-5396ac08c190/",
            "activate": false,
            "timestamp": "2023-03-03T12:29:12.997Z",
            "__v": 0,
            "id": "9e248c26-5202-4639-9718-5396ac08c190",
            "url": "https://api.gsmtasks.com/users/9e248c26-5202-4639-9718-5396ac08c190/",
            "first_name": "Ahmed",
            "last_name": "Omar",
            "display_name": "Ahmed Omar",
            "phone": "+234567897898",
            "intercom_hash": "f5bb7ec3ee11b90b78bfdf0dfa9edc5e4c13c46a9e630247a149f427edfd0173",
            "signature_image": null
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
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/rider/find/asdf1sd1f1sd1gsd1",
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
    "msg": "Rider found",
    "rider": {
        "_id": "6401e6f5475aa38bb675e8dd",
        "email": "armel2@test.me",
        "gsmTaskUrl": "https://api.gsmtasks.com/users/73228f67-d005-49d7-9d44-d1dd92768512/",
        "activate": false,
        "timestamp": "2023-03-03T12:12:18.743Z",
        "__v": 0,
        "id": "73228f67-d005-49d7-9d44-d1dd92768512",
        "url": "https://api.gsmtasks.com/users/73228f67-d005-49d7-9d44-d1dd92768512/",
        "first_name": "Armel2",
        "last_name": "Bent2",
        "display_name": "Armel2 Bent2",
        "phone": "+2345678978",
        "intercom_hash": "8b7663d96308a98b6875804ec2ed47b48dabee38f8deff64458ea3dea272d1c1",
        "signature_image": null
    }
}
```

This endpoint will fecth a single Rider.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/rider/find/:id`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and a rider ojbect
</aside>

# Banking Card

Bank Card management throught STRIPE You can a cards on a customer in order to charge the customer later.

## Add a Bank CARD

> Post a Credit Card and save in our database, 

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/bankCard/add",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    cardNumber: "4242424242424242", 
    cardHolderName: "Nicolas Brody", 
    expiryDate: "02/24", 
    cvvCvc: "314", 
    customer: "63db5cf616391c961dc3a4e5",
    email : "test15@me.com"
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
    "msg": "BankCard added successfully",
    "bankCard": {
        "stripeCardId": "card_1MklmbDSebOil4xLPQaiRWcq",
        "stripeCustomerId": "cus_NVnNyjUO1EtbxQ",
        "stripeToken": "tok_1MklmcDSebOil4xL6rY6tKIX",
        "verified": false,
        "customer": "63e78c8efaf9b5d76acb65fc",
        "_id": "640da3f5bd1565937686af24",
        "__v": 0
    }
}
```

This endpoint will add a BankCard.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/bankCard/add`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| cardNumber            | string |                                                     |
| cardHolderName        | number |                                                     |
| expiryDate            | string |                                                     |
| cvvCvc                | string |                                                     |
| customer              | number | ID of an existing customer                          |
| email                 | string | email of an existing customer                       |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>

## Get Card details

> Get a Credit card details saved in our database, 

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/bankCard/details/63db5cf616391c961dc3a4e5",
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
    "cardList": [
        {
            "_id": "63efc3ec20763151d87052be",
            "stripeCardId": "card_1McYRbDSebOil4xLEngZjrMu",
            "stripeCustomerId": "cus_NNJ3uS46jcceSx",
            "stripeToken": "tok_1McYRcDSebOil4xLKkm3C3nl",
            "verified": false,
            "customer": "63e78c8efaf9b5d76acb65fc",
            "__v": 0,
            "last4": "4242",
            "brand": "Visa"
        },
        {
            "_id": "63efc53f20763151d87052c3",
            "stripeCardId": "card_1McYX4DSebOil4xLDJS8QENb",
            "stripeCustomerId": "cus_NNJ9RGdW5xRm8V",
            "stripeToken": "tok_1McYX4DSebOil4xLWQmT2GN2",
            "verified": false,
            "customer": "63e78c8efaf9b5d76acb65fc",
            "__v": 0,
            "last4": "4242",
            "brand": "Visa"
        }
    ]
}
```

This endpoint will show you 4 last digits of your card.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/bankCard/details/:id`

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and all bookings
</aside>

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string |  ID of an existing customer                         |


## Delete a Card

> Delete a Credit card, 

```javascript
import axios from "axios";

const options = {
  method: "DELETE",
  url: "https://splasheroo-backend.herokuapp.com/api/bankCard/details/63ea14d39f2bdfe3554c67b9",
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
    "msg": "Card deleted successfully"
  }
```

This endpoint will delete your card from STRIPE.

### HTTP Request

`DELETE https://splasheroo-backend.herokuapp.com/api/bankCard/delete/:id`

<aside class="success">
Remember — if you delete successfully, then you gonna receive a success message and all bookings
</aside>

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string |  ID of an existing card                             |

# Promo Code

Promo Code management

## Add a Promo Code

> Post a promoCode and save in our database, 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/promoCode/add",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    amount: "5", 
    code: "x2023", 
    expireDate: "2023-10-01T12:00:59"
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
    "msg": "PromoCode added successfuly!"
}
```

This endpoint will add a promoCode.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/promoCode/add`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| amount                | string |                                                     |
| code                  | number |                                                     |
| expireDate            | string | in this format: YYYY-mm-ddTHH:MM:ss                 |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>


## Get single promo Code

> Get a single promo Code by it CODE, 

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/promoCode/find/x2023",
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
    "msg": "PromoCode found",
    "promoCode": [
        {
            "_id": "63e0269a2efe25d61bfbda03",
            "amount": 5,
            "code": "x2023",
            "expireDate": "2023-10-01T12:00:59",
            "timestamp": "2023-02-05T21:44:36.539Z",
            "__v": 0
        }
    ]
}
```

This endpoint will fecth a single promoCode.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/promoCode/find/:code`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| code                  | string | Existing promoCode's code                           |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and a promoCode ojbect
</aside>


# Booking

Booking management

## Add a Booking

> Post a booking and save it in (GSMTASKS)['https://app.gsmtasks.com/tasks'] , 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/booking/add",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    ref: "3FINAL200",
    userId:"63e8b4ce428e36c929691f64",
    address:"Leicester LE2 2FB, UK",
    date:"2023-02-21T06:30:00.000Z",
    endTime:"11:00",
    latitude:37.33233141,
    location:"60 Gartree Road  Leicester Leicestershire",
    longitude:-122.0312186,
    notes:"test notes",
    postCode:"le22fw",
    promocode:"FREE20",
    service:"63e75fef580c7eb24880c99b",
    startTime:"10:00",
    vechile:"63e0c60d62c9e9978212d600",
    paymentStatus: "waiting"
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
    "msg": "Booking added successfully",
    "task": {
    "_id": "63effb3b15a01bf0413ef89e",
    "status": "waiting",
    "paymentStatus": "waiting",
    "startTime": "10:00",
    "endTime": "11:00",
    "car": "63e0c60d62c9e9978212d600",
    "customer": "63e8b4ce428e36c929691f64",
    "service": "63e75fef580c7eb24880c99b",
    "timestamp": "2023-02-17T22:09:31.000Z",
    "__v": 0,
    "id": "a70c2561-bc9d-4a72-b6ef-3bbd36116d2a",
    "external_id": "63effb3b15a01bf0413ef89e",
    "reference": "3FINAL200",
    "barcodes": [ "63e8b4ce428e36c929691f64" ],
    "url": "https://api.gsmtasks.com/tasks/a70c2561-bc9d-4a72-b6ef-3bbd36116d2a/",
    "account": "https://api.gsmtasks.com/accounts/040967e8-a52d-4436-80f0-77b153c783fa/",
    "state": "unassigned",
    "assignee": null,
    "order": "https://api.gsmtasks.com/orders/53c4b0d9-38bb-46c9-b94f-0c59f0a35443/",
    "orderer_name": null,
    "route": null,
    "category": "assignment",
    "contact": 
    { 
      "name": "Splasheroo",
      "company": "Splasheroo Tech",
      "phones": [ "+270000000000" ],
      "emails": [ "splasheroo.tech@gmail.com" ],
      "notes": "test notes" 
    },
    "address": 
    { 
      "raw_address": "Leicester LE2 2FB, UK",
      "formatted_address": "60 Gartree Road  Leicester Leicestershire",
      "location": { "type": "Point", "coordinates": [ -122.0312186, 37.33233141 ] },
      "google_place_id": "",
      "point_of_interest": "",
      "street": "",
      "house_number": "",
      "apartment_number": "",
      "city": "",
      "state": "",
      "postal_code": "le22fw",
      "country": "United Kingdom",
      "country_code": "UK",
      "geocoded_at": "2023-02-18T06:10:04.928463+08:00",
      "geocode_failed_at": null 
    },
    "contact_address": null,
    "contact_address_external_id": null,
    "description": "Exterior & Interior",
    "complete_after": "2023-02-18T06:10:04.948296+08:00",
    "complete_before": "2023-02-21T14:30:00+08:00",
    "scheduled_time": "2023-02-21T14:30:00+08:00",
    "completed_at": null,
    "cancelled_at": null,
    "auto_assign": false,
    "assignee_proximity": "away",
    "position": 1676673811.74039,
    "priority": 0,
    "duration": "00:15:00",
    "size": null,
    "forms": {},
    "documents": [],
    "signatures": [],
    "metafields": {},
    "trackers": [],
    "issues": [],
    "counts": 
    { 
      "events": 1,
      "documents": 0,
      "signatures": 0,
      "forms": 0,
      "forms_completed": null 
    },
    "actions": [ "assign", "cancel" ],
    "created_at": "2023-02-18T06:10:04.951676+08:00",
    "updated_at": "2023-02-18T06:45:11.764140+08:00" }
  }
}
```

This endpoint will add a Booking.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/booking/add`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| userId                | id     | id                                                  |
| ref                   | String |                                                     |
| address               | string |                                                     |
| date                  | date   |                                                     |
| endTime               | string |                                                     |
| latitude              | number |                                                     |
| location              | string |                                                     |
| longitude             | number |                                                     |
| notes                 | string |                                                     |
| postCode              | string |   CODE                                              |
| promoCode             | string |                                                     |
| service               | string |  id                                                 |
| startTime             | string |                                                     |
| vechile               | string |  id                                                 |
| paymentStatus         | string |  It can be `waiting`, `completed` or `canceled`     |


<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>

## Update Booking paymentStatus

> Change `paymentStatus` from `Waiting` to `Complete`, 


```javascript
import axios from "axios";

const options = {
  method: "PUT",
  url: "https://splasheroo-backend.herokuapp.com/api/booking/updatePaymentStatus",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    id: "63efd9d0caf0aa67a2647164",
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
    "msg": "Booking payment status updated successfully!"
}
```

This endpoint will change `paymentStatus` from `Waiting` to `Complete`, 

### HTTP Request

`PUT https://splasheroo-backend.herokuapp.com/api/booking/updatePaymentStatus`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string | id                                                  |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>

## List all bookings

> Get all bookings saved in GSMTASKS

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/booking/all",
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
    "msg": "Bookings fetched successfully",
    "fullTasks": [
        {
            "_id": "641c353cb76aae80f7d25ad4",
            "date": "2023-03-24T06:30:00.000Z",
            "paymentStatus": "completed",
            "startTime": "10:00",
            "endTime": "11:00",
            "car": {
                "_id": "641b072facceb593aac0a15e",
                "RegistrationPlate": "KM12AKK",
                "licence": true,
                "model": "SHARAN",
                "make": "VOLKSWAGEN",
                "coulor": "Grey",
                "customer": "641b06c0acceb593aac0a159",
                "__v": 0
            },
            "customer": {
                "location": {
                    "coordinates": []
                },
                "_id": "641b06c0acceb593aac0a159",
                "fullName": "asif hassam",
                "phone": "0632770232",
                "postCode": "Le2 2fw",
                "address": "66 Gartree Road     Leicester Leicestershire",
                "__v": 0
            },
            "service": {
                "_id": "641ac6085ff9f0f660081ff4",
                "serviceName": "Exterior & Interior",
                "allService": [
                    "Exterior Bodywork",
                    "Exterior Glass",
                    "Exterior Trim",
                    "Alloys",
                    "Tyre Shine",
                    "Door Shuts",
                    "Interior Vacuum",
                    "Dashboard Wipe",
                    "Center Console Wiped",
                    "Anti-bacterial Treatment"
                ],
                "price": 25,
                "duration": "59:00",
                "__v": 0
            },
            "timestamp": "2023-03-23T11:16:48.667Z",
            "__v": 0,
            "id": "c9becb24-31bf-4307-af4e-8f8666361787",
            "external_id": "641c353cb76aae80f7d25ad4",
            "reference": "1ABCDEFGH",
            "barcodes": [
                "641b06c0acceb593aac0a159"
            ],
            "url": "https://api.gsmtasks.com/tasks/c9becb24-31bf-4307-af4e-8f8666361787/",
            "account": "https://api.gsmtasks.com/accounts/040967e8-a52d-4436-80f0-77b153c783fa/",
            "state": "unassigned",
            "assignee": null,
            "order": "https://api.gsmtasks.com/orders/da7d838f-3179-42ae-a398-6258e62197e3/",
            "orderer_name": null,
            "route": null,
            "category": "assignment",
            "contact": {
                "name": "Splasheroo",
                "company": "Splasheroo Tech",
                "phones": [
                    "+44 7590 797200"
                ],
                "emails": [
                    "splasheroo.tech@gmail.com"
                ],
                "notes": "test notes"
            },
            "address": {
                "raw_address": "Leicester LE2 2FB, UK",
                "formatted_address": "61 Gartree Road Leicester Leicestershire",
                "location": {
                    "type": "Point",
                    "coordinates": [
                        -122.0312186,
                        37.33233141
                    ]
                },
                "google_place_id": "",
                "point_of_interest": "",
                "street": "",
                "house_number": "",
                "apartment_number": "",
                "city": "",
                "state": "",
                "postal_code": "le22fw",
                "country": "United Kingdom",
                "country_code": "UK",
                "geocoded_at": "2023-03-26T12:07:53.465280Z",
                "geocode_failed_at": null
            },
            "contact_address": null,
            "contact_address_external_id": null,
            "description": "Exterior & Interior",
            "complete_after": "2023-03-24T00:00:00Z",
            "complete_before": "2023-03-24T01:00:00Z",
            "scheduled_time": "2023-03-24T00:00:00Z",
            "completed_at": null,
            "cancelled_at": null,
            "auto_assign": false,
            "assignee_proximity": "away",
            "position": 127540897381.53271,
            "priority": 0,
            "duration": "00:59:00",
            "size": null,
            "forms": {},
            "documents": [],
            "signatures": [],
            "metafields": {},
            "trackers": [],
            "issues": [
                "task_over_complete_before"
            ],
            "counts": {
                "events": 3,
                "documents": 0,
                "signatures": 0,
                "forms": 0,
                "forms_completed": null
            },
            "actions": [
                "assign",
                "cancel"
            ],
            "created_at": "2023-03-23T11:17:19.769707Z",
            "updated_at": "2023-03-26T12:30:13.937120Z",
            "rider": {}
        },
        {
            "_id": "641b10ffacceb593aac0a1b8",
            "date": "2023-03-23T10:00:00.000Z",
            "startTime": "15:00",
            "endTime": "16:00",
            "car": {
                "_id": "641b072facceb593aac0a15e",
                "RegistrationPlate": "KM12AKK",
                "licence": true,
                "model": "SHARAN",
                "make": "VOLKSWAGEN",
                "coulor": "Grey",
                "customer": "641b06c0acceb593aac0a159",
                "__v": 0
            },
            "customer": {
                "location": {
                    "coordinates": []
                },
                "_id": "641b06c0acceb593aac0a159",
                "fullName": "asif hassam",
                "phone": "0632770232",
                "postCode": "Le2 2fw",
                "address": "66 Gartree Road     Leicester Leicestershire",
                "__v": 0
            },
            "service": {
                "_id": "641ac25a5ff9f0f660081962",
                "serviceName": "Exterior Only",
                "allService": [
                    "Exterior Bodywork",
                    "Exterior Glass",
                    "Exterior Trim",
                    "Alloys",
                    "Tyre Shine"
                ],
                "price": 20,
                "duration": "45:00",
                "__v": 0
            },
            "timestamp": "2023-03-22T11:47:04.797Z",
            "__v": 0,
            "paymentStatus": "completed",
            "id": "f8539995-e172-4935-bed9-893fa35e89c9",
            "external_id": "641b10ffacceb593aac0a1b8",
            "reference": "JFF20SX",
            "barcodes": [
                "641b06c0acceb593aac0a159"
            ],
            "url": "https://api.gsmtasks.com/tasks/f8539995-e172-4935-bed9-893fa35e89c9/",
            "account": "https://api.gsmtasks.com/accounts/040967e8-a52d-4436-80f0-77b153c783fa/",
            "state": "assigned",
            "assignee": "https://api.gsmtasks.com/users/091aed43-2c5e-477b-83a5-5fab3ebfe8fa/",
            "order": "https://api.gsmtasks.com/orders/4238c4ec-f3e9-4318-86ca-c32ca01b0f92/",
            "orderer_name": null,
            "route": null,
            "category": "assignment",
            "contact": {
                "name": "Splasheroo",
                "company": "Splasheroo Tech",
                "phones": [
                    "+243841550213"
                ],
                "emails": [
                    "splasheroo.tech@gmail.com"
                ],
                "notes": ""
            },
            "address": {
                "raw_address": "Gartree Road, Oadby, Leicester, UK",
                "formatted_address": "62 Gartree Road     Leicester Leicestershire",
                "location": {
                    "type": "Point",
                    "coordinates": [
                        -1.07213442738098,
                        52.62040933543196
                    ]
                },
                "google_place_id": "",
                "point_of_interest": "",
                "street": "",
                "house_number": "",
                "apartment_number": "",
                "city": "",
                "state": "",
                "postal_code": "Le2 2fw",
                "country": "United Kingdom",
                "country_code": "UK",
                "geocoded_at": "2023-03-22T14:30:25.214128Z",
                "geocode_failed_at": null
            },
            "contact_address": null,
            "contact_address_external_id": null,
            "description": "Exterior Only",
            "complete_after": "2023-03-22T14:30:24.873000Z",
            "complete_before": "2023-03-25T00:00:00Z",
            "scheduled_time": "2023-03-23T00:00:00Z",
            "completed_at": null,
            "cancelled_at": null,
            "auto_assign": false,
            "assignee_proximity": "away",
            "position": 127541066615.60872,
            "priority": 0,
            "duration": "00:00:59",
            "size": null,
            "forms": {},
            "documents": [],
            "signatures": [],
            "metafields": {},
            "trackers": [],
            "issues": [
                "task_over_complete_before"
            ],
            "counts": {
                "events": 2,
                "documents": 0,
                "signatures": 0,
                "forms": 0,
                "forms_completed": null
            },
            "actions": [
                "unassign",
                "accept",
                "reject",
                "transit",
                "activate",
                "complete",
                "fail",
                "cancel"
            ],
            "created_at": "2023-03-22T14:30:25.238989Z",
            "updated_at": "2023-03-26T12:30:10.091308Z",
            "rider": {
                "id": "091aed43-2c5e-477b-83a5-5fab3ebfe8fa",
                "url": "https://api.gsmtasks.com/users/091aed43-2c5e-477b-83a5-5fab3ebfe8fa/",
                "first_name": "",
                "last_name": "",
                "display_name": "wezalab@gmail.com",
                "email": "wezalab@gmail.com",
                "phone": "",
                "intercom_hash": "f55476d672a5f7f7f83cbacfe55efaf2e7f6cbd99780610e718aca581e20a830",
                "signature_image": null
            }
        }
    ]
}
```

This endpoint will fetch all bookings.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/booking/all`

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and all bookings
</aside>

## List bookings by Customer's ID

> Get all bookings  by Customer's ID saved in GSMTASKS, 

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/booking/all/:id",
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
    "msg": "Bookings fetched successfully",
    "fullTasks": [
        {
            "_id": "63f274a6a3e9d90470d1017d",
            "status": "waiting",
            "paymentStatus": "completed",
            "startTime": "10:00",
            "endTime": "11:00",
            "car": {
                "_id": "63e78cb1faf9b5d76acb6601",
                "RegistrationPlate": "KM12AKK",
                "licence": true,
                "model": "SHARAN",
                "make": "VOLKSWAGEN",
                "coulor": "Grey",
                "customer": "63e78c8efaf9b5d76acb65fc",
                "__v": 0
            },
            "customer": {
                "location": {
                    "coordinates": []
                },
                "_id": "63e78c8efaf9b5d76acb65fc",
                "fullName": "Kislaytest12",
                "phone": "32323232232",
                "postCode": "LE22FW",
                "address": "70 Gartree Road     Leicester Leicestershire",
                "__v": 0
            },
            "service": {
                "_id": "63e75fef580c7eb24880c99b",
                "serviceName": "Exterior & Interior",
                "allService": [
                    "Exterior Bodywork",
                    "Exterior Glass",
                    "Exterior Trim ",
                    "Alloys",
                    "Tyre Shine",
                    "Door Shuts",
                    "Interior Vacuum",
                    "Dashboard Wipe",
                    "Center Console Wiped",
                    "Anti-bacterial Treatment"
                ],
                "price": 25,
                "duration": 60,
                "contact": "+243841550213",
                "__v": 0
            },
            "timestamp": "2023-02-19T19:11:41.095Z",
            "__v": 0,
            "id": "ceeb1c7f-7c19-44c7-a795-7328dd47bc8d",
            "external_id": "63f274a6a3e9d90470d1017d",
            "reference": "YZNIGO2",
            "barcodes": [
                "63e78c8efaf9b5d76acb65fc"
            ],
            "url": "https://api.gsmtasks.com/tasks/ceeb1c7f-7c19-44c7-a795-7328dd47bc8d/",
            "account": "https://api.gsmtasks.com/accounts/040967e8-a52d-4436-80f0-77b153c783fa/",
            "state": "assigned",
            "assignee": "https://api.gsmtasks.com/users/091aed43-2c5e-477b-83a5-5fab3ebfe8fa/",
            "order": "https://api.gsmtasks.com/orders/72dfb9ec-0213-412d-ae98-34a0f4462ab3/",
            "orderer_name": null,
            "route": null,
            "category": "assignment",
            "contact": {
                "name": "Splasheroo",
                "company": "Splasheroo Tech",
                "phones": [
                    "+270000000000"
                ],
                "emails": [
                    "splasheroo.tech@gmail.com"
                ],
                "notes": "test notes"
            },
            "address": {
                "raw_address": "Gartree Road, Leicester LE2 2FW, UK",
                "formatted_address": "70 Gartree Road     Leicester Leicestershire",
                "location": {
                    "type": "Point",
                    "coordinates": [
                        -1.095587,
                        52.6166008
                    ]
                },
                "google_place_id": "",
                "point_of_interest": "",
                "street": "",
                "house_number": "",
                "apartment_number": "",
                "city": "",
                "state": "",
                "postal_code": "le22fw",
                "country": "United Kingdom",
                "country_code": "UK",
                "geocoded_at": "2023-02-19T21:12:39.310494+02:00",
                "geocode_failed_at": null
            },
            "contact_address": null,
            "contact_address_external_id": null,
            "description": "Exterior & Interior",
            "complete_after": "2023-02-19T21:12:39.329066+02:00",
            "complete_before": "2023-02-21T08:30:00+02:00",
            "scheduled_time": "2023-02-21T08:30:00+02:00",
            "completed_at": null,
            "cancelled_at": null,
            "auto_assign": false,
            "assignee_proximity": "away",
            "position": 1676875084.9021854,
            "priority": 0,
            "duration": "00:15:00",
            "size": null,
            "forms": {},
            "documents": [],
            "signatures": [],
            "metafields": {},
            "trackers": [],
            "issues": [],
            "counts": {
                "events": 2,
                "documents": 0,
                "signatures": 0,
                "forms": 0,
                "forms_completed": null
            },
            "actions": [
                "unassign",
                "accept",
                "reject",
                "transit",
                "activate",
                "complete",
                "fail",
                "cancel"
            ],
            "created_at": "2023-02-19T21:12:39.332812+02:00",
            "updated_at": "2023-02-20T08:38:37.622320+02:00"
      }
      {
        ....
      },
      {
        ....
      },
    ],
}
```

This endpoint will fetch all bookings.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/booking/all/:id`


### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string | Customer's id                                       |

<aside class="success">
Remember — if you get successfully, then you gonna receive a success message and bookings
</aside>

## List bookings by Date

> Get all bookings  by date saved in GSMTASKS, 

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/booking/all/date/:date",
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
// TODO : Check response
{
    "success": true,
    "msg": "Bookings for 01-01-2023 fetched successfullyy",
    "bookings": [
           
      {
        "_id": "63effb22bf34234d77e4591b",
        "status": "waiting",
        "paymentStatus": "waiting",
        "startTime": "10:00",
        "endTime": "11:00",
        "car": "63e0c60d62c9e9978212d600",
        "customer": "63e8b4ce428e36c929691f64",
        "service": "63e75fef580c7eb24880c99b",
        "timestamp": "2023-02-17T22:09:31.000Z",
        "__v": 0,
        "id": "a70c2561-bc9d-4a72-b6ef-3bbd36116d2a",
        "external_id": "63effb22bf34234d77e4591b",
        "reference": "3FINAL200",
        "barcodes": [
            "63e8b4ce428e36c929691f64"
        ],
        "url": "https://api.gsmtasks.com/tasks/a70c2561-bc9d-4a72-b6ef-3bbd36116d2a/",
        "account": "https://api.gsmtasks.com/accounts/040967e8-a52d-4436-80f0-77b153c783fa/",
        "state": "unassigned",
        "assignee": null,
        "order": "https://api.gsmtasks.com/orders/53c4b0d9-38bb-46c9-b94f-0c59f0a35443/",
        "orderer_name": null,
        "route": null,
        "category": "assignment",
        "contact": {
            "name": "Splasheroo",
            "company": "Splasheroo Tech",
            "phones": [
                "+270000000000"
            ],
            "emails": [
                "splasheroo.tech@gmail.com"
            ],
            "notes": "test notes"
        },
        "address": {
            "raw_address": "Leicester LE2 2FB, UK",
            "formatted_address": "60 Gartree Road  Leicester Leicestershire",
            "location": {
                "type": "Point",
                "coordinates": [
                    -122.0312186,
                    37.33233141
                ]
            },
            "google_place_id": "",
            "point_of_interest": "",
            "street": "",
            "house_number": "",
            "apartment_number": "",
            "city": "",
            "state": "",
            "postal_code": "le22fw",
            "country": "United Kingdom",
            "country_code": "UK",
            "geocoded_at": "2023-02-18T06:10:04.928463+08:00",
            "geocode_failed_at": null
        },
        "contact_address": null,
        "contact_address_external_id": null,
        "description": "Exterior & Interior",
        "complete_after": "2023-02-18T06:10:04.948296+08:00",
        "complete_before": "2023-02-21T14:30:00+08:00",
        "scheduled_time": "2023-02-21T14:30:00+08:00",
        "completed_at": null,
        "cancelled_at": null,
        "auto_assign": false,
        "assignee_proximity": "away",
        "position": 1676673811.74039,
        "priority": 0,
        "duration": "00:15:00",
        "size": null,
        "forms": {},
        "documents": [],
        "signatures": [],
        "metafields": {},
        "trackers": [],
        "issues": [],
        "counts": {
            "events": 1,
            "documents": 0,
            "signatures": 0,
            "forms": 0,
            "forms_completed": null
        },
        "actions": [
            "assign",
            "cancel"
        ],
        "created_at": "2023-02-18T06:10:04.951676+08:00",
        "updated_at": "2023-02-18T06:45:11.764140+08:00"
      },
      {
        "_id": "63effb3b15a01bf0413ef89e",
        "status": "waiting",
        "paymentStatus": "waiting",
        "startTime": "10:00",
        "endTime": "11:00",
        "car": "63e0c60d62c9e9978212d600",
        "customer": "63e8b4ce428e36c929691f64",
        "service": "63e75fef580c7eb24880c99b",
        "timestamp": "2023-02-17T22:09:56.106Z",
        "__v": 0,
        "id": "7800bee0-26e0-4580-92da-40dd68a4cc80",
        "external_id": "63effb3b15a01bf0413ef89e",
        "reference": "FINAL",
        "barcodes": [
            "63eff825b329fe071caeff33"
        ],
        "url": "https://api.gsmtasks.com/tasks/7800bee0-26e0-4580-92da-40dd68a4cc80/",
        "account": "https://api.gsmtasks.com/accounts/040967e8-a52d-4436-80f0-77b153c783fa/",
        "state": "unassigned",
        "assignee": null,
        "order": "https://api.gsmtasks.com/orders/ffa81cca-bc08-4d22-bf1e-4b37199c5f4b/",
        "orderer_name": null,
        "route": null,
        "category": "assignment",
        "contact": {
            "name": "Splasheroo",
            "company": "Splasheroo Tech",
            "phones": [
                "+270000000000"
            ],
            "emails": [
                "splasheroo.tech@gmail.com"
            ],
            "notes": "test notes"
        },
        "address": {
            "raw_address": "Leicester LE2 2FB, UK",
            "formatted_address": "60 Gartree Road  Leicester Leicestershire",
            "location": {
                "type": "Point",
                "coordinates": [
                    37.33233141,
                    -122.0312186
                ]
            },
            "google_place_id": "",
            "point_of_interest": "",
            "street": "",
            "house_number": "",
            "apartment_number": "",
            "city": "",
            "state": "",
            "postal_code": "le22fw",
            "country": "United Kingdom",
            "country_code": "UK",
            "geocoded_at": "2023-02-18T05:56:55.573377+08:00",
            "geocode_failed_at": null
        },
        "contact_address": null,
        "contact_address_external_id": null,
        "description": "Exterior & Interior",
        "complete_after": "2023-02-18T05:56:55.590444+08:00",
        "complete_before": "2023-02-21T14:30:00+08:00",
        "scheduled_time": "2023-02-21T14:30:00+08:00",
        "completed_at": null,
        "cancelled_at": null,
        "auto_assign": false,
        "assignee_proximity": "away",
        "position": 1676673711.74039,
        "priority": 0,
        "duration": "00:15:00",
        "size": null,
        "forms": {},
        "documents": [],
        "signatures": [],
        "metafields": {},
        "trackers": [],
        "issues": [],
        "counts": {
            "events": 1,
            "documents": 0,
            "signatures": 0,
            "forms": 0,
            "forms_completed": null
        },
        "actions": [
            "assign",
            "cancel"
        ],
        "created_at": "2023-02-18T05:56:55.594066+08:00",
        "updated_at": "2023-02-18T06:45:11.763096+08:00"
      }
    ],
}
```

This endpoint will fetch bookings.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/booking/all/date/:date`


### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| date                  | date   | Date in this format: YYYYMMDD                       |

<aside class="success">
Remember — if you get successfully, then you gonna receive a success message and bookings
</aside>


## Get latest Booking

> Get latest booking  by Customer's ID saved in GSMTASKS, 

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/booking/latest/:id",
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
    "msg": "Bookings fetched successfully",
    "fullTasks": {
            "_id": "63f274a6a3e9d90470d1017d",
            "status": "waiting",
            "paymentStatus": "completed",
            "startTime": "10:00",
            "endTime": "11:00",
            "car": {
                "_id": "63e78cb1faf9b5d76acb6601",
                "RegistrationPlate": "KM12AKK",
                "licence": true,
                "model": "SHARAN",
                "make": "VOLKSWAGEN",
                "coulor": "Grey",
                "customer": "63e78c8efaf9b5d76acb65fc",
                "__v": 0
            },
            "customer": {
                "location": {
                    "coordinates": []
                },
                "_id": "63e78c8efaf9b5d76acb65fc",
                "fullName": "Kislaytest12",
                "phone": "32323232232",
                "postCode": "LE22FW",
                "address": "70 Gartree Road     Leicester Leicestershire",
                "__v": 0
            },
            "service": {
                "_id": "63e75fef580c7eb24880c99b",
                "serviceName": "Exterior & Interior",
                "allService": [
                    "Exterior Bodywork",
                    "Exterior Glass",
                    "Exterior Trim ",
                    "Alloys",
                    "Tyre Shine",
                    "Door Shuts",
                    "Interior Vacuum",
                    "Dashboard Wipe",
                    "Center Console Wiped",
                    "Anti-bacterial Treatment"
                ],
                "price": 25,
                "duration": 60,
                "contact": "+243841550213",
                "__v": 0
            },
            "timestamp": "2023-02-19T19:11:41.095Z",
            "__v": 0,
            "id": "ceeb1c7f-7c19-44c7-a795-7328dd47bc8d",
            "external_id": "63f274a6a3e9d90470d1017d",
            "reference": "YZNIGO2",
            "barcodes": [
                "63e78c8efaf9b5d76acb65fc"
            ],
            "url": "https://api.gsmtasks.com/tasks/ceeb1c7f-7c19-44c7-a795-7328dd47bc8d/",
            "account": "https://api.gsmtasks.com/accounts/040967e8-a52d-4436-80f0-77b153c783fa/",
            "state": "assigned",
            "assignee": "https://api.gsmtasks.com/users/091aed43-2c5e-477b-83a5-5fab3ebfe8fa/",
            "order": "https://api.gsmtasks.com/orders/72dfb9ec-0213-412d-ae98-34a0f4462ab3/",
            "orderer_name": null,
            "route": null,
            "category": "assignment",
            "contact": {
                "name": "Splasheroo",
                "company": "Splasheroo Tech",
                "phones": [
                    "+270000000000"
                ],
                "emails": [
                    "splasheroo.tech@gmail.com"
                ],
                "notes": "test notes"
            },
            "address": {
                "raw_address": "Gartree Road, Leicester LE2 2FW, UK",
                "formatted_address": "70 Gartree Road     Leicester Leicestershire",
                "location": {
                    "type": "Point",
                    "coordinates": [
                        -1.095587,
                        52.6166008
                    ]
                },
                "google_place_id": "",
                "point_of_interest": "",
                "street": "",
                "house_number": "",
                "apartment_number": "",
                "city": "",
                "state": "",
                "postal_code": "le22fw",
                "country": "United Kingdom",
                "country_code": "UK",
                "geocoded_at": "2023-02-19T21:12:39.310494+02:00",
                "geocode_failed_at": null
            },
            "contact_address": null,
            "contact_address_external_id": null,
            "description": "Exterior & Interior",
            "complete_after": "2023-02-19T21:12:39.329066+02:00",
            "complete_before": "2023-02-21T08:30:00+02:00",
            "scheduled_time": "2023-02-21T08:30:00+02:00",
            "completed_at": null,
            "cancelled_at": null,
            "auto_assign": false,
            "assignee_proximity": "away",
            "position": 1676875084.9021854,
            "priority": 0,
            "duration": "00:15:00",
            "size": null,
            "forms": {},
            "documents": [],
            "signatures": [],
            "metafields": {},
            "trackers": [],
            "issues": [],
            "counts": {
                "events": 2,
                "documents": 0,
                "signatures": 0,
                "forms": 0,
                "forms_completed": null
            },
            "actions": [
                "unassign",
                "accept",
                "reject",
                "transit",
                "activate",
                "complete",
                "fail",
                "cancel"
            ],
            "created_at": "2023-02-19T21:12:39.332812+02:00",
            "updated_at": "2023-02-20T08:38:37.622320+02:00"
      },
}
```

This endpoint will fetch all bookings.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/booking/latest/:id`


### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string | Customer's id                                       |

<aside class="success">
Remember — if you get successfully, then you gonna receive a success message and bookings
</aside>

## Assign a Booking to a Rider

> Assign a Booking to a Rider, 

```javascript
import axios from "axios";

const options = {
  method: "PUT",
  url: "https://splasheroo-backend.herokuapp.com/api/booking/assignBookingToRider",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    bookingId :"63efd9d0caf0aa67a2647164",
    riderId: "7d354534sd54f5s5sdfhrt5tye",
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
    "msg": "Assign Booking successfully!"
}
```

This endpoint will change `paymentStatus` from `Waiting` to `Complete`, 

### HTTP Request

`PUT https://splasheroo-backend.herokuapp.com/api/booking/assignBookingToRider`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| bookingId             | string | id                                                  |
| riderId               | string | id                                                  |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>


## Route Optimization

> Route Optimization

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/booking/optimizeRoute",
  params: {},
  headers: {
    "content-type": "application/json",
  },
 
  data: {
    ridersUrl: ["https://api.gsmtasks.com/users/5789286c-aa73-474e-9990-da9f337c33f4/", "https://api.gsmtasks.com/users/7158ea76-772a-47e6-96f0-8c8f50be0f4b/"],
    date:"20230317"
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
    "msg": "Route Optimized successfully",
    "booking": {
        "id": "04859518-aa99-464b-acfd-5a3c930f626b",
        "url": "https://api.gsmtasks.com/route_optimizations/04859518-aa99-464b-acfd-5a3c930f626b/",
        "account": "https://api.gsmtasks.com/accounts/040967e8-a52d-4436-80f0-77b153c783fa/",
        "assignees": [
            "https://api.gsmtasks.com/users/5789286c-aa73-474e-9990-da9f337c33f4/",
            "https://api.gsmtasks.com/users/7158ea76-772a-47e6-96f0-8c8f50be0f4b/"
        ],
        "state": "pending",
        "objective": "completion_time",
        "tasks": [
            "https://api.gsmtasks.com/tasks/05d49d2e-c695-4630-bb2a-d74491c6a4b0/",
            "https://api.gsmtasks.com/tasks/1ee85438-bce7-4075-b31e-66571229a51d/",
            "https://api.gsmtasks.com/tasks/3aa1858b-13dd-4461-b4be-ff8e789aeb60/",
            "https://api.gsmtasks.com/tasks/3ecde4af-9a38-4ed1-bcbd-e19c8759b495/"
        ],
        "start_time": "2023-03-17T00:00:00Z",
        "unassign_not_optimal": false,
        "total_distance": null,
        "total_duration": null,
        "commit": true,
        "created_by": "https://api.gsmtasks.com/users/eb6ca015-37de-461b-be78-c564f7b6fded/",
        "commited_at": null,
        "scheduled_at": null,
        "started_at": null,
        "ready_at": null,
        "completed_at": null,
        "failed_at": null,
        "created_at": "2023-03-17T09:38:08.750302Z",
        "updated_at": "2023-03-17T09:38:08.750326Z",
        "errors": null,
        "start_location": {
            "type": "Point",
            "coordinates": [
                -1.095587,
                52.6166008
            ]
        },
        "end_location": {
            "type": "Point",
            "coordinates": [
                -1.095587,
                52.6166008
            ]
        }
    }
}
```

This endpoint will optimize Route

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/booking/optimizeRoute`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| date                  | date   |   YYYYMMDD FORMAT                                   |
| ridersUrl             | array  |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>

# Payment

Payment management
 
## Charge a Customer

> Charge a Customer and pay throught Stripe, 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/payment/charge",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    amount: 20, 
    id_customer: "63e78c8efaf9b5d76acb65fc", 
    id_service: "63e75fef580c7eb24880c99b",
    stripe_customer_id: "cus_NVBsV1zqydvc5H"
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
    "msg": "Payment passed successfully",
    "charge": {
        "id": "ch_3MkC5yDSebOil4xL0WG3da4c",
        "object": "charge",
        "amount": 2000,
        "amount_captured": 2000,
        "amount_refunded": 0,
        "application": null,
        "application_fee": null,
        "application_fee_amount": null,
        "balance_transaction": "txn_3MkC5yDSebOil4xL0VEZnqga",
        "billing_details": {
            "address": {
                "city": null,
                "country": null,
                "line1": null,
                "line2": null,
                "postal_code": null,
                "state": null
            },
            "email": null,
            "name": null,
            "phone": null
        },
        "calculated_statement_descriptor": "Stripe",
        "captured": true,
        "created": 1678478358,
        "currency": "usd",
        "customer": "cus_NVBsV1zqydvc5H",
        "description": "Exterior & Interior",
        "destination": null,
        "dispute": null,
        "disputed": false,
        "failure_balance_transaction": null,
        "failure_code": null,
        "failure_message": null,
        "fraud_details": {},
        "invoice": null,
        "livemode": false,
        "metadata": {},
        "on_behalf_of": null,
        "order": null,
        "outcome": {
            "network_status": "approved_by_network",
            "reason": null,
            "risk_level": "normal",
            "risk_score": 32,
            "seller_message": "Payment complete.",
            "type": "authorized"
        },
        "paid": true,
        "payment_intent": null,
        "payment_method": "card_1MkBUXDSebOil4xLAK52JKDK",
        "payment_method_details": {
            "card": {
                "brand": "visa",
                "checks": {
                    "address_line1_check": null,
                    "address_postal_code_check": null,
                    "cvc_check": null
                },
                "country": "US",
                "exp_month": 2,
                "exp_year": 2024,
                "fingerprint": "OoEiI0DZsnhWNuF8",
                "funding": "credit",
                "installments": null,
                "last4": "4242",
                "mandate": null,
                "network": "visa",
                "three_d_secure": null,
                "wallet": null
            },
            "type": "card"
        },
        "receipt_email": null,
        "receipt_number": null,
        "receipt_url": "https://pay.stripe.com/receipts/payment/CAcaFwoVYWNjdF8xTVpNYkpEU2ViT2lsNHhMKJeYrqAGMgaA1W0RuTY6LBaifTQiTBpgeeepTUFh65ljFIy9DROoLiSDIEHb8sli0USy7MUoreA5sPDP",
        "refunded": false,
        "review": null,
        "shipping": null,
        "source": {
            "id": "card_1MkBUXDSebOil4xLAK52JKDK",
            "object": "card",
            "address_city": null,
            "address_country": null,
            "address_line1": null,
            "address_line1_check": null,
            "address_line2": null,
            "address_state": null,
            "address_zip": null,
            "address_zip_check": null,
            "brand": "Visa",
            "country": "US",
            "customer": "cus_NVBsV1zqydvc5H",
            "cvc_check": null,
            "dynamic_last4": null,
            "exp_month": 2,
            "exp_year": 2024,
            "fingerprint": "OoEiI0DZsnhWNuF8",
            "funding": "credit",
            "last4": "4242",
            "metadata": {},
            "name": null,
            "tokenization_method": null
        },
        "source_transfer": null,
        "statement_descriptor": null,
        "statement_descriptor_suffix": null,
        "status": "succeeded",
        "transfer_data": null,
        "transfer_group": null
    }
}
```

This endpoint will charge A customer.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/payment/charge`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id_customer           | string | id                                                  |
| id_service            | string | id                                                  |
| amount                | number |                                                     |
| stripe_customer_id    | number |  you can get it from bankCard's table               |


<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>

# Slot

Slot management

##  Get Slots availability

> To obtain a slot availability by date

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/slot/getSlotsAvailability/:date",
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
<!-- TODO : CHECK FOR RESPONSE -->
```json
{
    "success": true,
    "msg": "Successfully ",
}
```

This endpoint list available slots by a given date.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/slot/getSlotsAvailability/:date`

<aside class="warning">
  This endpoint list available slots by a given date.
</aside>

## Edit individual Bookings per Hour

> Edit individual Bookings per Hour for given date

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/slot/editBookingsPerHourForEachSlotOfDate",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    date: "20230303"
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
    "msg": "Edited individual Bookings per Hour successfully for given date"
}
```

This endpoint will edit individual Bookings per Hour successfully for given date

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/slot/editBookingsPerHourForEachSlotOfDate`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| date                  | date   | finding the slots of the given date                 |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>

# Operation

Operation management

## Update Operations 

> Update Operations

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/operation/updateOperations",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  // TODO : TO BE DEFINED
  data: {
    isDefault: "",
    bookingsPerSlot: "",
    startTime: "",
    endTime: "",
    updateOnlyDefault: "",
    startDate: "20230101",
    endDate: "20230101",
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
    "msg": "Operation completed successfully"
}
```

This endpoint will update Operations

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/operation/updateOperations`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| date                  | date   |                                                     |
| isDefault             | BOOL   |                                                     |
| bookingsPerSlot       | NUMBER |                                                     |
| startTime             | STRING |                                                     |
| endTime               | STRING |                                                     |
| updateOnlyDefault     | BOOL   |                                                     |
| startDate             | date   |                                                     |
| endDate               | date   |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>

# GSM task

The GSMtasks API is a RESTful web service for developers to programmatically interact with GSMtasks data, real-time delivery and task management and route optimization functionality.

## Authentication

> To obtain a authentication token the fallowing HTTP request has to be performed.

```javascript
import axios from "axios";

const options = {
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/booking/authGsmtask",
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
    "msg": "Successfully authentified",
    "gsmuser": {
        "token": "f69d6f61840fb92efc24b0267abb47***********",
        "user": "https://api.gsmtasks.com/users/eb6ca015-37de-461b-be78-************/",
        "accounts": [
            "040967e8-a52d-4436-80f0-**************"
        ],
        "account": "040967e8-a52d-4436-80f0-**************"
    }
}
```

This endpoint will authentificate the user.

### HTTP Request

`GET https://splasheroo-backend.herokuapp.com/api/authGsmtask`

<aside class="success">
Remember — this is the token  <code>"token": "f69d6f61840fb92efc24b0267abb47***********" </code>,
</aside>

<aside class="warning">
The tokens are valid forever, unless refreshed by the user himself.
</aside>
