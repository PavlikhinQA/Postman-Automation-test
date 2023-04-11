# [018] Check that list deleted
___

This step is the same as __[012]__, __[014]__ and __[016]__. Now need to know if list deleted or not. 

__Use below path:__
```
list/:list_id?api_key={{apiKey}}
```
![image](https://user-images.githubusercontent.com/122685448/231021558-0ac341d3-9870-46f4-ad00-9a57f1324e5e.png)

In Query Params we need __{{apiKey}}__, and in Path __{{listId}}__.

__Test code below:__
```
pm.test("Status code is 404 - There is no list № " + pm.globals.replaceIn("{{listId}}") , function () {
    pm.response.to.have.status(404);
});

const response = pm.response.json();

pm.test("Check - list deleted", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 404 – that mean that there is no such list on the server and checking that the list deleted.
So after pushing Send, we receive body response:
![image](https://user-images.githubusercontent.com/122685448/231021588-971bbe8a-b22c-4d90-aa31-29f8199e1a5c.png)
 
So here, response telling us that system cannot find requested list.

__And test response:__
 
![image](https://user-images.githubusercontent.com/122685448/231021601-0df4760a-fa39-4112-9dfb-3b8efc6eaa10.png)

___So if we will return to previous step where we found BUG – we understand that system complete our request, but response is wrong.___

