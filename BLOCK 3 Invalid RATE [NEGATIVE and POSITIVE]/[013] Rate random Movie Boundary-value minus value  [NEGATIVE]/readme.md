# [013] Rate random Movie Boundary-value minus value [NEGATIVE]
___

In this step, we will use __POST__ request we will start __Boundary-value__ type of testing, we will rate new random movie with minus value.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=-0.5 
```

![image](https://user-images.githubusercontent.com/122685448/231307906-92c24587-ce15-4283-8a56-3b960d5f8b1f.png)
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__ and __{{movie#Id}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 400", function () {
    pm.response.to.have.status(400);
});

const response = pm.response.json();

pm.test("The movie has not been rated.", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 400 and system must tell that value invalid.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231307916-e0446327-e81e-4d5b-abf3-7802e6819053.png)
 
__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231307927-3f8f6585-c8e6-4a01-b309-f3dda1761762.png)


