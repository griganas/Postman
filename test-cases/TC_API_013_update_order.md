Test Case ID: TC_API_013  
Title: Update Order (customer name and comment)

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: PATCH /orders/:orderId  
URL: https://simple-grocery-store-api.glitch.me/orders/{{orderId}}  
Method: PATCH

Scenario:  
Update the customer's name and comment for an existing order.

Body:
- customerName: Mark Grig  
- comment: I will get it from the store

Steps:  
1. Use a valid orderId from a previous request  
2. Make a PATCH request to /orders/:orderId  
3. Set the body with updated values for name and comment  
4. Click Send  
5. Check that the status code is 204

Expected Result:  
- Status code should be 204 No Content  
- No response body is expected  
- The order is updated successfully

Postman Test Code:
pm.test("Status code is 204", function () {
    pm.response.to.have.status(204);
});

Status: Pass
