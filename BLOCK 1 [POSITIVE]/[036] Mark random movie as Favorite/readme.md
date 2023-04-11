# [036] Mark random movie as Favorite
___

In this POST request, we mark random movie to add to system Favorite list.

__Use below path:__
```
account/:account_id/favorite?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231298053-bbf4a120-1230-441b-aae3-d54ea9b95168.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__, and body request:
```js {.line-numbers}
{
  "media_type": "movie",
  "media_id": {{movie6Id}},
  "favorite": true
}
```

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 201 - OK", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();

pm.test("Movie № " + pm.globals.replaceIn("{{movie6Id}}") + " added to Favorie", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```
In above code we are checking:

Response of status code must be 201, checking that exactly random movie added to system Favorite list.

Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231298070-7ca24a2e-1b55-46a5-94f1-75e3e29dc3c3.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231298077-d0a82a46-1f91-47db-a6de-795b6a152b01.png)

