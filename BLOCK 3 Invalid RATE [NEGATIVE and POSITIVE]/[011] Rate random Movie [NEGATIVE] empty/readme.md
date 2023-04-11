# [011] Rate random Movie [NEGATIVE] empty
___

In this step, we will use __POST__ request we will rate new random movie with empty value.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=
```

![image](https://user-images.githubusercontent.com/122685448/231307651-ced6fe2a-3f4d-403e-b59c-2bc6880a0385.png)
 
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
![image](https://user-images.githubusercontent.com/122685448/231307667-07b670d7-bf4b-4b5e-9d69-6b4b735aed3c.png)
 

__Test response:__
![image](https://user-images.githubusercontent.com/122685448/231307673-8b80343b-781c-4e7b-a8a8-fa0f37445be5.png)
 


