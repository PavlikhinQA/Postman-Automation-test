# [022] Check if Movie removed from Watchlist
___

This is the same request as was on __[020]__ step. We need GET request to understand that the system Whatchlist is empty.

__Use below path:__
```
account/:account_id/watchlist/movies?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231021883-2d73c386-a978-4d18-84ed-eddfe5739734.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__ and in Path __{{account_id}}__

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that movie № " + pm.globals.replaceIn("{{movie4Id}}") + " removed from Watch", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(0);
});
```

In above code we are checking:

Response of status code must be 200 and checking that the system Whatchlist is empty.

Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231021891-544a0f06-d1d9-42b6-9e7d-1eaace0a2f3a.png)

And test response:

![image](https://user-images.githubusercontent.com/122685448/231021897-0e3715a0-9076-4ef8-9e7f-1ac292816056.png)


