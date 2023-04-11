# [003] Create Session
___

In this __POST__ request, we want to create session and add to account

__Use below path:__
```
authentication/session/new?api_key=1234567890
```
![image](https://user-images.githubusercontent.com/122685448/231305100-b9b63fee-7b17-4be6-a9c0-e31cfaf7556f.png)

In Query Params we need __{{apiKey}}(fake)__ and body request:
```js {.line-numbers}
{
    "request_token": "{{requestToken}}"
}
```

__Test code below:__
```js {.line-numbers}
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

![image](https://user-images.githubusercontent.com/122685448/231305134-0508ae40-7721-4a75-be51-4e69abb7279c.png)

Test response:
![image](https://user-images.githubusercontent.com/122685448/231305146-77228e99-decf-4e16-a448-03bd1fd9b194.png)

New variable created but with null.
 
![image](https://user-images.githubusercontent.com/122685448/231305163-9683a403-eaa1-4f1c-ae63-d5f10b573672.png)
