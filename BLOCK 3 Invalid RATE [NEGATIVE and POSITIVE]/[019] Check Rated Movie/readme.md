# [019] Check Rated Movie
___

In this step, we will use __GET__ request to check that movie rated on previous step.

__Use below path:__
```
account/:account_id/rated/movies?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231308566-710965b2-e568-43f5-9a03-27abfa1461e5.png)
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__ and __{{account_id}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Movie rated: [" + jsonData.results[0].rating + "]", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(1);
});
```

In above code we are checking:

Response of status code must be 200 and system rated correctly movie.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231308579-2c1e52fc-5162-4cd4-867c-9482df2e0740.png)
 
__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231308585-cde59af2-73f6-40ff-b399-8c3a5110a9b2.png)


