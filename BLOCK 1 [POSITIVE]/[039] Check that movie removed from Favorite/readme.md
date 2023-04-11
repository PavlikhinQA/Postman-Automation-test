# [039] Check that movie removed from Favorite
___

In this GET request, we check that exactly random movie removed from system Favorite list.

__Use below path:__
```
account/:account_id/favorite/movies?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231298454-eb16b9d1-1c8a-4730-85d5-7850b892cae0.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__.

__Test code below:__
``` js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that movie № " + pm.globals.replaceIn("{{movie6Id}}") + " removed from Favorite", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(0);
});
```

In above code we are checking:

Response of status code must be 200, checking that exactly random movie removed from system Favorite list.

Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231298545-32b63931-8aff-4fc1-af91-e37e467de611.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231298653-9af27704-6ecb-4d75-ab16-ceeb489a102d.png)
 
