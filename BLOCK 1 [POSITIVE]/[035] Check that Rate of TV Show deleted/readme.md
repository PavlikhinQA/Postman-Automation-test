# [035] Check that Rate of TV Show deleted
___

In this GET request, we will find a list of all TV Shows with rates – must be empty.

__Use below path:__
```
account/:account_id/rated/tv?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231297946-f5a72c4a-f191-4274-b8d6-fc478764c59c.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__.

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that TV Show " + pm.globals.replaceIn("{{tv2Id}}") + " has been unrated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(0);
});
```

In above code we are checking:

Response of status code must be 200, checking that rated list is empty

Therefore, after pushing Send, we receive body response:
![image](https://user-images.githubusercontent.com/122685448/231297968-28fc473e-c2a6-4cd7-938c-be3251e7ff8f.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231297992-a6795ece-5594-4602-86a8-440e7a964b9e.png)
 
