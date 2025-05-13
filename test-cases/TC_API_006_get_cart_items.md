Test Case ID: TC_API_006  
Title: Get Items from Cart

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: GET /carts/:cartId/items  
URL: https://simple-grocery-store-api.glitch.me/carts/{{cartId}}/items  
Method: GET

Scenario:  
Check if we can get the list of products that have been added to a specific cart.

Steps:  
1. Use an existing cartId  
2. Make a GET request to /carts/:cartId/items  
3. Click Send  
4. Check the response status

Expected Result:  
- Status code should be 200 OK  
- The list of items in the cart is returned (can be empty or contain products)

Postman Test Code:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
Status: Pass
