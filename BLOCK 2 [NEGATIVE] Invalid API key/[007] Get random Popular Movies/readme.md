# [007] Get Popular Movies
___

In this __GET__ request, we want to search popular list of movies.

__Use below path:__
```
movie/popular?api_key=1234567890
```
///***

In Query Params we need __{{apiKey}}(fake)__.

__Test code below:__
```
pm.test("Status code is 401 - OK", function () {
    pm.response.to.have.status(401);
});

const response = pm.response.json();

pm.test("The system does not allow searching movies due to Invalid API key", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 401, and checking if system allow searching any movies without correct __apiKey__.

Body response:

///***

Test response:

///***
