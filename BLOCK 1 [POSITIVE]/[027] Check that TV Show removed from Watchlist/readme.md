# [027] Check that TV Show removed from Watchlist
___

In this GET request, we checking that the system Watchlist is empty.

__Use below path:__
```
account/:account_id/watchlist/tv?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231022298-5979298e-833b-4cd4-8a91-1f2ed41949a4.png)
In Query Params we need __{{apiKey}}__, __{{sessionId}}__, in the Path __{{account_id}}__.

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that TV Show №" + pm.globals.replaceIn("{{tv1Id}}") + " removed from Watch", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(0);
});
```

In above code we are checking:

Response of status code must be 200, and checking that the system Watchlist is empty.

Therefore, after pushing Send, we receive body response:
![image](https://user-images.githubusercontent.com/122685448/231022315-82ca3518-267c-465b-b185-c306ea7e6237.png)

And test response:
![image](https://user-images.githubusercontent.com/122685448/231022321-6945c009-e5be-40c8-abbc-e34e68d32034.png)

