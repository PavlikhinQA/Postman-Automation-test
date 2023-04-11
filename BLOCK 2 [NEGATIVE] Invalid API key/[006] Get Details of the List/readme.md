# [006] Get Details of the List
___

In this __GET__ request, we want to check if list created or not.

__Use below path:__
```
list/:list_id?api_key=1234567890
```
///***

In Query Params we need __{{apiKey}}(fake)__, and in Path __{{listId}}__

__Test code below:__
```
pm.test("Status code is 401 - OK", function () {
    pm.response.to.have.status(401);
});

const response = pm.response.json();

pm.test("The system does not allow searching List due to Invalid API key", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 401, and checking if system allow to search any list without correct __apiKey__.

Body response:
///***

Test response:
 
///***