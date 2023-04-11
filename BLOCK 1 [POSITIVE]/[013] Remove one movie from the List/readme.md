# [013] Remove one movie from the List
___

In this step we will sent POST request to remove one movie from the list.

__Use below path:__
```
list/:list_id/remove_item?api_key={{apiKey}}&session_id={{sessionId}}&media_id={{movie1Id}}
```
![image](https://user-images.githubusercontent.com/122685448/231021015-fb0b7825-a2ca-43fa-a66c-3f773876bf5e.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, __{{movie1Id}}__ and in Path __{{listId}}__ without body request.

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("The Movie № " + pm.globals.replaceIn("{{movie1Id}}") + " has been removed from list № " + pm.globals.replaceIn("{{listId}}"), function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 200 and check if movie was delited.

So after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231021028-f8c8c3f2-b399-4be0-9af0-f0371f426482.png)

__And test response:__
 
![image](https://user-images.githubusercontent.com/122685448/231021034-4ebc58c3-545c-43b5-8ac1-9f9e62f03462.png)


