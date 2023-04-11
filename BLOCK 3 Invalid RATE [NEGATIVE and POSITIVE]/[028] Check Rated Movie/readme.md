# [028] Check Rated Movie
___

In this step, we will use __GET__ request to check that movie rated on previous step or not.

__Use below path:__
```
account/:account_id/rated/movies?api_key={{apiKey}}&session_id={{sessionId}}
```

![image](https://user-images.githubusercontent.com/122685448/231309488-df25a7ba-115b-4212-b3cb-b6ae55de2b39.png)
 
In Query Params we use __{{apiKey}}__,__{{sessionId}}__ and __{{account_id}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();

pm.test("No rated movies", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(0);
});

pm.globals.clear();
```

In above code we are checking:

Response of status code must be 200 and system must inform that there is no rated movie. Also, delete all global variables.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231309512-0e2d1551-c88f-4798-be0c-da2f50fa92b6.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231309516-aa79a55d-9071-477a-8074-3324b469aee0.png)

__Cleaned all variables:__

![image](https://user-images.githubusercontent.com/122685448/231309524-b79c1705-3498-47a6-b8fe-67b630b789d0.png)

 


