# [009] Add random TV Show to Watchlist
___
In this __POST__ request, we want to add random movie to system Whatchlist.

__Use below path:__
```
account/:account_id/watchlist?api_key=1234567890&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231306185-02d10247-d06d-4eae-b76e-3dc42eecba72.png)

In Query Params we need __{{apiKey}}(fake)__, __{{sessionId}}__, in Path __{{accountId}}__, and bode request:
```js {.line-numbers}
{
  "media_type": "tv",
  "media_id": {{tvShow}},
  "watchlist": true
}
```

__Test code below:__
```js {.line-numbers}
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

![image](https://user-images.githubusercontent.com/122685448/231306198-fa826e49-4389-457b-b811-706daa0d88d1.png)

Test response:

![image](https://user-images.githubusercontent.com/122685448/231306203-a87afcba-d167-4506-adc5-a31cabd475f3.png)
