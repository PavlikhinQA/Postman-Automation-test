# [007] Get Popular Movies
___

In this __GET__ request, we want to search popular list of movies.

__Use below path:__
```
movie/popular?api_key=1234567890
```
![image](https://user-images.githubusercontent.com/122685448/231305938-d149eec0-9e2b-4272-9375-9a7551cbb383.png)

In Query Params we need __{{apiKey}}(fake)__.

__Test code below:__
```js {.line-numbers}
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

![image](https://user-images.githubusercontent.com/122685448/231305954-97900aab-98d4-4b26-8442-c698ac874fb5.png)

Test response:

![image](https://user-images.githubusercontent.com/122685448/231305962-14e010d5-e37d-42e3-8bd2-a4000b5b3099.png)
