# Twitter
API 1
Path: /register/
Method: POST
Request

{
  "username": "adam_richard",
  "password": "richard_567",
  "name": "Adam Richard",
  "gender": "male"
}
Scenario 1

Description:

If the username already exists

Response

Status code
400
Body
User already exists
Scenario 2

Description:

If the registrant provides a password with less than 6 characters

Response

Status code
400
Body
Password is too short
Scenario 3

Description:

Successful registration of the registrant

Response

Status code

200
Body

User created successfully


API 2
Path: /login/
Method: POST
Request

{
  "username":"JoeBiden",
  "password":"biden@123"
}
Scenario 1

Description:

If the user doesn't have a Twitter account

Response

Status code
400
Body
Invalid user
Scenario 2

Description:

If the user provides an incorrect password

Response

Status code
400
Body
Invalid password
Scenario 3

Description:

Successful login of the user

Response

Return the JWT Token

{
  "jwtToken": "ak2284ns8Di32......"
}
Authentication with JWT Token
Write a middleware to authenticate the JWT token.

Scenario 1

Description:

If the JWT token is not provided by the user or an invalid JWT token is provided

Response

Status code
401
Body
Invalid JWT Token
Scenario 2

After successful verification of JWT token, proceed to next middleware or handler



API 3
Path: /user/tweets/feed/
Method: GET
Description:
Returns the latest tweets of people whom the user follows. Return 4 tweets at a time

Response
 [
   {
      username: "SrBachchan",
      tweet: "T 3859 - do something wonderful, people may imitate it ..",
      dateTime: "2021-04-07 14:50:19"
   },
   ...
 ]



API 4
Path: /user/following/
Method: GET
Description:
Returns the list of all names of people whom the user follows

Response
[
  {
    "name": "Narendra Modi"
  },
  ...
]


API 5
Path: /user/followers/
Method: GET
Description:
Returns the list of all names of people who follows the user

Response
[
  {
    "name": "Narendra Modi"
  },
  ...
]


API 6
Path: /tweets/:tweetId/
Method: GET
Scenario 1

Description:

If the user requests a tweet other than the users he is following

Response

Status code
401
Body
Invalid Request
Scenario 2

Description:

If the user requests a tweet of the user he is following, return the tweet, likes count, replies count and date-time

Response

{
   "tweet": "T 3859 - do something wonderful, people may imitate it ..",
   "likes": 3,
   "replies": 1,
   "dateTime": "2021-04-07 14:50:19"
}



API 7
Path: /tweets/:tweetId/likes/
Method: GET
Scenario 1

Description:

If the user requests a tweet other than the users he is following

Response

Status code
401
Body
Invalid Request
Scenario 2

Description:

If the user requests a tweet of a user he is following, return the list of usernames who liked the tweet

Response

{
   "likes": ["albert", ]
}



API 8
Path: /tweets/:tweetId/replies/
Method: GET
Scenario 1

Description:

If the user requests a tweet other than the users he is following

Response

Status code
401
Body
Invalid Request
Scenario 2

Description:

If the user requests a tweet of a user he is following, return the list of replies.

Response

```
{
   "replies": [
     {
       "name": "Narendra Modi",
       "reply": "When you see it.."
      },
    ...]
}
```



API 9
Path: /user/tweets/
Method: GET
Description:
Returns a list of all tweets of the user

Response
[
  {
    "tweet": "Ready to don the Blue and Gold",
    "likes": 3,
    "replies": 4,
    "dateTime": "2021-4-3 08:32:44"
  },
  ...
]



API 10
Path: /user/tweets/
Method: POST
Description:
Create a tweet in the tweet table

Request
{
   "tweet": "The Mornings..."
}
Response
Created a Tweet
API 11
Path: /tweets/:tweetId/
Method: DELETE
Scenario 1

Description:

If the user requests to delete a tweet of other users

Response

Status code
401
Body
Invalid Request
Scenario 2

Description:

If the user deletes his tweet

Response

Tweet Removed
