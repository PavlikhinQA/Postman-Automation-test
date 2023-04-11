# [007]  Check searching via Query numbers (8 length)
___

In this step, we will create random number with 8 length in pre-request and search it via Query.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{randomNumber}}&page=1
```
///***
 
In Query Params we need __{{apiKey}}__, __{{randomNumber}}__ and page must be 1.

__Pre-request:__
```
let randomNumber = Math.floor(Math.random() * (99999999 - 10000000 + 1)) + 10000000;
pm.globals.set("randomNumber", randomNumber.toString());

```
In this code, we create random number with length 8 and create for it variable.

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Movie not found", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(0);
});
```
In above code we are checking:

Response of status code must be 200 and checking that movie not found.

__Body response:__
///***

 
__Test Response:__
///***
 

__Bellow created new variable with unreal word:__
///***
 

