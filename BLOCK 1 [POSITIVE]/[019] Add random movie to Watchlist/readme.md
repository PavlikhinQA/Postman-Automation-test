# [019] Add random movie to Watchlist
___

In this POST request we will add random movie(4) to system Whatchlist.

__Use below path:__
```
account/:account_id/watchlist?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231021675-55f879c9-e215-4fcf-b0aa-b68137e5c471.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__ and in Path __{{account_id}}__ and we will need a body:

```
{
  "media_type": "movie",
  "media_id": {{movie4Id}},
  "watchlist": true
}
```

__Test code below:__
```
pm.test("Status code is 201 - OK", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();

pm.test("Movie № " + pm.globals.replaceIn("{{movie4Id}}") + " added to Watch", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 201 and checking that the movie added to the system Whatchlist.

Therefore, after pushing Send, we receive body response:
![image](https://user-images.githubusercontent.com/122685448/231021692-9219dad0-be67-43c9-a053-c24012954f22.png)
__And test response:__
![image](https://user-images.githubusercontent.com/122685448/231021705-4a6b0ae7-a5f3-4b3d-b792-fc085e6a73b9.png)

