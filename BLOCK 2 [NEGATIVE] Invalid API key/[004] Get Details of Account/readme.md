# [004] Get Details of Account
___
In this GET request, we want to receive detail of our account and understand if session created or not.

__Use below path:__
```
account?api_key={{apiKey}}&session_id={{sessionId}}
```
///***

In Query Params we need __{{apiKey}}(real)__, __{{session_id}}__ (= null)

__Test code below:__
```
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
///*** 
Test response:
 
///***