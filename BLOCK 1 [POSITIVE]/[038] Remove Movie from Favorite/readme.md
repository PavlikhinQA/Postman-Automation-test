# [038] Remove Movie from Favorite
___

In this POST request, we remove exactly random movie from system Favorite list.

__Use below path:__
```
account/:account_id/favorite?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231298265-ffd5f8ce-1f29-4dc4-9b23-d7d97f382b41.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, in the Path __{{account_id}}__, and body request:
```
{
  "media_type": "movie",
  "media_id": {{movie6Id}},
  "favorite": false
}
```

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("Movie № " + pm.globals.replaceIn("{{movie6Id}}") + " removed from Favorie", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 200, checking that exactly random movie removed from system Favorite list.

Therefore, after pushing Send, we receive body response:
 
![image](https://user-images.githubusercontent.com/122685448/231298285-6450ffe8-cb4d-4da4-b7cd-1b51233159c5.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231298293-20f84aec-386c-44f3-9ef9-ad788ef222c2.png)

