# [006]  Check searching via Query unreal word with numbers
___

In this step, we will create unreal word including numbers in pre-request and search it via Query.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{randomWordWithNumbers}}&page=1
```
///***
 
In Query Params we need __{{apiKey}}__, __{{randomWordWithNumbers}}__ and page must be 1.

__Pre-request:__
```
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
```
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
///***
 

__Test Response:__
///***
 

__Bellow created new variable with unreal word:__
///***
 

