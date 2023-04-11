# [005] Create List with random number
___

In this step we POST request to create a list, with which we will work in future steps.

__Use below path:__
```
/list?api_key={{apiKey}}&session_id={{sessionId}}&name={{listName}}&description={{listDescription}}
```

Regarding documentation, we need add body for this request, but also we can add it in Query Params.

![image](https://user-images.githubusercontent.com/122685448/231020454-54462aec-ef4b-4c9a-b299-f8ed066ce49c.png)
 
__{{ApiKey}}__ and __{{SessionId}}__ we already know, but additional two Query Params are new:

We need create name of list and description, I decided to use __pre-request__ and create random number and create description, using function in __JS__. For each of them I created variable.
```
let  numberForList = parseInt(Math.random() * 10000);

function getListName() {
    const listName = "New list № " + numberForList;
    console.log(listName);
    return listName;
};

function getDescription() {
    const listDescription = "I created description for the list № " + numberForList;
    console.log(listDescription);
    return listDescription;
}

pm.environment.set("listName",getListName());
pm.environment.set("listDescription",getDescription());
```

__Test code below:__
```
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();
pm.globals.set("listId", response.list_id);

pm.test("List has been created", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 201. In addition, check that if list created.

![image](https://user-images.githubusercontent.com/122685448/231020484-90c9b627-667e-4f37-85c6-e31b284c93c7.png)
![image](https://user-images.githubusercontent.com/122685448/231020497-cd7eb9dc-9e36-4067-a1b6-c70e3fcd2a43.png)
 
So added additional variable:

![image](https://user-images.githubusercontent.com/122685448/231020506-fe741a36-c6c7-4b77-9879-a01970838692.png)
