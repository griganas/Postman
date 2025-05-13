Test Case ID: TC_API_009  
Title: Replace Product in Cart

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: PUT /carts/:cartId/items/:itemId  
URL: https://simple-grocery-store-api.glitch.me/carts/{{cartId}}/items/{{lastItemId}}  
Method: PUT

Scenario:  
Replace an item in the cart with a different product and quantity.

Path Variables:
- cartId = {{cartId}}  
- itemId = {{lastItemId}}

Body:
{
  "productId": 4643,
  "quantity": 2
}

Steps:  
1. Use a valid cartId and itemId  
2. Make a PUT request with the new productId and quantity  
3. Click Send  
4. Check the response status

Expected Result:  
- Status code should be 204 No Content  
- No response body is expected  
- The item is replaced with the new product

Postman Test Code:
pm.test("Status code is 204", function () {
    pm.response.to.have.status(204);
});
Status: Pass
