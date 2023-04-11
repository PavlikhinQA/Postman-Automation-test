# [001] Get 3 random Movies
___

In this Block, we will test searching service via __Query requests__.
We need have account and must have authorization:
///***
///***
 

 
In this step we need to take random movies from popular list.
__Use below path:__
```
movie/popular?api_key={{apiKey}}
```
///***
 
In Query Params we need __{{apiKey}}__.
__Test code below:__
```
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const jsonData = pm.response.json();
const items = [];

for (let i = 0; i < 3; i++) {
  const index = Math.trunc(Math.random() * jsonData.results.length);
  const item = jsonData.results[index].original_title;
  items.push(item);
  pm.globals.set(`movie${i + 1}`, item);
}

for (let i = 0; i < 3; i++) {
  pm.test(`Created variable for Movie №${i + 1}: <<${pm.globals.get(`movie${i + 1}`)}>>`, function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.results.find(item => item.original_title === pm.globals.get(`movie${i + 1}`))).to.not.be.undefined;
  });
}
```
In above code we are checking:

Response of status code must be 200. Create function create names of variables for three random movies with its name.

__Body response:__
///***
 
__Test Response:__
///***
 
__New variables:__
///***
 
