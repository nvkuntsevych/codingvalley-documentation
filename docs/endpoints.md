# Media  

https://codingvalley.tech/watchlists/search/ - GET  

Using:  
Get paginated list of movies or series by title or part of title with 
filtering by release year.  

Query parameters:  

| Parameter | Required | Description |
| --------- | -------- | ----------- |
| search | Yes | Title or part of title to search for |
| year | No | Year of release |
| page | No | Number of page to return(1 by default) |

***

https://codingvalley.tech/watchlists/get/ - GET  

Using:  
Get specific movie or series by IMDb ID.  

Query parameters:  

| Parameter | Required | Description |
| --------- | -------- | ----------- |
| imdb_id | Yes | IMDb ID of movie of series |
| type | Yes | Media type(Either movie or series) |
| imdb_rating | No | Minimum media rating(any rating by default) |

***

https://codingvalley.tech/watchlists/get/season/ - GET  

Using:  
Get specific season of the series by series IMDb ID and season number with 
filtering by episode imdb_rating.  

Query parameters:  

| Parameter | Required | Description |
| --------- | -------- | ----------- |
| imdb_id | Yes | IMDb ID of series |
| season | Yes | Season number |
| imdb_rating | No | Minimum episodes rating(any rating by default) |

***

https://codingvalley.tech/watchlists/recently_searched/ - GET  

Using:  
Get paginated list of movies or series sorted by receiving time.  

Query parameters:  
No any query parameters are required.  

***

## Discussion  

Description:  
Discussion objects represent discussions about any topics;  

Endpoints:  

| URL | HTTP Method | Description |
| ---- | ------ | ----------- |
| https://codingvalley.tech/discussions/ | GET | get list of discussions |
| https://codingvalley.tech/discussions/ | POST | create a discussion |
| https://codingvalley.tech/discussions/<id\>/ | GET | retrieve specific discussion |
| https://codingvalley.tech/discussions/<id\>/ | PUT/PATCH | update specific discussion |
| https://codingvalley.tech/discussions/<id\>/ | DELETE | delete specific discussion |

Permissions:  
POST - only for authenticated users;  
PUT/PATCH, DELETE - only for onner and admins.  

***

## Comment  

Description:  
Comment objects represent comments to a specific discussion;  

Endpoints:  

| URL | HTTP Method | Description |
| ---- | ------ | ----------- |
| https://codingvalley.tech/comments/ | POST | create a comments |
| https://codingvalley.tech/comments/<id\>/ | PUT/PATCH | update specific comments |
| https://codingvalley.tech/comments/<id\>/ | DELETE | delete specific comments |

Permissions:  
POST - only for authenticated users;  
PUT/PATCH, DELETE - only for onner and admins;  

Notes:  
The list of comments is retrieved for the specific Discussion object.  

***

## Review  

Description:  
Review objects represent review to a specific movie or series;  

Endpoints:  

| URL | HTTP Method | Description |
| ---- | ------ | ----------- |
| https://codingvalley.tech/reviews/ | POST | create a reviews |
| https://codingvalley.tech/reviews/<id\>/ | PUT/PATCH | update specific reviews |
| https://codingvalley.tech/reviews/<id\>/ | DELETE | delete specific reviews |

Permissions:  
POST - only for authenticated users;  
PUT/PATCH, DELETE - only for onner and admins;  

Notes:  
The list of reviews is retrieved for the specific Media object.  

***

## ReviewsLike  

Description:  
ReviewsLike objects represent a bundle user-review in order to user can not add several likes for the same review;  

Endpoints:  

| URL | HTTP Method | Description |
| ---- | ------ | ----------- |
| https://codingvalley.tech/reviewlikes/ | POST | create a reviewlikes |
| https://codingvalley.tech/reviewlikes/<id\>/ | DELETE | delete specific reviewlikes |

Permissions:  
POST - only for authenticated users;  
DELETE - only for onner and admins;  

***

# Registration and authentication  

Endpoints:  

| URL | HTTP Method | Description |
| ---- | ------ | ----------- |
| https://codingvalley.tech/users/register/ | POST | create new user and get access and refresh tokens |
| https://codingvalley.tech/users/login/ | POST | get access and refresh tokens |
| https://codingvalley.tech/users/logout/ | POST | add given refresh token to blacklist |
| https://codingvalley.tech/users/logout/all/ | POST | add all the user's refresh tokens to blacklist |
| https://codingvalley.tech/users/login/refresh/ | POST | get new refresh token, given refresh token is added to blacklist |
| https://codingvalley.tech/users/login/google/ | POST | get access tokens by given google's token |

***

# User account

Endpoints:  

| URL | HTTP Method | Description |
| ---- | ------ | ----------- |
| https://codingvalley.tech/users/account/email/activate/ | POST | send an email to verify email address of current user |
| https://codingvalley.tech/users/account/activate/<uidb64\>/<token\> | GET | vefify email of current user |
| https://codingvalley.tech/users/account/password/reset/ | POST | send an email to reset password of current user |
| https://codingvalley.tech/users/account/reset/<uidb64\>/<token\> | POST | reset password of current user |
| https://codingvalley.tech/users/account/change_password/ | PUT/PATCH | change password of current user |

***

# User profile

Endpoints:  

| URL | HTTP Method | Description |
| ---- | ------ | ----------- |
| https://codingvalley.tech/users/user/<username\>/ | GET | retrieve profile of user with `username` username |
| https://codingvalley.tech/users/user/<username\>/follow/ | POST | start of stop following user with `username` username |
| https://codingvalley.tech/users/<uuid\>/save/ | POST | add media with `uuid` id to the favorites |
| https://codingvalley.tech/users/profile/edit/ | PUT/PATCH | update user profile |

***
