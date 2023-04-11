# [040] Mark random TV Show as Favorite
___

In this POST request, we mark random TV Show to add to system Favorite list.

__Use below path:__
```
account/:account_id/favorite?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231298925-b662b252-4245-4f6f-99bc-31d34aef33a1.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__, and body request:
```
{
  "media_type": "tv",
  "media_id": {{tv3Id}},
  "favorite": true
}
```

__Test code below:__
```
pm.test("Status code is 201 - OK", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();

pm.test("TV Show № " + pm.globals.replaceIn("{{tv3Id}}") + " added to Favorie", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```
In above code we are checking:

Response of status code must be 201, checking that exactly random TV Show added to system Favorite list.

Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231298993-be213ab9-1a99-4bad-8a9e-207e475645dc.png)
 
__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231299096-81e3e7f4-9aef-4918-b8d5-3ea684094595.png)

