# [023] Delete Rate of the movie
___

In this step, we will use __DEL__ request to delete rate.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231308998-2f3549e0-e93c-4e0b-8a52-e45581691f4b.png)

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

![image](https://user-images.githubusercontent.com/122685448/231309016-8d62f69e-27d8-4272-aac9-8f2a3631cc5f.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231309031-efca6b73-3b65-4763-bb39-ed90843789e4.png)



