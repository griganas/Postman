Test Case ID: TC_API_011  
Title: Create an Order

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: POST /orders  
URL: https://simple-grocery-store-api.glitch.me/orders  
Method: POST

Scenario:  
Create an order using a valid cartId and customer name. The API should return a new orderId.

Body:
- cartId: {{cartId}} (from previous test)
- customerName: {{$randomFullName}}

Steps:  
1. Use a valid cartId and a random name  
2. Make a POST request to /orders  
3. Check if the status code is 201  
4. Check if the response confirms creation  
5. Save the orderId to collection variables

Expected Result:  
- Status code is 201 Created  
- Response confirms order creation (created: true)  
- Response includes orderId (string)  
- orderId is saved for future use

Postman Test Code:
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});
pm.test('Order was created', () => {
    const response = pm.response.json();
    pm.expect(response).to.be.an('object');
    pm.expect(response.created).to.be.true;
    pm.expect(response.orderId).to.be.a('string');     
    pm.collectionVariables.set('orderId', response.orderId);
});

Status: Pass
