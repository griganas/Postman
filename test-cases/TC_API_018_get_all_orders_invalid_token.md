Test Case ID: TC_API_018  
Title: Get All Orders with Invalid Token

Collection: Simple Grocery Store API  
Folder: Negative Paths → Invalid Authentication  
Request: GET /orders  
URL: https://simple-grocery-store-api.glitch.me/orders  
Method: GET

Scenario:  
Try to get all orders using an invalid bearer token.

Body:
- cartId = {{cartId}}
- customerNam = {{$randomFullName}}

Steps:  
1. Set an invalid Authorization header (e.g. Bearer wrong.token)  
2. Make a GET request to /orders  
3. Include the body with cartId and customerName  
4. Click Send  
5. Check the response code and error message

Expected Result:  
- Status code is 401 Unauthorized  
- Error message is: "Invalid bearer token."

Postman Test Code:
pm.test("Status code is 401", () => {
    pm.response.to.have.status(401);
});
pm.test("Error message", () => {
    const response = pm.response.json();
    pm.expect(response.error).to.eql("Invalid bearer token.");
});

Status: Pass
