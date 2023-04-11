# [008] Delete Rate of the movie
___

In this step, we will use __DEL__ request to delete rate from the movie, which rated in previous steps.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}
```

![image](https://user-images.githubusercontent.com/122685448/231307325-6721b667-80ab-4551-af86-fb1a50df8ef1.png)
 
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

Response of status code must be 200 and that system must tell that movie unrated.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231307339-cf5c9f39-bec6-4ae7-a325-0f7b3d9662fd.png)
 
__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231307352-00f3cd1d-3a71-4dcd-a3e0-9a668978c0c7.png)
 
