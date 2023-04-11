# [009] Rate random Movie [NEGATIVE] not multiple of 0.50
___

In this step, we will use __POST__ request we will rate new random movie with value which not multiple of 0.5 (as in documentation).

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=5.63
```

![image](https://user-images.githubusercontent.com/122685448/231307443-a40a59a0-f13c-49b2-95f4-1fbf5117aa1c.png)
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__ and __{{movie#Id}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 400", function () {
    pm.response.to.have.status(400);
});

const response = pm.response.json();

pm.test("Value invalid: Values must be a multiple of 0.50.", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 400 and system must tell that value invalid.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231307457-0105087e-605d-40a5-a6be-71412146adac.png)
 
__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231307473-964044ca-fb6e-4b83-89b8-512308eff509.png)
 

