# [006] Rate random Movie [NEGATIVE] number with a comma
___

In this step, we will use __POST__ request rate random movie with rate with a comma (2,5).

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=2,5
```
///***
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__, value = 2,5, __{{movie#Id}}__

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

Response of status code must be 201 and that move rated.

__Body response:__

///***
 
__Test response:__
///***
 
