# [025] Check that TV Show added to Watchlist
___

In this GET request, we are checking that exactly first random TV Show added to the system Watchlist and that there is only one item in this list.

__Use below path:__
```
account/:account_id/watchlist/tv?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231022152-ea96374c-dece-4647-9ae7-4966a89ac743.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, in the Path __{{account_id}}__.

__Test code below:__
``` js {.line-numbers}
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that TV Show <<" + jsonData.results[0].original_name + ">> has been added to Watch", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.results[0].id).to.eql(parseInt(pm.globals.get("tv1Id")));
});
```

In above code we are checking:

Response of status code must be 200, and checking that exactly first TV Show added in system Whatchlist and that there is only one item in it.

Therefore, after pushing Send, we receive body response:
 
![image](https://user-images.githubusercontent.com/122685448/231022174-ca67daff-e489-43da-b0fd-35670b95d179.png)
__And test response:__
![image](https://user-images.githubusercontent.com/122685448/231022184-1ac62a50-4752-46cc-934f-99ddbd2f45cf.png)


