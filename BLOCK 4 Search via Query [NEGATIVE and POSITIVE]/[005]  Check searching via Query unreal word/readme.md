# [005] Check searching via Query unreal word
___

In this step, we will create unreal word in pre-request and search it via Query.

__Use below path:__
```
search/movie?api_key={{apiKey}}&query={{unrealWord}}&page=1
```
///***
 
In Query Params we need __{{apiKey}}__, __{{unrealWord}}__ and page must be 1.

__Pre-request:__
```
function randomWord(length) {
    var vowels = "aeiou";
    var consonants = "bcdfghjklmnpqrstvwxyz";
    var word = "";
    var i;

    for (i = 0; i < length; i++) {
        if (i % 2 === 0) {
            word += consonants.charAt(Math.floor(Math.random() * consonants.length));
        } else {
            word += vowels.charAt(Math.floor(Math.random() * vowels.length));
        }
    }

    return word;
}

var randomEnglishWord = randomWord(7);
pm.globals.set("unrealWord", randomEnglishWord);

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
 

