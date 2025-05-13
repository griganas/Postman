Test Case ID: TC_API_014  
Title: Delete Order

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: DELETE /orders/:orderId  
URL: https://simple-grocery-store-api.glitch.me/orders/{{orderId}}  
Method: DELETE

Scenario:  
Delete an existing order using its orderId.

Path Variables:
- orderId = {{orderId}}

Steps:  
1. Use a valid orderId from a previous request  
2. Make a DELETE request to /orders/:orderId  
3. Click Send  
4. Check that the response status is 204

Expected Result:  
- Status code is 204 No Content  
- No response body is expected  
- The order is deleted successfully

Postman Test Code:
pm.test("Status code is 204", function () {
    pm.response.to.have.status(204);
});

Status: Pass
