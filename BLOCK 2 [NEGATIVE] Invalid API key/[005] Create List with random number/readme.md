# [005] Create List with random number
___

In this __POST__ request, we want to create with random number for name of list and create description for it.

__Use below path:__
```
list?api_key=1234567890&session_id={{sessionId}}&name={{listName}}&description={{listDescription}}
```
![image](https://user-images.githubusercontent.com/122685448/231305668-bfac990b-2847-436a-8740-1bab1df2a20d.png)

In Query Params we need __{{apiKey}}(fake)__, __{{session_id}}__ (= null), __{{listName}}__ and __{{listDescription}}__.

For __{{listName}}__ and __{{listDescription}}__ we will create variables in __Pre-req.__:

```js {.line-numbers}
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
```js {.line-numbers}
pm.test("Status code is 401 - OK", function () {
    pm.response.to.have.status(401);
});

const response = pm.response.json();

pm.test("List has not been created", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 401, and checking that list not created.

Body response:

![image](https://user-images.githubusercontent.com/122685448/231305689-3453f9c3-a14a-4e5d-96ae-f9bdfbd01d10.png)

Test response:

![image](https://user-images.githubusercontent.com/122685448/231305697-ca298f06-6a00-40fc-98a3-655eec32580b.png)

In addition, because of this __{{listId}}__ not created in variables.

