# [010] Rate random Movie [NEGATIVE] text
___

In this step, we will use __POST__ request we will rate new random movie with value string/text.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=five
```

![image](https://user-images.githubusercontent.com/122685448/231307550-bce339b3-9458-40b1-befd-90196edba5ec.png)
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__ and __{{movie#Id}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 400", function () {
    pm.response.to.have.status(400);
});

const response = pm.response.json();

pm.test("The movie has not been rated.", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 400 and system must tell that value invalid.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231307557-66a00e0c-530a-46ba-8156-5df41386659e.png)
 
__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231307565-71b944d0-df19-4fa2-8f73-f79505babd28.png)


