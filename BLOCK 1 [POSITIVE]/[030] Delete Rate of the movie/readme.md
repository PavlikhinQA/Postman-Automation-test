# [030] Delete Rate of the movie
___

In this DEL request, we will delete rate for movie.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231022520-f61bd1d6-d226-47f1-a5de-26969c1702d0.png)
In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{movie5Id}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("Movie № " + pm.globals.replaceIn("{{movie5Id}}") + " was unrated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 200, checking that exactly movie # 5.

Therefore, after pushing Send, we receive body response:
 
![image](https://user-images.githubusercontent.com/122685448/231022532-bba458c5-d86b-4f04-b182-52c0ef55c9c4.png)
In addition, test response:

![image](https://user-images.githubusercontent.com/122685448/231022537-27a03e2c-6630-4e98-8a26-99129e5a4555.png)
