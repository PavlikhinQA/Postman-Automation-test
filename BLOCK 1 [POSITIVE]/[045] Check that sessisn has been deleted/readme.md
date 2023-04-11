# [045] Check that session has been deleted
___

In this GET request, we check that session deleted in previous step and we will delete all variables.

__Use below path:__
```
account?api_key={{apiKey}}&session_id={{sessionId}}
```
///***
In Query Params we need __{{apiKey}}__ and __{{sessionId}}__.

__Test code below:__
```
pm.test("Status code is 401", function () {
    pm.response.to.have.status(401);
});

const response = pm.response.json();

pm.test("Session has been deleted", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});

pm.globals.clear();
```

In above code we are checking:

Response of status code must be 401 that mean there is no such __{{sessionId}}__.

Before sending request, we have several variables, which are below and which must deleted too.

///***

Therefore, after pushing Send, we receive body response:
///***
 
In addition, test response:
///***

Variable list:

///***
