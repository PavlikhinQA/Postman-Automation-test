# [007] Get random Popular Movies
___

In this step, we will use GET request see all popular movies and choose six random of it.

__Use below path:__
```
movie/popular?api_key={{apiKey}}
```

In Query Params we use only apiKey.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});
const jsonData = pm.response.json();
const maxMovies = 6;

function setMovieId(index, varName) {
  const jsonData = pm.response.json();
  const movie = jsonData.results[index];
  pm.expect(movie).to.not.be.null;
  pm.expect(movie.id).to.be.a('number');
  pm.globals.set(varName, movie.id);
}

for (let i = 1; i <= maxMovies; i++) {
  const index = Math.trunc(Math.random() * jsonData.results.length);
  setMovieId(index, `movie${i}Id`);
}

for (let i = 1; i <= maxMovies; i++) {
  pm.test(`Created variable for Movie ${i}`, function () {
    const jsonData = pm.response.json();
    const expectedId = pm.globals.get(`movie${i}Id`);
    const movie = jsonData.results.find(m => m.id === expectedId);
    pm.expect(movie).to.not.be.null;
  });
}
```

In above code we are checking:

Response of status code must be 200. In addition, creating function on __JS__ to choose six random movies and create for each of them global variable with numbers.

So after pushing Send, we receive response in body with huge list:

![image](https://user-images.githubusercontent.com/122685448/231020668-083a63b0-0699-4fc4-868a-dfdac7a4810b.png)
![image](https://user-images.githubusercontent.com/122685448/231020682-7c95a187-3492-4bec-913b-065d5f7d43da.png)
![image](https://user-images.githubusercontent.com/122685448/231020691-8c297a02-90ec-4788-a0c2-62d3d2d2508c.png)
And we can find that we created new six variables:
 
![image](https://user-images.githubusercontent.com/122685448/231020697-8bac28fc-095d-4bc9-9fb1-f16cba54e89e.png)
