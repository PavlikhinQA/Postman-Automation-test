# [017] Delete Rate of the movie
___

In this step, we will use __DEL__ request to delete rate.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231308348-d907e84c-b3a0-41df-9595-5a6703530aef.png)
 
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

![image](https://user-images.githubusercontent.com/122685448/231308367-8df0c24d-b8aa-4d48-8733-e528ee974266.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231308380-ada0147d-b188-4b56-b48b-709f5e5423eb.png)
