# [042] Remove TV Show from Favorite
___

In this POST request, we remove exactly random TV Show from system Favorite list.

__Use below path:__
```
account/:account_id/favorite?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231299927-b5e8261a-af94-4d37-8f35-057133b7a0cb.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, in the Path __{{account_id}}__, and body request:
```
{
  "media_type": "tv",
  "media_id": {{tv3Id}},
  "favorite": false
}
```

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("TV Show № " + pm.globals.replaceIn("{{tv3Id}}") + " removed from Favorie", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```
In above code we are checking:

Response of status code must be 200, checking that exactly random TV Show removed from system Favorite list.

Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231299993-6ba3cb59-bd22-4e28-a8e0-42c740beec21.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231300028-3cd84734-8b63-48e2-abbd-f58ad648e5ce.png)
