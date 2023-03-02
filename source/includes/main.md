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
    type: "",
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
| type                  | string |                                                     |
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
  method: "GET",
  url: "https://splasheroo-backend.herokuapp.com/api/rider/find/:id",
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
  // TODO : Change Response
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

`GET https://splasheroo-backend.herokuapp.com/api/rider/find/:id`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string |                                                     |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and a rider ojbect
</aside>


## Activate Rider

> Activation of a Rider 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/rider/activate",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    id: "a432as4d3a2sf453fh4y5asd"
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
    "msg": "Rider activated successfully!"
}
```

This endpoint will add a BankCard.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/rider/activate`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string | Rider's ID                                          |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>



## Deactivate Rider

> Activation of a Rider 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/rider/deactivate",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    id: "a432as4d3a2sf453fh4y55sd"
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
    "msg": "Rider deactivated successfully!"
}
```

This endpoint will add a BankCard.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/rider/deactivate`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string | Rider's ID                                          |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
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
    "msg": "BankCard added successfuly!"
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
    "last4": "4242",
    "brand": "Visa"
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
    vechile:"63e0c60d62c9e9978212d600"
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
    "msg": "Booking added successfuly!",
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
| userId                | id     |                                                     |
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
| service               | string |   id                                                |
| startTime             | string |                                                     |
| vechile               | string |  id                                                 |

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

> Get all bookings saved in GSMTASKS, 

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
    id_customer: "63e8b4ce428e36c929691f64",
    amount: 35.5,
    id_service: "63e75fef580c7eb24880c99b"
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
    "msg": "Payment added successfuly!"
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
