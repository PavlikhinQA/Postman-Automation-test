# [014] Rate random Movie Boundary-value ZERO [NEGATIVE]
___

In this step, we will use __POST__ request we will continue __Boundary-value__ type of testing, we will rate new random movie with value 0.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=0 
```

![image](https://user-images.githubusercontent.com/122685448/231308005-9e0c1383-c469-4879-9336-c4adfa8c180b.png)
 
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

![image](https://user-images.githubusercontent.com/122685448/231308032-9a8c9383-c0bf-42df-9054-06cf0864b36d.png)
 
__Test response:__
![image](https://user-images.githubusercontent.com/122685448/231308045-37705f2d-5e2f-466e-9a14-6f515706a230.png)
 


