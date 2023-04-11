# [020] Check that movie has been added to Watchlist
___

In this GET request we will check if movie added to system Whatchlist.

__Use below path:__
```
account/:account_id/watchlist/movies?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231021745-326dc89e-6f46-4495-ac91-4bcdb6dc2b98.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__ and in Path __{{account_id}}__:

__Test code below:__
``` js {.line-numbers}
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that movie <<" + jsonData.results[0].original_title + ">> has been added to Watch", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.results[0].id).to.eql(parseInt(pm.globals.get("movie4Id")));
});

pm.test("Only one movie in Watchlist ", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(1);
});
```

In above code we are checking:

Response of status code must be 200 and checking that the exactly __{{movie4Id}}__ added to the system Whatchlist and that there is only one movie in it.


Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231021757-ecb21ae0-1037-4b72-8bf1-58e6f2309c8a.png)

__And test response:__

![image](https://user-images.githubusercontent.com/122685448/231021763-340e358e-df38-46e6-b8f5-11323e3f5c9c.png)


