# [024] Rate random Movie Boundary-value 10
___

In this step, we will use __POST__ request we will continue Boundary-value type of testing, we will rate new random movie with value 10. [POSITIVE]

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=10
```

![image](https://user-images.githubusercontent.com/122685448/231309102-c1b56320-6ef5-41c7-ba5f-af5dc211873a.png)
 
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
![image](https://user-images.githubusercontent.com/122685448/231309116-ea25b9c7-7477-403c-a339-7af49fe8f1e9.png)
 

__Test response:__
![image](https://user-images.githubusercontent.com/122685448/231309122-ca796fa2-dd7e-4c14-965d-d46b77278cdb.png)


