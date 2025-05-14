Test Case ID: TC_API_017  
Title: Create Order without Authentication

Collection: Simple Grocery Store API  
Folder: Negative Paths → Missing Authentication  
Request: POST /orders  
URL: https://simple-grocery-store-api.glitch.me/orders  
Method: POST

Scenario:  
Try to create an order without sending an authorization token.

Body:
- cartId = {{cartId}}
- customerName = {{$randomFullName}}

Steps:  
1. Do not include Authorization header  
2. Make a POST request to /orders  
3. Send the body with cartId and customerName  
4. Click Send  
5. Check status code and error message

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
