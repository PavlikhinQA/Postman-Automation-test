# [004] Get Details of Account
___
In this GET request, we want to receive detail of our account and understand if session created or not.

__Use below path:__
```
account?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231305547-814c8cd2-3953-4306-82f1-494200b09f0b.png)

In Query Params we need __{{apiKey}}(real)__, __{{session_id}}__ (= null)

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 401 - OK", function () {
    pm.response.to.have.status(401);
});
const response = pm.response.json();

pm.test("Authentication failed - session not found", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```

In above code we are checking:

Response of status code must be 401, and checking that Authentication failed.

Body response:

![image](https://user-images.githubusercontent.com/122685448/231305559-1f3b4def-aff6-40b7-99f0-8b52130d4535.png)

Test response:
 
![image](https://user-images.githubusercontent.com/122685448/231305581-ebb10591-7352-42c2-aa58-dd0675d2a082.png)
