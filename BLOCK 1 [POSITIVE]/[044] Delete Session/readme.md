# [044] Delete Session
___

In this DEL request, we want to delete session, which created on the first steps.

__Use below path:__
```
authentication/session?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231300474-76b86844-e56b-4367-aabb-3afbfe62f28c.png)

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

![image](https://user-images.githubusercontent.com/122685448/231300486-6d847043-a667-4a91-8c55-cac9098e3c7f.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231300495-50be6d28-e24e-4699-99c8-e4b688b39d4a.png)

