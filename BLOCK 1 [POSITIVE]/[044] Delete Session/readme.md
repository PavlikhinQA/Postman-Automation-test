# [044] Delete Session
___

In this DEL request, we want to delete session, which created on the first steps.

__Use below path:__
```
authentication/session?api_key={{apiKey}}&session_id={{sessionId}}
```
///***

In Query Params we need __{{apiKey}}__ and __{{sessionId}}__.

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Session has been deleted", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 200, checking that session has been deleted.

Therefore, after pushing Send, we receive body response:

///***
In addition, test response:
///***

