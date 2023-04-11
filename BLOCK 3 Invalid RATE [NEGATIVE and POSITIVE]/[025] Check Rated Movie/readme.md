# [025] Check Rated Movie
___

In this step, we will use __GET__ request to check that movie rated on previous step.

__Use below path:__
```
account/:account_id/rated/movies?api_key={{apiKey}}&session_id={{sessionId}}
```

![image](https://user-images.githubusercontent.com/122685448/231309179-6f43c177-0346-4347-8ead-1744f851df77.png)
 
In Query Params we use __{{apiKey}}__, __{{sessionId}}__ and __{{account_id}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Movie rated: [" + jsonData.results[0].rating + "]", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(1);
});
```

In above code we are checking:

Response of status code must be 200 and system rated correctly movie.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231309187-08ab2a88-a565-4725-9407-b4b6e7b81c4d.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231309194-0f8265df-388f-41db-8b32-b45293681689.png)
 


