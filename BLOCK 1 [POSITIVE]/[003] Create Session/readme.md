# [003] Create Session
___

On this step, we must create new session __{{sessionId}}__, for this we must sent POST request

__Use below path:__
```
/authentication/session/new?api_key={{apiKey}}
```

In Query Params need use __{{apiKey}}__ as on first step. In addition, we need to add body:
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
Also creating new variable __{{sessionId}}__.


![image](https://user-images.githubusercontent.com/122685448/231020285-105184bd-e988-4d02-aa72-23abea61f6c5.png)
![image](https://user-images.githubusercontent.com/122685448/231020301-698a98fa-50e9-4e20-9d7e-0afce892683d.png)
![image](https://user-images.githubusercontent.com/122685448/231020307-ffa8175b-b476-43fa-a866-496e5baacf3a.png)
 
 
