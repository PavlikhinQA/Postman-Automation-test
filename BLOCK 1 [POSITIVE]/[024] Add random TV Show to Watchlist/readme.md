# [024] Add random TV Show to Watchlist
___

In this POST request, we add first random TV Show to the system Watchlist.

__Use below path:__
```
account/:account_id/watchlist?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231022028-bb9857b1-aed0-48ec-ba33-e007a0688678.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, in the Path __{{account_id}}__ and in bode request:
```js {.line-numbers}
{
  "media_type": "tv",
  "media_id": {{tv1Id}},
  "watchlist": true
}
```

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 201 - OK", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();

pm.test("TV Show № " + pm.globals.replaceIn("{{tv1Id}}") + " added to Watch", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 201, and checking that exactly first TV Show added in system Whatchlist.

Therefore, after pushing Send, we receive body response:
![image](https://user-images.githubusercontent.com/122685448/231022057-4efda14d-5f55-4fb0-a44c-959fbd51c0ff.png)
__And test response:__
 
![image](https://user-images.githubusercontent.com/122685448/231022065-a0d76032-a284-4efe-83b7-5c1e939f4d2b.png)

