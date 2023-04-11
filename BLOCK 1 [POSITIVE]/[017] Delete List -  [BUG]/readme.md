# [017] Delete List - > [BUG]
___

This step we will DEL request to delete list

__Use below path:__
```
list/:list_id?api_key={{apiKey}}&session_id={{sessionId}}
```
![image](https://user-images.githubusercontent.com/122685448/231021411-d50339ff-9197-4114-b6bb-d2532e6ba6c4.png)

In Query Params we need __{{apiKey}}__, __{{sessionId}}__ and in Path __{{listId}}__.

__Test code below:__
```js {.line-numbers}
pm.test("Status code is 201 - OK", function () {
    pm.response.to.have.status(201);
});
```

In above code we are checking only that status code of response must be 200
 

So after pushing __Send__ we receiving response whith __status code 500__ and in body:
```
{ "success": false}
```

But must be 201, bellow you can find link for documentation of this situation, so we found __BUG__ in API response.
```
https://developers.themoviedb.org/3/lists/delete-list
```
 
![image](https://user-images.githubusercontent.com/122685448/231021496-5cae8a7a-30cf-4bc7-baaa-49596d58edf5.png)

And test response:

![image](https://user-images.githubusercontent.com/122685448/231021506-a8a6cd61-a279-4607-8e78-93ee285932a9.png)
 



