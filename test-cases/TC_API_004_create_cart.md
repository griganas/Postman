Test Case ID: TC_API_004  
Title: Create New Cart

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: POST /carts  
URL: https://simple-grocery-store-api.glitch.me/carts  
Method: POST

Scenario:  
Send a POST request to create a new shopping cart. The response should return a cartId.

Steps:  
1. Make a POST request to /carts  
2. Click Send  
3. Check the response status  
4. Check that the response is an object  
5. Check that it contains a cartId (string)  
6. Save the cartId to collection variables

Expected Result:  
- Status code should be 201 Created  
- The response should contain a valid cartId (string)  
- The cartId is saved for later use

Postman Test Code:
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});
pm.test('Response has valid cartId', () => {
    const response = pm.response.json();
    pm.expect(response).to.be.an('object');
    pm.expect(response).to.haveOwnProperty('cartId');
    pm.expect(response.cartId).to.be.a('string');
    pm.collectionVariables.set('cartId', response.cartId);
});

Status: Pass
