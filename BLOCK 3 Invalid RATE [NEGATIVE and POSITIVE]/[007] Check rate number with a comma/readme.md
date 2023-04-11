# [007] Check rate: number with a comma
___

In this step, we will use __GET__ request to check if movie rated with a comma in previous step.

__Use below path:__
```
account/:account_id/rated/movies?api_key={{apiKey}}&session_id={{sessionId}}
```

![image](https://user-images.githubusercontent.com/122685448/231307197-55f6a09f-f365-41f3-b168-0d20ee7e2751.png)
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__ and __{{accountId}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("The system has assigned a rate to the decimal comma: [" + jsonData.results[0].rating + "]", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(1);
});
```
In above code we are checking:

Response of status code must be 201 and that system take only first number before comma.

__Body response:__
![image](https://user-images.githubusercontent.com/122685448/231307215-23aa6bd9-98d6-4567-ad3a-e8ba07086799.png)

__Test response:__
![image](https://user-images.githubusercontent.com/122685448/231307230-f0a24a83-9bed-408f-a8e8-0ed2cb41ac0a.png)
 
