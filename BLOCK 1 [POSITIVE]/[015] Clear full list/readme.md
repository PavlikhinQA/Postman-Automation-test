# [015] Clear full list
___

In this step lest clear/remove all items from the list

__Use below path:__
```
list/:list_id/clear?api_key={{apiKey}}&session_id={{sessionId}}&confirm=true
```
![image](https://user-images.githubusercontent.com/122685448/231021178-f5c5250c-de31-4174-8656-37d16ec92af1.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, confirmation and in Path __{{listId}}__ without body request.

__Test code below:__
```
pm.test("Status code is 201 - OK", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();

pm.test("List № " + pm.globals.replaceIn("{{listId}}") + " has been cleaned", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 201. In addition checking that in the list removed all items.

So after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231021217-1fab0aeb-1f8b-4e80-b0d6-97d11384a3cd.png)

__And test response:__
![image](https://user-images.githubusercontent.com/122685448/231021224-ef1b10f8-e069-44fc-896e-83751bcca84d.png)



