Test Case ID: TC_API_012  
Title: Get All Orders

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: GET /orders  
URL: https://simple-grocery-store-api.glitch.me/orders  
Method: GET

Scenario:  
Get the list of all orders by using a cartId and a customer name.

Body (optional depending on API behavior):
- cartId: {{cartId}}  
- customerName: {{$randomFullName}}

Steps:  
1. Use a valid cartId and customer name  
2. Make a GET request to /orders  
3. Click Send  
4. Check if the status code is 200

Expected Result:  
- Status code is 200 OK  
- A list of orders is returned (can be filtered or full list)

Postman Test Code:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

Status: Pass
