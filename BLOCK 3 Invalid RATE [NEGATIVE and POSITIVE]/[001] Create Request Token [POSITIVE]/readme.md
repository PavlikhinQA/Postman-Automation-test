# [001] Create Request Token [POSITIVE]
___

First five steps will be positive with real values and equal as in Block # 1. 

The main idea of this Block is check if system will correctly response on incorrectly values, but before it in first five steps, we will do all standard steps.

As you, remember we must have an account and must be authorize. Just for remind pls see below screens:
///***
///***
 
 

__Base url below:__
```
https://api.themoviedb.org/3/
```

So lest start testing. 

First need to send __GET__ request to create __{{requestToken}}__. 

__Use below path/query to base url:__
```
/authentication/token/new?api_key={{apiKey}} 
```

You can find below parameters tab for such request:
///***
 
__Code test:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
pm.globals.set("requestToken", response.request_token);

pm.test("Token has been created successfully", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(true);
});
```

In above code we are checking:

Response of status code must be 200.

Creating Variable __{{requestToken}}__, which will use in next requests and checking that it created.

So after this we click on button __Send__, I find bellow response:

__Body:__
///***
 
__Test Results:__
///***
 
After if we can find in Environment tab, that variable __{{requestToken}}__ created.
///***
 





