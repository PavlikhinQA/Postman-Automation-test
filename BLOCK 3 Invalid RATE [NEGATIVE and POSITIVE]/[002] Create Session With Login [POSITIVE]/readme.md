# [002] Create Session with Login [POSITIVE]
___

On this step, we must create new session, for this we must sent __POST__ request.

__Use below path:__
```
/authentication/token/validate_with_login?api_key={{apiKey}}
```
![image](https://user-images.githubusercontent.com/122685448/231306677-1af6e746-e358-4225-a61f-b858d60fbbe7.png)
 
In Query Params need use __{{apiKey}}__ as on previous step. In addition, we need to add body:
```js {.line-numbers}
{
  "username": "{{userName}}",
  "password": "{{passWord}}",
  "request_token": "{{requestToken}}"
}
```

__Test code below:__
```js {.line-numbers}
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
 
 ![image](https://user-images.githubusercontent.com/122685448/231306693-971589ea-cee7-459b-a8c7-e03bbae1b1b5.png)
![image](https://user-images.githubusercontent.com/122685448/231306701-4073489f-b7c4-406a-8eeb-b7a8e8e2e5ed.png)
