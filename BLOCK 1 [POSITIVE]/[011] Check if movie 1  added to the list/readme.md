# [011] Check if movie 1 added to the list
___

Now we will send GET request to check if exactly movie # 1 added into the list.

__Use below path:__
```
list/:list_id/item_status?api_key={{apiKey}}&movie_id={{movie1Id}}
```
![image](https://user-images.githubusercontent.com/122685448/231020838-f7d2e06b-cbd7-4b62-a8f0-dde52d6f0f4b.png)

In Query Params we need __{{apiKey}}__, __{{movie#Id}}__ and in Path __{{listId}}__

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("The Movie № " + pm.globals.replaceIn("{{movie1Id}}") + " has been added to the list № " + pm.globals.replaceIn("{{listId}}"), function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.item_present).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 200. In addition checking that {{movie1Id}} added to the list.

So after pushing Send, we receive body response:
 
![image](https://user-images.githubusercontent.com/122685448/231020857-1802ff30-24f0-4991-a8be-7dcaba272025.png)

And test response:
![image](https://user-images.githubusercontent.com/122685448/231020867-3671dabf-40d3-41c8-ae8b-d320d20cac2e.png)

