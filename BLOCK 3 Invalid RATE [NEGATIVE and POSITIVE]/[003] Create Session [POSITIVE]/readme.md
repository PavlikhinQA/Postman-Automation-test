# [003] Create Session [POSITIVE]
___

On this step, we must create new session __{{sessionId}}__, for this we must sent __POST__ request

__Use below path:__
```
/authentication/session/new?api_key={{apiKey}}
```

///***
 
In Query Params need use __apiKey__ as on first step. In addition, we need to add body:
```
{
    "request_token": "{{requestToken}}"
}
```

Request token we create on first step.

__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("The token is attached to the user.", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```
In above code we are checking:

Response of status code must be 200. In addition, check that token added to session.

Also creating new variable __{{sessionId}}__
///***
///***
///***
 
 
 

