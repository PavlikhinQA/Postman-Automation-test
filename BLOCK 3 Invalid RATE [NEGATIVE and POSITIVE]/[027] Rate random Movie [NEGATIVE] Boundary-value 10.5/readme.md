# [027] Rate random Movie [NEGATIVE] Boundary-value 10.5
___

In this step, we will use __POST__ request we will continue Boundary-value type of testing, we will rate new random movie with value 10.5. [POSITIVE]

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=10.5
```

///***
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__ and __{{movie#Id}}__.

__Test code below:__
```
pm.test("Status code is 400", function () {
    pm.response.to.have.status(400);
});

const response = pm.response.json();

pm.test("Value too high: Value must be less than, or equal to 10.0.", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 400 and system must tell movie did not rated.

__Body response:__
///***
 

__Test response:__
///***
 


