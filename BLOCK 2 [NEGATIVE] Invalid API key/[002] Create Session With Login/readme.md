# [002] Create Session with Login
___

In this __POST__ request, we want to create session with correct __api_key__

__Use below path:__
```
authentication/token/validate_with_login?api_key=1234567890
```
![image](https://user-images.githubusercontent.com/122685448/231304977-9e6d66c6-2e1e-40b8-9673-0c2073b27b71.png)

In Query Params we need __{{apiKey}}(fake)__ and body request:
```js {.line-numbers}
{
  "username": "{{userName}}",
  "password": "{{passWord}}",
  "request_token": "{{requestToken}}"
}
```

__Test code below:__
```js {.line-numbers}
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

![image](https://user-images.githubusercontent.com/122685448/231304997-71003713-5a49-45ca-a558-83de84b30cec.png)

Test response:

![image](https://user-images.githubusercontent.com/122685448/231305012-6f648705-f82d-46c9-9797-75920314bf1d.png)

