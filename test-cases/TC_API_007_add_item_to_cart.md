Test Case ID: TC_API_007  
Title: Add Item to Cart

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: POST /carts/:cartId/items  
URL: https://simple-grocery-store-api.glitch.me/carts/{{cartId}}/items  
Method: POST

Scenario:  
Add a product to the cart using a valid productId and quantity.

Body:
{
  "productId": {{productId}},
  "quantity": 1
}

Steps:  
1. Use a valid cartId and productId  
2. Make a POST request to /carts/:cartId/items with the above body  
3. Click Send  
4. Check the response status  
5. Verify that the item was created  
6. Save the itemId to collection variables

Expected Result:  
- Status code should be 201 Created  
- The response should confirm that the item was created  
- The response should include itemId  
- itemId is saved for future use

Postman Test Code:
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});
pm.test('Item was created', () => {
    const response = pm.response.json();
    pm.expect(response).to.be.an('object');
    pm.expect(response.created).to.be.true;
    pm.expect(response.itemId).to.be.a('number');
    pm.collectionVariables.set('lastAddedItemId', response.itemId);
});

Status: Pass
