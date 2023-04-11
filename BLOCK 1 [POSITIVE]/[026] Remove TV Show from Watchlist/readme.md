# [026] Remove TV Show from Watchlist
___

In this POST request, we are removing exactly first random TV Show from the system Watchlist.

__Use below path:__
```
account/:account_id/watchlist?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231022235-f526c9d3-fb9d-4da1-9cd4-b9139b472c29.png)
In Query Params we need __{{apiKey}}__, __{{sessionId}}__, in the Path __{{account_id}}__, and in body request:
```
{
  "media_type": "tv",
  "media_id": {{tv1Id}},
  "watchlist": false
}
```

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("TV Show № " + pm.globals.replaceIn("{{tv1Id}}") + " removed from Watch", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 200, and checking that exactly first TV Show added in system Whatchlist.

Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231022253-4a8780fb-c23e-4d0e-bbd5-bb540915d6ab.png)
__And test response:__
 
![image](https://user-images.githubusercontent.com/122685448/231022262-172dd3e8-a301-42be-b165-a8e63f790098.png)
