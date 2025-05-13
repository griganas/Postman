Test Case ID: TC_API_015  
Title: Get Single Order (Order Not Found)

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: GET /orders/:orderId  
URL: https://simple-grocery-store-api.glitch.me/orders/{{orderId}}  
Method: GET

Scenario:  
Try to get a single order using an orderId that does not exist (for example, after deleting it).

Path Variables:
- orderId = {{orderId}}

Steps:  
1. Use an orderId that does not exist anymore (e.g. already deleted)  
2. Make a GET request to /orders/:orderId  
3. Click Send  
4. Check the response status  
5. Check if the error message is correct and includes the orderId

Expected Result:  
- Status code is 404 Not Found  
- The response contains an "error" field  
- The message includes the orderId we tried to access

Postman Test Code:
pm.test("Status code is 404", function () {
    pm.response.to.have.status(404);
});
pm.test("Error message", () => {
    const response = pm.response.json();
    pm.expect(response).to.haveOwnProperty("error");
    pm.expect(response.error).to.contain(pm.collectionVariables.get('orderId'));
});

Status: Pass
