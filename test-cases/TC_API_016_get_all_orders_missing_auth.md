Test Case ID: TC_API_016  
Title: Get All Orders without Authentication

Collection: Simple Grocery Store API  
Folder: Negative Paths → Missing Authentication  
Request: GET /orders  
URL: https://simple-grocery-store-api.glitch.me/orders  
Method: GET

Scenario:  
Try to get all orders without sending an authorization token.

Body:
- cartId = {{cartId}},
- customerName = {{$randomFullName}}

Steps:  
1. Remove Authorization header  
2. Make a GET request to /orders  
3. Include the body with cartId and customerName  
4. Click Send  
5. Check the response status and message

Expected Result:  
- Status code is 401 Unauthorized  
- Error message is: "Missing Authorization header."

Postman Test Code:
pm.test("Status code is 401",  () => {
    pm.response.to.have.status(401);
});
pm.test("Error message", () => {
    const response = pm.response.json();
    pm.expect(response.error).to.eql("Missing Authorization header.");
});

Status: Pass
