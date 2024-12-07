# Restful-Booker-API-Testing-In-Postman
Restful-booker is an API that can use to learn more about API Testing or try out API testing tools against. Restful-booker is a Create Get Update Delete Web API that comes with authentication features and loaded with a bunch of bugs .


This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API. 

### **Features**

- Tests for GET, POST, PUT, DELETE requests
- Collection of tests covering different API endpoints
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

## API Documentation:
- https://documenter.getpostman.com/view/39629746/2sAYBaBANF
  
### **Technology used:**
- Postman
- Newman

### **Prerequisite:**
- Node Js
- Newman
- Newman Html Report Library

### **Installation**

1. Postman: If you haven't already, [download and install Postman. (https://www.postman.com/downloads/)
2. Clone the repository:
 ```console 
  git clone https://github.com/29safia/Restful-Booker-API-Testing-In-Postman.git
```
3. Import the Postman collection:
    - Open Postman.
    - Click on the Import button.
    - Select the file from the repository.
4. Import the Postman environment:
    - In Postman, click on the gear icon in the top right corner.
    - Select **Import** and choose the file.
5. Newman and Report Installation Process:
    - Newman Install Command:
     ```console 
      npm install -g newman
    ```
    - Newman Html Report Install Command:
     ```console 
      npm install -g newman-reporter-htmlextra
    ```
### **Usage**
1. Select Environment:
    -   In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
3. Run Collection:
    -   Select the imported collection from the Collections sidebar.
    -   Click on the Runner button to open the collection runner.
    -   Select the desired environment.
    -   Click Start Test to run the collection.
8. View Results:
    -   Once the tests are complete, view the results in the Runner tab.
    -   Detailed test results can be viewed for each request.

## **Testing**

## Test Case Scenarios:

## _**1. Create Booking**_

### Request URL: https://restful-booker.herokuapp.com/booking/
### Request Method: POST
### Pre-request Script:
```console 
    //firstname

       var firstName = pm.variables.replaceIn("{{$randomFirstName}}")
       console.log(firstName)
       pm.environment.set("firstName", firstName)

   //lastname

     var lastName = pm.variables.replaceIn("{{$randomLastName}}")
     console.log(lastName)
     pm.environment.set("lastName", lastName)

  // checkin
     const moment = require('moment')

  // Set today's date and format 

       const today = moment()
       var checkin = today.add(1, 'y').format("YYYY-MM-DD") 
       console.log("Check-in Date:", checkin)
       pm.environment.set("checkin", checkin)

 // checkout

      const checkout = moment(checkin).add(7, 'days').format("YYYY-MM-DD")
      pm.environment.set("checkout", checkout)
      console.log("Check-out Date:", checkout)

 //total price

     var totalprice = pm.variables.replaceIn("{{$randomInt}}")
     console.log(totalprice)
     pm.environment.set("totalprice", totalprice)

 //deposite 

    var depositpaid = pm.variables.replaceIn("{{$randomBoolean}}")
    pm.environment.set("depositpaid", depositpaid)
    console.log("Deposit-Paid", depositpaid)

 //need
    var needs = pm.variables.replaceIn("{{$randomProduct}}")
    console.log(needs)
    pm.environment.set("needs",needs)
```
  **Response Body:**
 ```console 
{
    "firstname": "Verona",
    "lastname": "Sipes",
    "totalprice": 796,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2025-12-07",
        "checkout": "2025-12-14"
    },
    "additionalneeds": "Pizza"
}```
 ## _**2. Get Booking **_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: GET
### Response Body:
 ```console 
{
    "firstname": "Verona",
    "lastname": "Sipes",
    "totalprice": 796,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2025-12-07",
        "checkout": "2025-12-14"
    },
    "additionalneeds": "Pizza"
}
```
## _**3. Create A Token For Authentication.**_
### Request URL: https://restful-booker.herokuapp.com/auth
### Request Method: POST
### Pre-request Script: None
### Request Body:
 ```console 
{
	"username": "admin",
	"password": "password123"
}
```
  **Response Body:**
 ```console 
{
    "token": "3ee096687a1d34d"
}
```

 ## _**4. Update Booking **_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: PUT
### Pre-request Script:
```console 
//firstname
var updated_firstName = pm.variables.replaceIn("{{$randomFirstName}}")
console.log(updated_firstName)
pm.environment.set("updated_firstName", updated_firstName)

//lastname
var updated_lastName = pm.variables.replaceIn("{{$randomLastName}}")
console.log(updated_lastName)
pm.environment.set("updated_lastName", updated_lastName)

// checkin
const moment = require('moment')

// Set today's date and format 
const today = moment()
var updated_checkin = today.add(1, 'y').format("YYYY-MM-DD") 
console.log("Check-in Date:", updated_checkin)
pm.environment.set("updated_checkin", updated_checkin)

// checkout
const updated_checkout = moment(updated_checkin).add(7, 'days').format("YYYY-MM-DD")
pm.environment.set("updated_checkout", updated_checkout)
console.log("Check-out Date:", updated_checkout)

//total price
var updated_totalprice = pm.variables.replaceIn("{{$randomInt}}")
console.log(updated_totalprice)
pm.environment.set("updated_totalprice", updated_totalprice)

//deposite 
var updated_depositpaid = pm.variables.replaceIn("{{$randomBoolean}}")
pm.environment.set("updated_depositpaid", updated_depositpaid)
console.log("Deposit-Paid", updated_depositpaid)

//need
var updated_needs = pm.variables.replaceIn("{{$randomProduct}}")
console.log(updated_needs)
pm.environment.set("updated_needs",updated_needs)
```
  **Request Body:** 
 ```console 
  {
	  "firstname" : "{{firstName}}",
	  "lastname" : "{{lastName}}",
	  "totalprice" : {{totalPrice}},
	  "depositpaid" : {{depositPaid}},
	  "bookingdates" : {
    	  "checkin" : "{{checkin}}",
    	  "checkout" : "{{checkout}}"
	  },
	  "additionalneeds" : "{{additionalNeeds}}"
  }
```
  **Response Body:**
 ```console 
{
    "firstname": "Kieran",
    "lastname": "Lynch",
    "totalprice": 974,
    "depositpaid": false,
    "bookingdates": {
        "checkin": "2025-12-07",
        "checkout": "2025-12-14"
    },
    "additionalneeds": "Ball"
}
```

 ## _**5. Delete Booking Record**_

### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: DELETE
### Response Body: None 

## Run Command:  
- Run Command for Console: 
```console 
newman run postman_collection.json -e postman_environment.json 
```
- Run Command for Report: 
```console 
newman run postman_collection.json -e postman_environment.json -r htmlextra
```

## Newman Report Summary:
file:///E:/SQA%20Note/API%20Export/APIproject1-2024-12-06-13-41-47-704-0.html
