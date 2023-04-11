# [012] Rate random Movie [NEGATIVE] random sign (not letters, not numbers)
___

In this step, we will use __POST__ request we will rate new random movie with sign (not letters, not numbers) value.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value={{randomSign}}
```

![image](https://user-images.githubusercontent.com/122685448/231307761-d38f7302-1a52-48bd-95f7-db7f80837042.png)
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__, __{{movie#Id}}__ and value with new variable __{{randomSign}}__, which will created in __Pre-Request__:

```js {.line-numbers}
const signChars = "!@#$%^&*()_+-={}[]|\\\:;\"'<>,.?/";
const index = Math.floor(Math.random() * signChars.length);

const sign = signChars.charAt(index);
pm.globals.set("randomSign", sign);
```

In this pre request we will create random value with random sign: __!@#$%^&*()_+-={}[]|\:;"'<>,.?/;__

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

![image](https://user-images.githubusercontent.com/122685448/231307775-2dd1b8b2-dc17-452e-a433-fe124f8ae2b5.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231307795-106202ec-98c0-4646-973d-bedd1e662b42.png)
 
__Created new variable:__

![image](https://user-images.githubusercontent.com/122685448/231307814-65649b78-55f8-40b0-b889-e024fa96dd38.png)
 
