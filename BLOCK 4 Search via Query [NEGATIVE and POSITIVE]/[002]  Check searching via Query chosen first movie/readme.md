# [002] Check searching via Query chosen first movie
___

In this step, we will search first movie via Query request using created variable on first step.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{movie1}}&page=1
```
![image](https://user-images.githubusercontent.com/122685448/231310082-6a130f59-23c9-4978-b373-c2e63fadabc4.png)
 
In Query Params we need __{{apiKey}}__, __{{movie#}}__ and page must be 1.
__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Movie №1: <<" + pm.globals.replaceIn("{{{{movie1}}}}") + ">> was found", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.results[0].original_title).to.eql(pm.variables.get("movie1"));
});
```
In above code we are checking:

Response of status code must be 200 and checking that movie from variable is the same as in response.

Bellow variable, which we create on first step

![image](https://user-images.githubusercontent.com/122685448/231310121-b7eb3e60-9c9d-4161-8c4f-23ec60a287c7.png)
 
 __Body response:__

![image](https://user-images.githubusercontent.com/122685448/231310147-46f3e8db-4de3-4cdd-8ba7-83ca9d09816e.png)
 
__Test Response:__

![image](https://user-images.githubusercontent.com/122685448/231310171-3ea1f092-f360-45c5-b054-e3432444ae99.png)
 
