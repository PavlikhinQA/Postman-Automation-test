# [005] Get random Popular Movies [POSITIVE]
___

In this step, we will use __GET__ request see all popular movies and choose 12 random of it.

__Use below path:__
```
movie/popular?api_key={{apiKey}}
```
![image](https://user-images.githubusercontent.com/122685448/231306964-2edd32ca-1607-4478-a691-03b1a7370bf4.png)
 
In Query Params we use only __{{apiKey}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 200 - OK", function () {
    pm.response.to.have.status(200);
});
const jsonData = pm.response.json();
const maxMovies = 12;

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

Response of status code must be 200. In addition, creating function on __JS__ to choose 12 random movies and create for each of them global variable with numbers.

So after pushing __Send__, we receive response in body with huge list:

![image](https://user-images.githubusercontent.com/122685448/231307021-cbf70ccc-abe3-4f0a-a057-7113c29bd554.png)
![image](https://user-images.githubusercontent.com/122685448/231307035-5783fc0e-0575-4947-af71-64298f4088ca.png)

 
In addition, we can find that we created new 12 variables:

![image](https://user-images.githubusercontent.com/122685448/231307044-5ab36845-94cd-4207-95ca-f6f07b2eee2f.png)

