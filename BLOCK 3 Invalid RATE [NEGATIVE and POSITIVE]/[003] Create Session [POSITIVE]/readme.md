# [003] Create Session [POSITIVE]
___

On this step, we must create new session __{{sessionId}}__, for this we must sent __POST__ request

__Use below path:__
```
/authentication/session/new?api_key={{apiKey}}
```

![image](https://user-images.githubusercontent.com/122685448/231306756-ecd6e1e4-1fac-415c-ab16-9d2f134c784b.png)
 
In Query Params need use __apiKey__ as on first step. In addition, we need to add body:
```js {.line-numbers}
{
    "request_token": "{{requestToken}}"
}
```

Request token we create on first step.

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

Response of status code must be 200. In addition, check that token added to session.

Also creating new variable __{{sessionId}}__

![image](https://user-images.githubusercontent.com/122685448/231306783-4f4f3a7e-b222-4ad5-b312-b83d0fa94e86.png)
![image](https://user-images.githubusercontent.com/122685448/231306791-0af9868e-aa4f-4632-a164-dcea01e1e096.png)
![image](https://user-images.githubusercontent.com/122685448/231306801-b06ef8e6-800a-4c9e-84b1-ed911d097eca.png)
 

