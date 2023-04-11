# [016] Get Details of the List - empty list

This step is the same as __[012]__ and __[014]__. We must look inside of List and don’t find any movies. 

__Use below path:__
```
list/:list_id?api_key={{apiKey}}
``` 
![image](https://user-images.githubusercontent.com/122685448/231021334-9f17501f-badb-4c6d-be3c-e22fcbb4c258.png)

In Query Params we need __{{apiKey}}__, and in Path __{{listId}}__.

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("There are no movies in the List № " + pm.globals.replaceIn("{{listId}}"), function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.id).to.eql(pm.globals.replaceIn("{{listId}}"));
    pm.expect(jsonData.item_count).to.eql(0);
});
```

In above code we are checking:

Response of status code must be 200 and checking that the list is empty.

So after pushing Send, we receive body response:
 
![image](https://user-images.githubusercontent.com/122685448/231021347-5ac8160e-6841-41db-ab71-f8c5a6317e3c.png)

__And test response:__
 
![image](https://user-images.githubusercontent.com/122685448/231021351-e0d99529-acba-4b7a-8f86-18b13eff1e91.png)


