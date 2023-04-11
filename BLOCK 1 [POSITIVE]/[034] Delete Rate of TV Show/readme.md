# [034] Delete Rate of TV Show
___

In this DEL request, we will delete rate for TV Show.

__Use below path:__
```
tv/:tv_id/rating?api_key={{apiKey}}&session_id={{sessionId}}
```
///***
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
 
///***
In addition, __test response:__
///***
