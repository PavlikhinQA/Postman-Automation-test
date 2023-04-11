# [020] Delete Rate of the movie
___

In this step, we will use __DEL__ request to delete rate.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231308715-704b5dbe-4e9b-4f95-8d48-ff08a1373059.png)

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

![image](https://user-images.githubusercontent.com/122685448/231308748-1171e593-6bad-4c69-b2e4-d38d95feb9fe.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231308769-54409f90-81b2-47e4-9981-3711d8dddb3c.png)
 

