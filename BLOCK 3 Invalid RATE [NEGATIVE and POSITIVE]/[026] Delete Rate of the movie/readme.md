# [026] Delete Rate of the movie
___

In this step, we will use __DEL__ request to delete rate.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}
```

![image](https://user-images.githubusercontent.com/122685448/231309300-d2ba3a5e-ef8a-4f1e-84e3-418822d0c88f.png)
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__ and __{{movie#Id}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("Movie was unrated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```
In above code we are checking:

Response of status code must be 200 and system unrated movie.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231309305-bc7f5774-7bb0-46ec-b99d-6319e0d3cfa2.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231309309-18ff678d-bac6-4bc0-b793-2737c2163b7a.png)


