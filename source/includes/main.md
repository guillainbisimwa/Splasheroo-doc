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


# Car Wash Service

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


# Riders

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

# Banking Card

Bank Card management

## Add a Bank CARD

> Post a bankCard and save in our database, 


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
    cardNumber: "123456789123", 
    cardHolderName: "Nicolas Brody", 
    expiryDate: "12/25", 
    cvvCvc: "12/12", 
    customer: "63db5cf616391c961dc3a4e5"
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
| customer              | number | ID of an existing customer                             |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>


## Get single Bankcard

> Get a single bankCard by it customer's ID, 

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/bankCard/find",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    customer: "63db5cf616391c961dc3a4e5"
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
    "msg": "bankCard found",
    "bankCard": [
        {
            "_id": "63e022086852fc4fee6bb40a",
            "cardNumber": "123456789123",
            "cardHolderName": "Nicolas Brody",
            "expiryDate": "2001-12-24T22:00:00.000Z",
            "cvvCvc": "12/12",
            "verified": false,
            "customer": "63db5cf616391c961dc3a4e5",
            "__v": 0
        }
    ]
}
```

This endpoint will fecth a single bankCard.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/bankCard/find`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| customer              | string | Existing Customer's ID                              |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and a bankCard ojbect
</aside>


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

> Get a single promo Code by it customer's ID, 

```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/promoCode/find",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    id: "63e0269a2efe25d61bfbda03"
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

`POST https://splasheroo-backend.herokuapp.com/api/promoCode/find`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| id                    | string | Existing promoCode's ID                             |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message and a promoCode ojbect
</aside>


# Booking

Booking management

## Add a Booking

> Post a booking and save in our database, 


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
    date: "2023-03-01T12:00:59", 
    ref: "C10000002", 
    contact: "+24389897544", 
    notes: "This car needs attention when clining left tyers", 
    slot_start_time: "2023-03-01T12:00:59", 
    slot_end_time: "2023-03-01T13:00:59", 
    location: "10 Downing street", 
    car: "63dcde4dfb6a27a947f255a1",
    service: "63e014aa4969108cb5bc1797",
    driver: "63e01b1d747fbe40578423db"
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
    "msg": "Booking added successfuly!"
}
```

This endpoint will add a Booking.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/booking/add`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| date                  | string |                                                     |
| ref                   | number |                                                     |
| contact               | string |                                                     |
| notes                 | string |                                                     |
| slot_start_time       | string |  in this format: YYYY-mm-ddTHH:MM:ss                |
| slot_end_time         | string |  in this format: YYYY-mm-ddTHH:MM:ss                |
| location              | string |                                                     |
| car                   | string |  id                                                 |
| service               | string |  id                                                 |
| driver                | string |  id                                                 |
| promoCode?            | string |  id (optional)                                      |

<aside class="success">
Remember — if you post successfully, then you gonna receive a success message
</aside>


## Get all bookings

> Get all bookings saved in our database, 

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
    "msg": "Booking fetched successfully",
    "bookings": [
        {
            "_id": "63e02d66276302955b62e222",
            "date": "2023-02-05T22:27:43.550Z",
            "status": "waiting",
            "ref": "C10000002",
            "contact": "+24389897544",
            "notes": "This car needs attention when clining left tyers",
            "slot_start_time": "2023-03-01T10:00:59.000Z",
            "slot_end_time": "2023-03-01T11:00:59.000Z",
            "location": "10 Downing street",
            "jobCompleted": false,
            "car": "63dcde4dfb6a27a947f255a1",
            "service": "63e014aa4969108cb5bc1797",
            "driver": "63e01b1d747fbe40578423db",
            "timestamp": "2023-02-05T22:27:43.550Z",
            "__v": 0
        },
        {
            "_id": "63e030ab1e50a3131769ade5",
            "date": "2023-03-01T11:00:59.000Z",
            "status": "waiting",
            "ref": "AB0000100",
            "contact": "+24389897544",
            "notes": "Don't forget to clean glasses",
            "slot_start_time": "2023-03-01T11:00:59.000Z",
            "slot_end_time": "2023-03-01T11:45:59.000Z",
            "location": "10 Downing street",
            "jobCompleted": false,
            "car": "63dfb03bd18638890433cadf",
            "service": "63e00d434969108cb5bc1794",
            "driver": "63e01b1d747fbe40578423db",
            "timestamp": "2023-02-05T22:41:38.605Z",
            "__v": 0
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


# Payment

Payment management

## Add a Payment

> Post a Payment and save in our database, 


```javascript
import axios from "axios";

const options = {
  method: "POST",
  url: "https://splasheroo-backend.herokuapp.com/api/payment/add",
  params: {},
  headers: {
    "content-type": "application/json",
  },
  data: {
    bankCard: "4680945nge93ff67", 
    booking: "43570934750935034"
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

This endpoint will add a promoCode.

### HTTP Request

`POST https://splasheroo-backend.herokuapp.com/api/payment/add`

### Query Parameters

| Parameter             | Type   | Description                                         |
| --------------------- | ------ | --------------------------------------------------- |
| bankCard              | string | id                                                  |
| booking               | number | id                                                  |

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
