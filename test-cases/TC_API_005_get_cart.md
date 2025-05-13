Test Case ID: TC_API_005  
Title: Get Cart by ID

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: GET /carts/:cartId  
URL: https://simple-grocery-store-api.glitch.me/carts/{{cartId}}  
Method: GET

Scenario:  
Use an existing cartId to check if the cart can be retrieved successfully.

Steps:  
1. Use a saved cartId from a previous request  
2. Make a GET request to /carts/:cartId  
3. Click Send  
4. Check that the status code is 200

Expected Result:  
- Status code should be 200 OK  
- The cart is returned successfully

Postman Test Code:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

Status: Pass
