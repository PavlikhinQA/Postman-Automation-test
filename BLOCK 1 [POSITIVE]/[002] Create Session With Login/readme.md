# [002] Create Session with Login
___
On this step, we must create new session, for this we must sent POST request.

__Use below path:__
```
/authentication/token/validate_with_login?api_key={{apiKey}}
```

In Query Params need use __{{apiKey}}__ as on previous step. In addition, we need to add body:
```
{
  "username": "{{userName}}",
  "password": "{{passWord}}",
  "request_token": "{{requestToken}}"
}
```

User name and password – we create in Variables.

Request token we create in previous step.

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

Response of status code must be 200.
Creating Variable __{{requestToken}}__, which will use in next requests and checking that it created.
![image](https://user-images.githubusercontent.com/122685448/231020192-3907f5ad-ed0a-4f1b-8c9b-44b68101e2b1.png)
