# [033] Check rated TV Show
___

In this GET request, we will find a list of all TV Shows with rates and will check that for __{{tv2Id}}__ will be rate 4.5, as created variable in previous step, also that only one rated movie.

__Use below path:__
```
account/:account_id/rated/tv?api_key={{apiKey}}&session_id={{sessionId}}
```

In Query Params we need __{{apiKey}}__, __{{sessionId}}__, and in the Path __{{account_id}}__.

__Test code below:__
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
var jsonData = pm.response.json();

pm.test("Checked that TV Show № " + pm.globals.replaceIn("{{tv2Id}}") + " has been rated", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.results[0].id).to.eql(parseInt(pm.globals.get("tv2Id")));
});
```

In above code we are checking:

Response of status code must be 200, checking that exactly tv2id was rated and that only one movie with rate.

Therefore, after pushing Send, we receive body response:
 
///***
In addition, test response:

