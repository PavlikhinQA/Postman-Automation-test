# [034] Delete Rate of TV Show
___

In this DEL request, we will delete rate for TV Show.

__Use below path:__
```
tv/:tv_id/rating?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231297790-3a0b6ea9-0de3-4049-bc7e-be9dc22bff2c.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{tv2Id}}__.

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("TV Show № " + pm.globals.replaceIn("{{tv2Id}}") + " was unrated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 200, checking that exactly __TV Show # 2__.

Therefore, after pushing Send, we receive body response:
 
![image](https://user-images.githubusercontent.com/122685448/231297820-4bb8d091-5517-46a7-96dd-b51e60ef6f11.png)

__Test response:__
![image](https://user-images.githubusercontent.com/122685448/231297857-d9210ce6-ecea-47e9-b56c-eac2daf8942a.png)

