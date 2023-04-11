# [002] Create Session with Login
___

In this __POST__ request, we want to create session with correct __api_key__

__Use below path:__
```
authentication/token/validate_with_login?api_key=1234567890
```
///***

In Query Params we need __{{apiKey}}(fake)__ and body request:
```
{
  "username": "{{userName}}",
  "password": "{{passWord}}",
  "request_token": "{{requestToken}}"
}
```

__Test code below:__
```
pm.test("Status code is 401 - OK", function () {
    pm.response.to.have.status(401);
});

const response = pm.response.json();

pm.test("Token for session has not been created", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 401, and checking that session will not create.

Body response:
///***
Test response:
///*** 

