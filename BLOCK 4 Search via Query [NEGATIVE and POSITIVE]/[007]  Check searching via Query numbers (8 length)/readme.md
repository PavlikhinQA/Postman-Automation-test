# [007]  Check searching via Query numbers (8 length)
___

In this step, we will create random number with 8 length in pre-request and search it via Query.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{randomNumber}}&page=1
```
![image](https://user-images.githubusercontent.com/122685448/231406177-25807c71-c3bd-45f2-a514-0e1409b38a99.png)
 
In Query Params we need __{{apiKey}}__, __{{randomNumber}}__ and page must be 1.

__Pre-request:__
``` js {.line-numbers}
let randomNumber = Math.floor(Math.random() * (99999999 - 10000000 + 1)) + 10000000;
pm.globals.set("randomNumber", randomNumber.toString());

```
In this code, we create random number with length 8 and create for it variable.

__Test code below:__
``` js {.line-numbers}
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Movie not found", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.total_results).to.eql(0);
});
```
In above code we are checking:

Response of status code must be 200 and checking that movie not found.

__Body response:__

![image](https://user-images.githubusercontent.com/122685448/231406220-aaad3c34-e4bf-42d3-9627-4b2fb92179a9.png)

__Test Response:__

![image](https://user-images.githubusercontent.com/122685448/231406252-137dbfd8-5641-4e03-aa9a-afd34fd8214f.png)
 
__Bellow created new variable with unreal word:__

![image](https://user-images.githubusercontent.com/122685448/231406274-4ac1eb18-749c-48a0-b9de-2ca7902b421f.png)
 

