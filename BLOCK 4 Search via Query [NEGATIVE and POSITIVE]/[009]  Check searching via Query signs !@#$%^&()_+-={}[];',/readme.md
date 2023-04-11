# [009] Check searching via Query signs !@#$%^&()_+-={}[];',.
___

In this step, we will create random string __[!@#$%^&*()_+-={}[]|:;"'<>,.?/]__ in pre-request and search it via Query.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{randomSign}}&page=1
```
///***
 

In Query Params we need __{{apiKey}}__, __{{randomSign}}__ and page must be 1.

__Pre-request:__
```
const signChars = "!@#$%^&*()_+-={}[]|\\:;\"'<>,.?/";

const index = Math.floor(Math.random() * signChars.length);
const sign = signChars.charAt(index);
pm.globals.set("randomSign", sign);

```
In this code, we create random sign and create for it variable.

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const jsonData = pm.response.json();

if (jsonData.total_results === 0) {
    pm.test("No movies found", function() {
        pm.expect(jsonData.total_results).to.eql(0);
    });
} else {
    const index = Math.trunc(Math.random() * jsonData.results.length);
    const movieTitle = jsonData.results[index].original_title;
    pm.globals.set("movieTitle", movieTitle);

    pm.test("Movie found: <<" + pm.globals.replaceIn("{{movieTitle}}") + ">>", function() {
        pm.expect(jsonData.total_results).to.be.above(0);
        pm.expect(movieTitle).to.be.a('string');
    });
}
pm.globals.clear();
```

In above code we are checking:

Response of status code must be 200 and create two response if system found and not movie with requested sign. So we will have several request to find movie with a sign.

First request:

__Created bellow variable:__

///***

 
__Body response:__
///***
 

__Test Response:__
///***
 


Next request:

__Created bellow variable:__
///***


 
__Body response:__
///***

 
__Test Response:__
///***
 

