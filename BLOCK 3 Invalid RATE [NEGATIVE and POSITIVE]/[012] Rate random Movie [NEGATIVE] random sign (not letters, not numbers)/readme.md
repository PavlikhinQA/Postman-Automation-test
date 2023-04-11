# [012] Rate random Movie [NEGATIVE] random sign (not letters, not numbers)
___

In this step, we will use __POST__ request we will rate new random movie with sign (not letters, not numbers) value.

__Use below path:__
```
movie/:movie_id/rating?api_key={{apiKey}}&session_id={{sessionId}}&value={{randomSign}}
```

///***
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__, __{{movie#Id}}__ and value with new variable __{{randomSign}}__, which will created in __Pre-Request__:

```
const signChars = "!@#$%^&*()_+-={}[]|\\\:;\"'<>,.?/";
const index = Math.floor(Math.random() * signChars.length);

const sign = signChars.charAt(index);
pm.globals.set("randomSign", sign);
```

In this pre request we will create random value with random sign: __!@#$%^&*()_+-={}[]|\:;"'<>,.?/;__

__Test code below:__
```
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
///***
 

__Test response:__
///***
 

__Created new variable:__
///***
 
