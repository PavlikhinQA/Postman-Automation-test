# [031] Check that Rated Movies deleted
___
In this GET request, we will find a list of all movies with rates – must be empty.

__Use below path:__
```
account/:account_id/rated/movies?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231022577-e958c4d5-5810-4cb4-a9db-2a17d0ad1e0c.png)
In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__.

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that movie " + pm.globals.replaceIn("{{movie5Id}}") + " has been unrated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(0);
});
```

In above code we are checking:

Response of status code must be 200, checking that rated list is empty

Therefore, after pushing Send, we receive body response:
![image](https://user-images.githubusercontent.com/122685448/231022597-19ac0df5-84d6-4c75-a5c4-9a3983d2b5eb.png)

__In addition, test response:__
![image](https://user-images.githubusercontent.com/122685448/231022603-15a5ab67-882f-4df4-b31f-1f651a936efd.png)

