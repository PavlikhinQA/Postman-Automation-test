#[028] Rate random Movie
___

In this POST request, we will give a random rate (from 0,5 till 10 with step 0,5) for random movie.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value={{myNumber}}
```
![image](https://user-images.githubusercontent.com/122685448/231022372-ce67b932-d419-493f-bad1-dfc1aa75dc62.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, value with new variable __{{myNumber}}__, which will created in Pre-request and in the Path __{{movie5Id}}__, without body request.

__Pre-req.:__
```
const randomNumber = (Math.floor(Math.random() * 19) + 1) / 2;
pm.globals.set("myNumber", randomNumber);
```

We created here new variable __{{myNumber}}__ with random number: from 0,5 till 10 with step 0,5

__Test code below:__
```
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();

pm.test("Movie № " + pm.globals.replaceIn("{{movie5Id}}") + " was rated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 201, and checking that the movie rated.

Therefore, after pushing Send, we receive body response:

![image](https://user-images.githubusercontent.com/122685448/231022403-37288b67-83c8-41e0-9ec6-bb0bc769bfcd.png)

And test response:
![image](https://user-images.githubusercontent.com/122685448/231022414-f036b3a6-bd04-47b2-beb7-4ebe6816d879.png)
And we have new variable:
 
![image](https://user-images.githubusercontent.com/122685448/231022425-c7969430-6450-4fee-a418-62f9e0be3d8e.png)
