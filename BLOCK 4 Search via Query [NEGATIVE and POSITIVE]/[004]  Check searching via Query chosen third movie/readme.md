# [004]  Check searching via Query chosen third movie
___

In this step, we will search third movie via Query request using created variable on first step.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{movie1}}&page=1
```
///***
 
In Query Params we need __{{apiKey}}__, __{{movie#}}__ and page must be 1.

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Movie №3: <<" + pm.globals.replaceIn("{{{{movie3}}}}") + ">> was found", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.results[0].original_title).to.eql(pm.variables.get("movie3"));
});
```
In above code we are checking:

Response of status code must be 200 and checking that movie from variable is the same as in response.

Bellow variable that we create on first step
///***
 
 
__Body response:__
///***
 

__Test Response:__
///***
 

