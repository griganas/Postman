Test Case ID: TC_API_001  
Title: Check if API is working (GET /status)

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: GET /status  
URL: https://simple-grocery-store-api.glitch.me/status  
Method: GET

Scenario:  
Send a GET request to /status to check if the API is online.

Steps:  
1. Open Postman  
2. Make a GET request to /status  
3. Click Send  

Expected Result:  
- Status code should be 200 OK  
- The API is up and running

Postman Test Code:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

Status: Pass
