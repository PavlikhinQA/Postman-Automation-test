# [023] Get random Popular TV Show
___

In this GET request we will find 3 random TV Shows and will create for them variables.

__Use below path:__
```
tv/popular?api_key={{apiKey}}
```
![image](https://user-images.githubusercontent.com/122685448/231021938-e0fbd94b-a01e-4c90-b1f1-5721a4718e67.png)

In Query Params we need __{{apiKey}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});

const jsonData = pm.response.json();
const maxTv = 3;

function setTvId(index, varName) {
  const jsonData = pm.response.json();
  const tv = jsonData.results[index];
  pm.expect(tv).to.not.be.null;
  pm.expect(tv.id).to.be.a('number');
  pm.globals.set(varName, tv.id);
}

for (let i = 1; i <= maxTv; i++) {
  const index = Math.trunc(Math.random() * jsonData.results.length);
  setTvId(index, `tv${i}Id`);
}

for (let i = 1; i <= maxTv; i++) {
  pm.test(`Created variable for TV ${i}`, function () {
    const jsonData = pm.response.json();
    const expectedId = pm.globals.get(`tv${i}Id`);
    const tv = jsonData.results.find(m => m.id === expectedId);
    pm.expect(tv).to.not.be.null;
  });
}
```

In above code we are checking:

Response of status code must be 200, create function to create three variables of random TV Show and create for them numbers id.

Therefore, after pushing Send, we receive body response:
![image](https://user-images.githubusercontent.com/122685448/231021943-acefb599-42af-4624-a0af-59eb4c297a10.png)
![image](https://user-images.githubusercontent.com/122685448/231021949-e2744ccd-9993-4836-9e47-86216bf41cd5.png)
And test response:
![image](https://user-images.githubusercontent.com/122685448/231021959-1c7ee1e3-9a96-4868-911b-d67df47b25dd.png)

In addition, we can find new variables:
 
![image](https://user-images.githubusercontent.com/122685448/231021971-1454647e-4061-41b1-a1b6-a343814304d0.png)
