# [008]  Check searching via Query numbers (2 length)
___

In this step, we will create random number with 2 length in pre-request and search it via Query.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{randomNumber2}}&page=1\
```
![image](https://user-images.githubusercontent.com/122685448/231406494-be7abde6-7e1a-4330-9313-4e9b74ce2467.png)
 

In Query Params we need __{{apiKey}}__, __{{randomNumber2}}__ and page must be 1.

__Pre-request:__
``` js {.line-numbers}
let randomNumber = Math.floor(Math.random() * 100).toString().padStart(2, '0');
pm.globals.set('randomNumber2', randomNumber);

```
In this code, we create random number with length 2 and create for it variable.

__Test code below:__
``` js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Movie was found", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).not.eql(0);
});
```
In above code we are checking:

Response of status code must be 200 and checking that movie found.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231406524-11f2b48b-606a-4e0e-b9ff-afc05f070d34.png)
 
__Test Response:__

![image](https://user-images.githubusercontent.com/122685448/231406542-fe3a4bc9-f274-4a68-ae29-61044610f7ae.png)
 
__Bellow created new variable with unreal word:__

![image](https://user-images.githubusercontent.com/122685448/231406572-472f098b-dc60-492b-8a6b-4ff9db23fcf3.png)
 

