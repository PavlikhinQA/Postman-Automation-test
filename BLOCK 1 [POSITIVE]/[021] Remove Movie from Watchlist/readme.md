# [021] Remove Movie from Watchlist
___

In this __POST__ request, we will remove movie from system Whatchlist.

__Use below path:__
```
account/:account_id/watchlist?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231021814-f8f2f924-2176-44b1-b29b-a84a913c3717.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__ and in Path __{{account_id}}__, in bode request need:
```js {.line-numbers}
{
  "media_type": "movie",
  "media_id": {{movie4Id}},
  "watchlist": false
}
```

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("Movie № " + pm.globals.replaceIn("{{movie4Id}}") + " removed from Watch", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 200 and checking that the exactly __{{movie4Id}}__ removed to the system Whatchlist.

Therefore, after pushing Send, we receive body response:
![image](https://user-images.githubusercontent.com/122685448/231021828-52ef6467-d26d-4ab6-9782-fa7f753dedee.png)
And test response:
 
![image](https://user-images.githubusercontent.com/122685448/231021836-51a7f603-fe77-4e8e-acba-45a950a2f86c.png)

