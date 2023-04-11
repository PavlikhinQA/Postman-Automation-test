# [003] Check searching via Query chosen second movie
___

In this step, we will search second movie via Query request using created variable on first step.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{movie1}}&page=1
```
![image](https://user-images.githubusercontent.com/122685448/231310266-21ce3062-ddc9-4527-8673-27d9a4eedce0.png)
 
In Query Params we need __{{apiKey}}__, __{{movie#}}__ and page must be 1.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Movie №2: <<" + pm.globals.replaceIn("{{{{movie2}}}}") + ">> was found", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.results[0].original_title).to.eql(pm.variables.get("movie2"));
});
```
In above code we are checking:

Response of status code must be 200 and checking that movie from variable is the same as in response.

Bellow variable that we create on first step

![image](https://user-images.githubusercontent.com/122685448/231310279-aca77921-e75b-4541-b35b-1e0bc16fea0d.png)
 
__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231310288-1cdf809a-66e1-4b0d-a066-faf7b111a92a.png)
 
__Test Response:__

![image](https://user-images.githubusercontent.com/122685448/231310295-c1d1c47d-8c31-44eb-a24e-801e838dbdab.png)
