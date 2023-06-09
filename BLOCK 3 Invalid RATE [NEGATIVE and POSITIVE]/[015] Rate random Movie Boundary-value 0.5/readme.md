# [015] Rate random Movie Boundary-value 0.5
___

In this step, we will use __POST__ request we will continue __Boundary-value__ type of testing, we will rate new random movie with value 0.5. [POSITIVE]

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=0.5 
```

![image](https://user-images.githubusercontent.com/122685448/231308148-e6b3b25e-5bdf-42bc-b8d4-1e6c1ba5cf6a.png)
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__ and __{{movie#Id}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();

pm.test("Movie was rated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 201 and system must tell that movie rated.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231308156-ed9cbb76-e803-420d-b9cd-5b7d78114912.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231308169-726b43d1-c7b9-45b9-b382-e06452d0a9eb.png)
 


