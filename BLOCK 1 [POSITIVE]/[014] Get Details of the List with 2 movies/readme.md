# [014] Get Details of the List with 2 movies
___

This step is equal as __[012]__ step, but we need check that in the list only 2 movies.

__Use below path:__
```
list/:list_id?api_key={{apiKey}}
```
![image](https://user-images.githubusercontent.com/122685448/231021086-e5baae54-a01c-4c5e-a8e4-621a5dbc4e9d.png)

In Query Params we need __{{apiKey}}__ and in Path __{{listId}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("There are only two Movie in the List № " + pm.globals.replaceIn("{{listId}}"), function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.id).to.eql(pm.globals.replaceIn("{{listId}}"));
    pm.expect(jsonData.item_count).to.eql(2);
});
```

In above code we are checking:

Response of status code must be 200. In addition checking that in List the items.

So after pushing Send, we receive body response:
![image](https://user-images.githubusercontent.com/122685448/231021103-119dad1d-772d-448d-b987-ae684020ced9.png)

And test response:
 
![image](https://user-images.githubusercontent.com/122685448/231021111-d90bab85-da14-42af-8d08-ebbbb8900508.png)


