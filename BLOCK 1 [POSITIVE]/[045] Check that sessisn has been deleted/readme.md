# [045] Check that session has been deleted
___

In this GET request, we check that session deleted in previous step and we will delete all variables.

__Use below path:__
```
account?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231300571-b5c46fad-ec45-44eb-914b-770376c48d93.png)

In Query Params we need __{{apiKey}}__ and __{{sessionId}}__.

__Test code below:__
``` js {.line-numbers}
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

![image](https://user-images.githubusercontent.com/122685448/231300588-4a34be18-9e91-4801-a338-da83945770b8.png)

Therefore, after pushing Send, we receive body response:
![image](https://user-images.githubusercontent.com/122685448/231300599-b2a88919-fa9d-4340-80ce-334855017846.png)
 
__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231300607-93c9c52f-aa71-4adb-a388-bf49627d8d21.png)

__Variable list:__

![image](https://user-images.githubusercontent.com/122685448/231300628-4b409e85-9379-4aea-9cf4-9d537ca4ae0e.png)
