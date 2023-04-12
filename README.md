# Dear Friends!
---
### In this repository, I would like to provide my portfolio on automated API testing in Postman.

I got the API from the site [The Movie Database (TMDB)](https://www.themoviedb.org/)
After analyzing all the [API documentation](https://developers.themoviedb.org/3/getting-started/introduction) on this site, I decided to do some automated tests for checking correct response. I create four blocks with requests. Below you can see the description of the steps of it. The codes, screenshots and explaining of requests and response you can find in separate folders in this repository. In these folders, you can find some created function on JS in pre-request or in Test request. I will be glad if you can give me some feedback. I hope you will enjoy

>__First Block__
### POSITIVE

| [001] __GET__ Request to create [__request_token__] | [002] __POST__ Request to create session with Login |
| - | - |
| [003] __POST__ Request to create [__session_id__] | [004] __GET__ Request to get details of the account |
| [005] Create List with random number | [006] Get Details of the List |
| [007] Get random Popular Movies | [008-9-10] Add random movie № 1-2-3 to the List |
| [011] Check if movie 1 added to the list | [012] Get Details of the List with 3 movies|
| [013] Remove one movie from the List | [014] Get Details of the List with 2 movies |
| [015] Clear full list | [016] Get Details of the List - empty list |
| [017] Delete List -  [BUG] | [018] Check that list deleted | 
| [019] Add random movie to Watchlist | [020] Check that movie has been added to Watchlist | 
| [021] Remove Movie from Watchlist | [022] Check if Movie removed from Watchlist | 
| [023] Get random Popular TV Show| [024] Add random TV Show to Watchlist | 
| [025] Check that TV Show added to Watchlist | [026] Remove TV Show from Watchlist | 
| [027] Check that TV Show removed from Watchlist | [028] Rate random Movie | 
| [029] Check Rated Movie | [030] Delete Rate of the movie | 
| [031] Check that Rated Movies deleted | [032] Rate random TV Show | 
| [033] Check rated TV Show | [034] Delete Rate of TV Show | 
| [035] Check that Rate of TV Show deleted | [036] Mark random movie as Favorite | 
| [037] Check that movie added to Favorite | [038] Remove Movie from Favorite | 
| [039] Check that movie removed from Favorite | [040] Mark random TV Show as Favorite | 
| [041] Checked that TV Show add to Favorite | [042] Remove TV Show from Favorite | 
| [043] Check that TV Show removed from Favorite| [044] Delete Session | 
| [045] Check that sessisn has been deleted | | 

![1](https://user-images.githubusercontent.com/122685448/231402831-3a522a09-8f3d-46b6-b09f-7ded1bfb620f.gif)


>__Second Block__
### Invalid API key [NEGATIVE]

| [001] Create Request Token | [002] Create Session With Login |
| - | - |
| [003] Create Session | [004] Get Details of Account |
| [005] Create List with random number | [006] Get Details of the List |
| [007] Get random Popular Movies | [008] Get random Popular TV Show |
| [009] Add random TV Show to Watchlist | [010] Check that TV Show added to Watchlist |

![2023-04-11-04-44-22](https://user-images.githubusercontent.com/122685448/231403047-30582b91-218c-461d-8884-60f872708a92.gif)

>__Third Block__
### BLOCK 3 Invalid RATE [NEGATIVE and POSITIVE]

| [001] Create Request Token [POSITIVE] | [002] Create Session With Login [POSITIVE] |
| - | - |
| [003] Create Session [POSITIVE] | [004] Get Details of Account [POSITIVE] |
| [005] Get random Popular Movies [POSITIVE] | [006] Rate random Movie [NEGATIVE] number with a comma |
| [007] Check rate number with a comma | [008] Delete Rate of the movie |
| [009] Rate random Movie [NEGATIVE] not multiple of 0.50 | [010] Rate random Movie [NEGATIVE] text |
| [011] Rate random Movie [NEGATIVE] empty | [012] Rate random Movie [NEGATIVE] random sign (not letters, not numbers) |
| [013] Rate random Movie Boundary-value minus value  [NEGATIVE] | [014] Rate random Movie Boundary-value ZERO  [NEGATIVE] |
| [015] Rate random Movie Boundary-value 0.5 | [016] Check Rated Movie |
| [017] Delete Rate of the movie | [018] Rate random Movie Boundary-value 1 |
| [019] Check Rated Movie | [020] Delete Rate of the movie |
| [021] Rate random Movie Boundary-value 9.5 | [022] Check Rated Movie |
| [023] Delete Rate of the movie | [024] Rate random Movie Boundary-value 10 |
| [025] Check Rated Movie | [026] Delete Rate of the movie |
| [027] Rate random Movie [NEGATIVE] Boundary-value 10.5 | [028] Check Rated Movie |

![2023-04-11-21-07-30](https://user-images.githubusercontent.com/122685448/231403170-acc1fd6b-7341-4333-a08a-6136e68ec64f.gif)

>__Fourth Block__
### BLOCK 3 Invalid RATE [NEGATIVE and POSITIVE]


| [001] Get 3 random Movies | [002]  Check searching via Query chosen first movie |
| - | - |
| [003]  Check searching via Query chosen second movie | [004]  Check searching via Query chosen third movie |
| [005]  Check searching via Query unreal word | [006]  Check searching via Query unreal word with numbers |
| [007]  Check searching via Query numbers (8 length) | [008]  Check searching via Query numbers (2 length) |
| [009]  Check searching via Query signs !@#$%^&()_+-={}[];', | |

![2023-04-11-23-30-37](https://user-images.githubusercontent.com/122685448/231403234-64422351-fcbc-425c-a50d-9790a5f0666d.gif)

