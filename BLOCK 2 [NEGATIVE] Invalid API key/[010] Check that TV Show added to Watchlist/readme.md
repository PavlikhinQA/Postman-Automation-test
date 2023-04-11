# [010] Check that TV Show added to Watchlist
___

In this __GET__ request, we want to check if TV Show added to system Whatchlist. 

__Use below path:__
```
account/:account_id/watchlist/tv?api_key=1234567890&session_id={{sessionId}}
```
///***
In Query Params we need __{{apiKey}}(fake)__, __{{sessionId}}__ and in Path __{{accountId}}__

__Test code below:__
```
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
///***
Test response:
///***
 

