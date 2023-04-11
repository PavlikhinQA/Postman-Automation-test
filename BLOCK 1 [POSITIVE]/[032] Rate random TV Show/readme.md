# [032] Rate random TV Show
___

In this POST request, we will give a random rate (from 0,5 till 10 with step 0,5) for random TV Show.

__Use below path:__
```
tv/:tv_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value={{myNumber2}}
```
![image](https://user-images.githubusercontent.com/122685448/231022646-0e382ca4-85b4-43ce-9355-2e474b3103ad.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, value with new variable __{{myNumber2}}__, which will created in Pre-request and in the Path __{{tv2Id}}__, without body request.

__Pre-req.:__
```js {.line-numbers}
const randomNumber = (Math.floor(Math.random() * 19) + 1) / 2;
pm.globals.set("myNumber2", randomNumber);
```

We created here new variable __{{myNumber2}}__ with random number: from 0,5 till 10 with step 0,5

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();

pm.test("TV Show № " + pm.globals.replaceIn("{{tv2Id}}") + " was rated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 201, and checking that the TV Show rated.

Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231022660-8887af1e-7295-4164-bad2-438580ffb364.png)

In addition, test response:
![image](https://user-images.githubusercontent.com/122685448/231022668-90030e72-a783-4476-a4a2-c96d73747c35.png)

In addition, we have new variable:
![image](https://user-images.githubusercontent.com/122685448/231022676-756a5c94-7716-4d17-b4c2-2cff6b80565d.png)


