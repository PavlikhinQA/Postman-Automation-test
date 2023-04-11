# [018] Rate random Movie Boundary-value 1
___

In this step, we will use __POST__ request we will continue Boundary-value type of testing, we will rate new random movie with value 1. [POSITIVE]

__Use below path__:
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=1
```

![image](https://user-images.githubusercontent.com/122685448/231308456-80dca75a-baac-478f-9147-823dbbd948c5.png)
 
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

![image](https://user-images.githubusercontent.com/122685448/231308480-03314f36-86ab-4466-a932-db644ca6d7f1.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231308489-85c746af-e7f0-4d51-8465-f00756f44bcd.png)
 
