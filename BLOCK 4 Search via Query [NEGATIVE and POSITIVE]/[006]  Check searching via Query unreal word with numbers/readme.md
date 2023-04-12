# [006]  Check searching via Query unreal word with numbers
___

In this step, we will create unreal word including numbers in pre-request and search it via Query.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{randomWordWithNumbers}}&page=1
```
![image](https://user-images.githubusercontent.com/122685448/231405882-68aec0ce-56bf-49fb-97e0-1d9bd962dcd0.png)
 
In Query Params we need __{{apiKey}}__, __{{randomWordWithNumbers}}__ and page must be 1.

__Pre-request:__
``` js {.line-numbers}
const letters = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';
const numbers = '0123456789';
let randomWord = '';

for(let i = 0; i < 8; i++) {
  if(i % 2 === 0) {
    randomWord += letters.charAt(Math.floor(Math.random() * letters.length));
  } else {
    randomWord += numbers.charAt(Math.floor(Math.random() * numbers.length));
  }
}

pm.globals.set('randomWordWithNumbers', randomWord);
```

In this code, we create function to create unreal word with length 7 and create for it variable.

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

![image](https://user-images.githubusercontent.com/122685448/231405929-7093d8e8-b5b0-48e2-901d-c8e97008c11a.png)
 
__Test Response:__

![image](https://user-images.githubusercontent.com/122685448/231405961-5d05df27-922b-4d7e-9ba5-b53e30ac2e63.png)
 
__Bellow created new variable with unreal word:__

![image](https://user-images.githubusercontent.com/122685448/231405983-4ded0208-8d2b-4313-afa5-3bbd822e97b4.png)
 

