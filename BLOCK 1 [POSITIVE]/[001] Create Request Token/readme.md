# [001] GET Request to create {{request_token}}

Before testing, we must have an account and must be authorized.

Below on the screen we can see the following variables:

![image](https://user-images.githubusercontent.com/122685448/231020070-ba29acb2-390c-4ae4-b375-70c46145f1c6.png)


![image](https://user-images.githubusercontent.com/122685448/231019891-b0461aaf-e332-4571-8a08-9d3221edbdc3.png)



In the authorization tab, we create Token with Bearer Token.

In Variables tab, we must create apiKey for Bearer Token. Also must be known User Name, Password and Account Id.

In addition, I created baseUrl variable to easy future work. Base url below:

```
https://api.themoviedb.org/3/
```
So lets start testing. 

First need to send GET request to create __{{requestToken}}__. 
Use below path/query to base url:
```
/authentication/token/new?api_key={{apiKey}} 
```
You can find below parameters tab for such request:

![image](https://user-images.githubusercontent.com/122685448/231019920-b66e9b6e-04a2-4f30-b71d-01c83108e448.png)


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
__In above code we are checking:__
Response of status code must be 200.

Creating Variable __{{requestToken}}__, which will use in next requests and checking that it created.

So after this we click on button __Send__, I find bellow response:
__Body:__

![image](https://user-images.githubusercontent.com/122685448/231019941-8e96baad-93fa-4001-ab44-a90318ad0b61.png)

__Test Results:__

![image](https://user-images.githubusercontent.com/122685448/231019969-fb72baec-7eb7-4719-aed8-c29656f97fa9.png)


After if we can find in Environment tab, that variable __{{requestToken}}__ was created.
![image](https://user-images.githubusercontent.com/122685448/231019980-fd6b8649-1fd5-4baf-89ae-7555625e3f01.png)





