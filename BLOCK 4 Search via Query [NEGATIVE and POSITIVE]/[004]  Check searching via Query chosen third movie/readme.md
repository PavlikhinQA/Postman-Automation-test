# [004]  Check searching via Query chosen third movie
___

In this step, we will search third movie via Query request using created variable on first step.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{movie1}}&page=1
```
![image](https://user-images.githubusercontent.com/122685448/231405187-a87ba237-53e7-459b-b332-ddd5f4927ce1.png)
 
In Query Params we need __{{apiKey}}__, __{{movie#}}__ and page must be 1.

__Test code below:__
```js {.line-numbers}
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

![image](https://user-images.githubusercontent.com/122685448/231405215-fefea1e3-2890-40d4-998a-6b7fb555a294.png)
 

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231405232-58d6e085-25b5-4704-9f1c-f4b9bc22c67e.png)

__Test Response:__

![image](https://user-images.githubusercontent.com/122685448/231405285-4861aa5d-047c-4533-94ef-e740df57215d.png)
 

