# [008] Add random movie № 1 to the List
# [009] Add random movie № 2 to the List
# [010] Add random movie № 3 to the List
___

Now we have three similar steps, we need change only __[media_ad]__ which is __{{movie#Id}}__, which we created in previous step. POST request in which we add movies to the List.

![image](https://user-images.githubusercontent.com/122685448/231020758-7a683dad-0e2e-4975-9990-0399af3b00be.png)

__Use below path:__

```
list/:list_id/add_item?api_key={{apiKey}}&session_id={{sessionId}}&media_id={{movie1Id}}
```

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, __{{movie#Id}}__ and in Path __{{listId}}__, without body request.

__Test code below:__

```
pm.test("Status code is 201 - OK", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();

pm.test("The Movie № " + pm.globals.replaceIn("{{movie1Id}}") + " has been added to the list № " + pm.globals.replaceIn("{{listId}}"), function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 201. In addition checking that movie added to the list.

So after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231020777-1205e2e7-62b6-4a7d-b0ba-5554ed022756.png)

__And test response:__

![image](https://user-images.githubusercontent.com/122685448/231020785-abf16360-4819-4085-9ff2-d2e6e4d54b3c.png)
 
We need to do the same two more times, change only movie variable from __{{movie1Id}}__ -> __{{movie2Id}}__ -> __{{movie3Id}}__.


