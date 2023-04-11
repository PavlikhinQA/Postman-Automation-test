# [012] Get Details of the List with 3 movies
___

Now we will send GET request to get details what is inside of the list.

__Use below path:__
```
list/:list_id?api_key={{apiKey}}
```
![image](https://user-images.githubusercontent.com/122685448/231020917-7a395904-43ac-4b2e-b241-b0f23ee650ba.png)

In Query Params we need __{{apiKey}}__, and in Path __{{listId}}__

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("In the list № " + pm.globals.replaceIn("{{listId}}") + " has been added 3 Movies", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.id).to.eql(pm.globals.replaceIn("{{listId}}"));
    pm.expect(jsonData.item_count).to.eql(3);
});
```

In above code we are checking:

Response of status code must be 200. In addition checking that in List the items.

So after pushing __Send__, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231020931-f4e8a8c7-4dad-4445-b3b6-a124fb1c4edc.png)
![image](https://user-images.githubusercontent.com/122685448/231020944-e3678bc0-f6c4-4f9d-aeb1-a842caf9c006.png)
 
__And test response:__
 
![image](https://user-images.githubusercontent.com/122685448/231020957-b3a5cdc0-2abd-42d8-9663-a9495402af15.png)


