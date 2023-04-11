# [001] Create Request Token
___
Before testing, we must have an account and must be authorized, but for exact negative testing, we will use fake value fro __[api_key]__
Below on the screen we can see the rest variables:
 
![image](https://user-images.githubusercontent.com/122685448/231304735-b2ca4717-1725-440d-a807-90826c9feaff.png)

In the authorization tab, we create Token with __Bearer Token__ – which we will not create.

Also must be known __User Name__, __Password__ and __Account Id__ – it will be real.

In addition, I created __{{baseUrl}}__ variable to easy future work. 

__Base url below:__

```
https://api.themoviedb.org/3/
```
So lest start testing. 

First need to send __GET__ request to create requestToken. 

__Use below path/query to base url:__
```
authentication/token/new?api_key=1234567890
```

You can find below parameters tab for such request:

![image](https://user-images.githubusercontent.com/122685448/231304790-9763042a-c2d5-4d27-b6c4-93e7b67fface.png)

__Code test:__
```js {.line-numbers}
pm.test("Status code is 401 - OK", function () {
    pm.response.to.have.status(401);
});

const response = pm.response.json();

pm.test("Token has not been created", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.success).to.eql(false);
});
```
In above code we are checking:

Response of status code must be 401. And Token must not create.

Therefore, after this we click on button Send, we will find bellow response:

Body response:

![image](https://user-images.githubusercontent.com/122685448/231304812-7a2343eb-8734-4926-a680-d2977dde95f1.png)

__Test response:__

![image](https://user-images.githubusercontent.com/122685448/231304819-1e05909a-38aa-4d5d-b65a-b2d9d30e8027.png)




