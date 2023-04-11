# [040] Mark random TV Show as Favorite
___

In this POST request, we mark random TV Show to add to system Favorite list.

__Use below path:__
```
account/:account_id/favorite?api_key={{apiKey}}&session_id={{sessionId}}
```
///***
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
///***
 
In addition, test response:
///***

