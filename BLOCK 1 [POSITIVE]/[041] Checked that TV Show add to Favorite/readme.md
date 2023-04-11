# [041] Checked that TV Show add to Favorite
___

In this GET request, we checking that exactly TV Show added to system Favorite list

__Use below path:__
```
account/:account_id/favorite/tv?api_key={{apiKey}}&session_id={{sessionId}}
```

![image](https://user-images.githubusercontent.com/122685448/231299342-8af2ba26-f534-4596-a21b-7a02c51a94e1.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__:

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that TV Show <<" + jsonData.results[0].original_name + ">> added to Favorite", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.results[0].id).to.eql(parseInt(pm.globals.get("tv3Id")));
});
```

In above code we are checking:

Response of status code must be 200, checking that exactly random TV Show added to system Favorite list.

Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231299413-656ae29a-5dbb-483b-9b0b-eca963df6456.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231299513-927f77c9-70f9-4525-920f-bb5c8da57220.png)

