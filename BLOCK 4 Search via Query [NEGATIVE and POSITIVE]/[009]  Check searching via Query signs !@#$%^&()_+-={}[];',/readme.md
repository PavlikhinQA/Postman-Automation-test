# [009] Check searching via Query signs !@#$%^&()_+-={}[];',.
___

In this step, we will create random string __[!@#$%^&*()_+-={}[]|:;"'<>,.?/]__ in pre-request and search it via Query.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{randomSign}}&page=1
```
![image](https://user-images.githubusercontent.com/122685448/231406819-127c42fa-e554-45f8-8bb8-8fc218e86c6e.png)

In Query Params we need __{{apiKey}}__, __{{randomSign}}__ and page must be 1.

__Pre-request:__
``` js {.line-numbers}
const signChars = "!@#$%^&*()_+-={}[]|\\:;\"'<>,.?/";

const index = Math.floor(Math.random() * signChars.length);
const sign = signChars.charAt(index);
pm.globals.set("randomSign", sign);

```
In this code, we create random sign and create for it variable.

__Test code below:__
``` js {.line-numbers}
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

## First request:

__Created bellow variable:__

![image](https://user-images.githubusercontent.com/122685448/231406903-527f491b-e2f5-49ff-990b-a6ec85ddfc7a.png)

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231406939-1560a077-b340-4a48-b81c-cf9475ce5337.png)
 
__Test Response:__

![image](https://user-images.githubusercontent.com/122685448/231406971-08af42f0-bc23-49e1-a663-271bbe698fea.png)
 


## Next request:

__Created bellow variable:__
![image](https://user-images.githubusercontent.com/122685448/231407011-abdfff95-3576-49c4-9669-1c87c21066f8.png)

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231407132-9ad91972-def6-48bd-af44-b5af081779b9.png)

__Test Response:__

![image](https://user-images.githubusercontent.com/122685448/231407179-4d1cdb27-ed39-49fa-b087-1bdf5fe6337d.png)

