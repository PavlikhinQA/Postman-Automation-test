# [006] Get Details of the List
___

In this step, we will use GET request to check details of created list.

__Use below path:__
```
list/:list_id?api_key={{apiKey}}
```

We need use __{{apiKey}}__ in Query Params and __{{listId}}__, which created in previous step in Path.

![image](https://user-images.githubusercontent.com/122685448/231020561-275b2e19-5c21-4ff8-a893-4d86e61cfcbb.png)

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("List № " + pm.globals.replaceIn("{{listId}}") + " has been checked", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.id).to.eql(pm.globals.replaceIn("{{listId}}"));
});
```

In above code we are checking:

Response of status code must be 200. In addition, check that if list created.
In body of response we can see name of List, description and id of list.
![image](https://user-images.githubusercontent.com/122685448/231020580-e818e054-fcba-446f-9b47-79cbf2522d97.png)
![image](https://user-images.githubusercontent.com/122685448/231020591-2702b81f-c82d-4dc3-aba3-95a2d80838c2.png)
 
 
