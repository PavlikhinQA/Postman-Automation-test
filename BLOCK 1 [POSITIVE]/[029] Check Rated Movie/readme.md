# [029] Check Rated Movie
___

In this GET request, we will find a list of all movies with rates and will check that for movie5Id will be rate 7.5, as created variable in previous step, also that only one rated movie.

__Use below path:__
```
account/:account_id/rated/movies?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231022470-0d33fdc6-316a-430e-af33-7f4d7b190552.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__.

__Test code below:__
``` js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that movie № " + + pm.globals.replaceIn("{{movie5Id}}") + " has been rated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.results[0].id).to.eql(parseInt(pm.globals.get("movie5Id")));
});

pm.test("Only one movie in total results", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(1);
});
```

In above code we are checking:

Response of status code must be 200, checking that exactly movie 5 was rated and that only one movie with rate.

Therefore, after pushing Send, we receive body response:
 
![image](https://user-images.githubusercontent.com/122685448/231022486-bf1243b1-b4df-4c09-9438-600f5f9f1941.png)

__In addition, test response:__

![image](https://user-images.githubusercontent.com/122685448/231022490-21958dcf-789c-4e40-a841-1e95bc8252f2.png)
