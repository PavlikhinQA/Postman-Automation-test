# [004] Get Details of Account [POSITIVE]
___

Now we need check that all ok and we must get details of our account.

__Use below path:__
```
/account?api_key={{apiKey}}&session_id={{sessionId}}
```

![image](https://user-images.githubusercontent.com/122685448/231306868-a5b55e3e-f929-4331-a9c8-56f38f1e533d.png)
 
In Query Params add __{{apiKey}}__ and __{{sessionId}}__. 

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("Session created for account", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.username).to.eql("QAndrey");
    pm.expect(jsonData.id).to.eql(parseInt(pm.variables.get("account_id")));
});
```
In above code we are checking:

Response of status code must be 200. In addition, check that in response __[id]__ will equal as __{{account_id}}__ and username will be equal real user name.

![image](https://user-images.githubusercontent.com/122685448/231306882-8303e61e-0f20-48ee-8b03-374f6b2721fb.png)
![image](https://user-images.githubusercontent.com/122685448/231306888-fb76fabe-993b-4168-a86b-17bcda79140c.png)
 
 

