# [006] Rate random Movie [NEGATIVE] number with a comma
___

In this step, we will use __POST__ request rate random movie with rate with a comma (2,5).

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value=2,5
```
![image](https://user-images.githubusercontent.com/122685448/231307134-780215c4-372a-49c4-9e59-e27d7746336a.png)
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__, value = 2,5, __{{movie#Id}}__

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();

pm.test("Movie was rated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```
In above code we are checking:

Response of status code must be 201 and that move rated.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231307146-c0513714-b459-40f2-a07a-2d046b817c5d.png)
 
__Test response:__
![image](https://user-images.githubusercontent.com/122685448/231307152-383f3088-d850-484a-9d2b-b0200a0d679c.png)
 
