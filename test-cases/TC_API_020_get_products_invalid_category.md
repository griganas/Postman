Test Case ID: TC_API_020  
Title: Get Products with Invalid Category

Collection: Simple Grocery Store API  
Folder: Negative Paths → Invalid Inputs  
Request: GET /products?category=invalid-category  
URL: https://simple-grocery-store-api.glitch.me/products?category=invalid-category  
Method: GET

Scenario:  
Try to filter products by using an invalid category name in the query parameters.

Query Parameters:
- category = invalid-category

Steps:  
1. Make a GET request to /products with query param category=invalid-category  
2. Click Send  
3. Check if the response status is 400  
4. Verify the error message

Expected Result:  
- Status code is 400 Bad Request  
- Error message contains: "Invalid value for query parameter 'category'."

Postman Test Code:
pm.test("Status code is 400", function () {
    pm.response.to.have.status(400);
});
pm.test("Error message", () => {
    const response = pm.response.json();
    pm.expect(response.error).to.contain("Invalid value for query parameter 'category'.");
});

Status: Pass
