Test Case ID: TC_API_008  
Title: Update Item Quantity in Cart

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: PATCH /carts/:cartId/items/:itemId  
URL: https://simple-grocery-store-api.glitch.me/carts/{{cartId}}/items/{{lastAddedItem}}  
Method: PATCH

Scenario:  
Change the quantity of a specific item in the cart.

Path Variables:
- cartId = {{cartId}}  
- itemId = {{lastAddedItem}}

Body:
{
  "quantity": 2
}

Steps:  
1. Use a valid cartId and itemId  
2. Make a PATCH request to update the quantity to 2  
3. Click Send  
4. Check the response status

Expected Result:  
- Status code should be 204 No Content  
- No body is expected

Postman Test Code:
pm.test("Status code is 204", function () {
    pm.response.to.have.status(204);
});

Status: Pass
