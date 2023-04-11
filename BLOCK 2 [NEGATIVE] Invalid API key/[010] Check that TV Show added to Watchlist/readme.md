# [010] Check that TV Show added to Watchlist
___

In this __GET__ request, we want to check if TV Show added to system Whatchlist. 

__Use below path:__
```
account/:account_id/watchlist/tv?api_key=1234567890&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231306274-b007e9dc-d9b3-46c6-95fc-407b9f51a168.png)
In Query Params we need __{{apiKey}}(fake)__, __{{sessionId}}__ and in Path __{{accountId}}__

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 401 - OK", function () {
    pm.response.to.have.status(401);
});

const response = pm.response.json();

pm.test("The system does not allow check TV Show due to Invalid API key", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 401, and checking if system allow adding TV Show to system Watchlist.

Body response:
![image](https://user-images.githubusercontent.com/122685448/231306298-87290681-f3b4-43e1-9e37-0a01a4d97f38.png)

Test response:
![image](https://user-images.githubusercontent.com/122685448/231306312-82aa0142-61a2-4350-91c6-808ddfcfa99e.png)
 

