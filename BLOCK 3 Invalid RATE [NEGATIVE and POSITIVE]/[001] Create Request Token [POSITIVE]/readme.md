# [001] Create Request Token [POSITIVE]
___

First five steps will be positive with real values and equal as in Block # 1. 

The main idea of this Block is check if system will correctly response on incorrectly values, but before it in first five steps, we will do all standard steps.

As you, remember we must have an account and must be authorize. Just for remind pls see below screens:

![image](https://user-images.githubusercontent.com/122685448/231306489-1a01dfcb-02a7-4eef-937d-84bd309c32f3.png)
![image](https://user-images.githubusercontent.com/122685448/231306496-b274d0f2-6c56-4629-8d8e-450d0f87bc96.png)
 
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
![image](https://user-images.githubusercontent.com/122685448/231306530-cdf63cbe-64da-49e0-8544-2f130a84ace2.png)
 
__Code test:__
```js {.line-numbers}
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

![image](https://user-images.githubusercontent.com/122685448/231306545-487b28cd-8968-40cb-b8d6-fe7df38c6221.png)
 
__Test Results:__

![image](https://user-images.githubusercontent.com/122685448/231306556-dfd620c8-b922-4b76-9997-b30602c5797d.png)
 
After if we can find in Environment tab, that variable __{{requestToken}}__ created.

![image](https://user-images.githubusercontent.com/122685448/231306567-6206a25c-8a52-4bcf-a582-4959c547fa14.png)
 





