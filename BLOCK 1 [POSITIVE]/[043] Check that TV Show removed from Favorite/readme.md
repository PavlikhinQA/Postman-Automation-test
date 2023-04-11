# [043] Check that TV Show removed from Favorite
___

In this GET request, we check that exactly random TV Show removed from system Favorite list.

__Use below path:__
```
account/:account_id/favorite/tv?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231300381-db9a331f-fdd3-479e-896d-cf319e0deaa5.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__.

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that TV Show № " + pm.globals.replaceIn("{{tv3Id}}") + " removed from Favorite", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(0);
});
```

In above code we are checking:

Response of status code must be 200, checking that exactly random TV Show removed from system Favorite list.

Therefore, after pushing Send, we receive body response:
 
![image](https://user-images.githubusercontent.com/122685448/231300394-68e10eb4-8d2d-4c45-9ac7-f4b30a8749be.png)

In addition, test response:

![image](https://user-images.githubusercontent.com/122685448/231300407-bac5e4f0-939f-4790-bf7b-04b9e39e0734.png)
