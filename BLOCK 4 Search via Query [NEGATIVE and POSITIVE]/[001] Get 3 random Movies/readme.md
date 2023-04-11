# [001] Get 3 random Movies
___

In this Block, we will test searching service via __Query requests__.
We need have account and must have authorization:

![image](https://user-images.githubusercontent.com/122685448/231309874-22cfc6c9-3bc0-439d-b718-ec471517745a.png)
![image](https://user-images.githubusercontent.com/122685448/231309878-3642aab1-0544-43c9-bbcb-a6b95fe10514.png)
 
In this step we need to take random movies from popular list.
__Use below path:__
``` 
movie/popular?api_key={{apiKey}}
```
![image](https://user-images.githubusercontent.com/122685448/231309921-7909088a-4400-45da-958d-42c09cebd25d.png)
 
In Query Params we need __{{apiKey}}__.
__Test code below:__
```js {.line-numbers}
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

![image](https://user-images.githubusercontent.com/122685448/231309929-f7fc26c5-4a49-46b5-9ae8-4bd5a6e54594.png)
 
__Test Response:__

![image](https://user-images.githubusercontent.com/122685448/231309935-cd604781-a5f8-4f49-8489-2ccd33524cae.png)
 
__New variables:__

![image](https://user-images.githubusercontent.com/122685448/231309943-e0cbfa02-332f-41bd-87d2-d12abda1f2b2.png)
 
