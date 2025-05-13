Test Case ID: TC_API_010  
Title: Register New API Client

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: POST /api-clients  
URL: https://simple-grocery-store-api.glitch.me/api-clients  
Method: POST

Scenario:  
Register a new API client using random name and email. After registration, we get an access token that we will use in the next requests.

Pre-request:
A random email is created using the current timestamp and saved in collection variables.

Request Body:
- clientName: {{$randomFullName}}
- clientEmail: {{randomEmail}} (generated dynamically)
- password: 123456

Steps:  
1. Run the pre-request script to create a random email  
2. Make a POST request to /api-clients  
3. Check if the status code is 201  
4. Check if the response includes an access token  
5. Save the accessToken in collection variables

Expected Result:  
- Status code is 201 Created  
- The response includes accessToken  
- Token is saved for future use

Pre-request Script:
let timestamp = Date.now();  
let randomEmail = `testuser_${timestamp}@example.com`;  
pm.collectionVariables.set("randomEmail", randomEmail);  

Postman Test Code:
-Pre-request Script:
let timestamp = Date.now();  
let randomEmail = `testuser_${timestamp}@example.com`;  
pm.collectionVariables.set("randomEmail", randomEmail);  
-Post-response:
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});  
const response = pm.response.json();  
pm.collectionVariables.set('AccessToken', response.accessToken);

Status: Pass
