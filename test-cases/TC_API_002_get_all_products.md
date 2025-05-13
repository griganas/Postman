Test Case ID: TC_API_002  
Title: Get All Products

Collection: Simple Grocery Store API  
Folder: Positive Paths  
Request: GET /products  
URL: https://simple-grocery-store-api.glitch.me/products  
Method: GET

Scenario:  
Check if we can get a list of products and at least one product is available in stock.

Steps:  
1. Open Postman  
2. Make a GET request to /products  
3. Click Send  
4. Check if the status is 200  
5. Check if the response is an array  
6. Make sure at least one product exists  
7. Check if the first product has a valid ID and is in stock  
8. Save the productId for later use

Expected Result:  
- Status code should be 200 OK  
- Response should be an array  
- At least one product exists  
- The product should have an ID and be in stock  
- Variable "productId" is saved

Postman Test Code:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test('At least one available product exists', () => {
    const response = pm.response.json();
   pm.expect(response).to.be.an('array');
    pm.expect(response.length).to.be.above(0);
    const product = response[0];
    pm.expect(product).to.be.an('object');
    pm.expect(product).to.haveOwnProperty('id');
    pm.expect(product.id).to.be.a('number');
    pm.expect(product).to.haveOwnProperty('inStock');
    pm.expect(product.inStock).to.be.true;   
    pm.collectionVariables.set('productId', product.id);
});

Status: Pass
