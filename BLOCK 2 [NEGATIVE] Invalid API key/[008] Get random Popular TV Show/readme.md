# [008] Get Popular TV Show
___

In this __GET__ request, we want to search popular list of TV Shows.

__Use below path:__
```
tv/popular?api_key=1234567890
```
![image](https://user-images.githubusercontent.com/122685448/231306085-8fdc6bdb-8b3a-4ed6-b15a-f64727e8eb2d.png)

In Query Params we need __{{apiKey}}(fake)__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 401 - OK", function () {
    pm.response.to.have.status(401);
});

const response = pm.response.json();

pm.test("The system does not allow searching TV Showes due to Invalid API key", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 401, and checking if system allow searching any TV Shows without correct __apiKey__.

Body response:
![image](https://user-images.githubusercontent.com/122685448/231306095-ab870cb2-3ff7-41e2-9817-c0898abab89b.png)
Test response:
![image](https://user-images.githubusercontent.com/122685448/231306102-be19d00c-4a7d-4231-a74c-b0c949ade299.png)
