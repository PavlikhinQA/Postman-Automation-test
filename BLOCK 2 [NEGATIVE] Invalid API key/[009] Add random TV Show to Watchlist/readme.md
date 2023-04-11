# [009] Add random TV Show to Watchlist
___
In this __POST__ request, we want to add random movie to system Whatchlist.

__Use below path:__
```
account/:account_id/watchlist?api_key=1234567890&session_id={{sessionId}}
```
///***

In Query Params we need __{{apiKey}}(fake)__, __{{sessionId}}__, in Path __{{accountId}}__, and bode request:
```
{
  "media_type": "tv",
  "media_id": {{tvShow}},
  "watchlist": true
}
```

__Test code below:__
```
pm.test("Status code is 401 - OK", function () {
    pm.response.to.have.status(401);
});

const response = pm.response.json();

pm.test("The system does not allow add TV Show due to Invalid API key", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 401, and checking if system allow to add any TV Shows without correct apiKey to system Watchlist.


Body response:

///***

Test response:

///***
