# [037] Check that movie added to Favorite
___

In this GET request, we checking that exactly movie added to system Favorite list

__Use below path:__
```
account/:account_id/favorite/movies?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231298145-425afb4c-ef64-48f0-825c-6710efee785e.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__:

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that movie № " + pm.globals.replaceIn("{{movie6Id}}") + " added to Favorite", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.results[0].id).to.eql(parseInt(pm.globals.get("movie6Id")));
});
```
In above code we are checking:

Response of status code must be 200, checking that exactly random movie added to system Favorite list.

Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231298164-d4156b9f-5594-4c68-8164-ba63e309c250.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231298195-2b8fb9af-27da-4019-9ebb-0010662e23ed.png)
