# [021] Rate random Movie Boundary-value 9.5
___

In this step, we will use POST request we will continue Boundary-value type of testing, we will rate new random movie with value 9.5. [POSITIVE]

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=9.5
```
///***
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__ and __{{movie#Id}}__.

__Test code below:__
```
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
///***
 

__Test response:__
///***


 
