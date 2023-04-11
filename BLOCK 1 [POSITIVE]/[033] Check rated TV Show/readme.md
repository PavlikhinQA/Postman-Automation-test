# [033] Check rated TV Show
___

In this GET request, we will find a list of all TV Shows with rates and will check that for __{{tv2Id}}__ will be rate 4.5, as created variable in previous step, also that only one rated movie.

__Use below path:__
```
account/:account_id/rated/tv?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231297595-8dc38681-d468-4217-8e06-a3441c0e141d.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__.

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that TV Show № " + pm.globals.replaceIn("{{tv2Id}}") + " has been rated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.results[0].id).to.eql(parseInt(pm.globals.get("tv2Id")));
});
```

In above code we are checking:

Response of status code must be 200, checking that exactly tv2id was rated and that only one movie with rate.

Therefore, after pushing Send, we receive body response:
 
![image](https://user-images.githubusercontent.com/122685448/231297650-4c4fd7ce-a367-4c45-ab1d-92ded79e5606.png)
__Test response:__
![image](https://user-images.githubusercontent.com/122685448/231297670-402f7dd2-0263-4683-8d1a-468d9ae2d406.png)

