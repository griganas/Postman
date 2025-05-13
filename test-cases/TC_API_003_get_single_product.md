Test Case ID: TC_API_003  
Title: Get Single Product by ID

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: GET /products/:productId  
URL: https://simple-grocery-store-api.glitch.me/products/{{productId}}  
Method: GET

Scenario:  
Get one product using a valid productId and check that the response contains correct product details.

Steps:  
1. Use the saved productId from a previous request  
2. Make a GET request to /products/:productId  
3. Click Send  
4. Check that the status code is 200  
5. Check that the response is an object  
6. Check that the id matches the requested productId  
7. Check that the product has a name (string), price (positive number), and is in stock

Expected Result:  
- Status code is 200 OK  
- The response is an object  
- The productId matches  
- Name is a string  
- Price is a number > 0  
- Product is in stock

Postman Test Code:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
const response = pm.response.json();
pm.test("Response is an object", () => {   
    pm.expect(response).to.be.an("object");
});
pm.test("Correct product was retrieved", () => {
    const requestedProductId = pm.collectionVariables.get('productId');
    pm.expect(response.id).to.eql(requestedProductId);
});
pm.test("Product name", () => {
    pm.expect(response.name).to.be.a('string');
});
pm.test("Product price", () => {
    pm.expect(response.price).to.be.a('number');
    pm.expect(response.price).to.be.above(0);
});
pm.test("Product is in stock", () => {
    pm.expect(response.inStock).to.be.true;
});

Status: Pass
