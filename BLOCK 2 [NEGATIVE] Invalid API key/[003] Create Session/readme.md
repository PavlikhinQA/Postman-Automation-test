# [003] Create Session
___

In this __POST__ request, we want to create session and add to account

__Use below path:__
```
authentication/session/new?api_key=1234567890
```
///***
In Query Params we need __{{apiKey}}(fake)__ and body request:
```
{
    "request_token": "{{requestToken}}"
}
```

__Test code below:__
```
pm.test("Status code is 401 - OK", function () {
    pm.response.to.have.status(401);
});

const response = pm.response.json();
pm.globals.set("sessionId", response.session_id);

pm.test("Session has not been created", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 401, and checking that session will not create. Also create new variable for session.

Body response:
///***
Test response:
///***
New variable created but with null.
 
///***