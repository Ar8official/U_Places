<p align="center">
  <a href="" rel="noopener">
 <img width=200px src="favicon.png" alt="Project logo"></a>
</p>

<h3 align="center">Uplaces</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

</div>

## ?? Table of Contents

- [About](#about)
- [Prerequisites](#prerequisites)
- [Documentation](#documentation)

## ?? About <a name = "about"></a>

This is the Nodejs backend for the react and node fullstack app.
React frontend code is available (here)[https://github.com/Ar8official/U-Places]

## Prerequisites

You will need to have [Nodejs](https://nodejs.org/en/) in your system.

## ?? Documentation <a name = "documentation"></a>

### JSON Objects returned by API:

Make sure the right content type like `Content-Type: application/json; charset=utf-8` is correctly returned.

#### Users (for authentication)

```JSON
{
  "user": {
    "name": "Borguuh",
    "email": "test@test.com",
    "token": "jwt.token.here",
    "image": "https://static.productionready.io/images/smiley-cyrus.jpg",
  }
}
```
#### User (Object Model)

```JSON
{
  "user": {
  	"userId": "u1",
    "name": "jake",
    "email": "test@test.com",
    "image": "https://static.productionready.io/images/smiley-cyrus.jpg",
  }
}
```

#### Place

```JSON
{
  "place": {
  	"id": "p1",
    "title": "Trenchard Hall, University Of Ibadan.",
    "description": "The best university hall to host your memorable events for students to link up and share some good time together.",
    "image": "https://static.productionready.io/images/smiley-cyrus.jpg",
    "address": "Mellanby Hall Road, 200132, University Of Ibadan, Ibadan",
    "location": {
    	"lat": 4,
    	"lng": 2.5
    },
    "creator": {
      "userId": "u1",
      "username": "jake",
      "image": "https://i.stack.imgur.com/xHWG8.jpg",
  }
}
```
#### Errors and Status Codes

If a request fails any validations, expect a 422 and errors in the following format:

```JSON
{
  "errors":{
    "body": [
      "can't be empty"
    ]
  }
}
```

##### Other status codes:

401 for Unauthorized requests, when a request requires authentication but it isn't provided

403 for Forbidden requests, when a request may be valid but the user doesn't have permissions to perform the action

404 for Not found requests, when a resource can't be found to fulfill the request

### Endpoints:

#### Retrieve list of all users
`GET /api/users/`

No authentication required, returns a list of all users

#### Authentication:

`POST /api/users/login`

Example request body:
```JSON
{
  "user":{
    "email": "jake@jake.jake",
    "password": "jakejake"
  }
}
```

No authentication required, returns a [User](#users-for-authentication)

Required fields: `email`, `password`


#### Registration:

`POST /api/users/signup`

Example request body:
```JSON
{
  "user":{
    "username": "Jacob",
    "email": "jake@jake.jake",
    "password": "jakejake"
  }
}
```

No authentication required, returns a [User](#users-for-authentication)

Required fields: `email`, `username`, `password`


#### Get List of all places by a given User

`GET /api/places/user/:uid`

No authentication required, returns a list of all places by a given User


### Get Place

`GET /api/places/:pid`

No authentication required, will return [single place](#single-place)

### Create Place

`POST /api/places/`

Example request body:

```JSON
{
  "place": {
    "title": "How to train your dragon",
    "description": "Ever wonder how?",
    "image": "https://static.productionready.io/images/smiley-cyrus.jpg",
    "address": "Mellanby Hall Road, 200132, University Of Ibadan, Ibadan",

  }
}
```

Authentication required, will return an [place](#single-place)

Required fields: `title`, `description`, `image`, `address`


### Update Place

`PUT /api/places/:pid`

Example request body:

```JSON
{
  "place": {
    "title": "Amphitheater"
  }
}
```

Authentication required, returns the updated [place](#single-place)

Optional fields: `title`, `description`, `address`, `image`


### Delete Place

`DELETE /api/places/:pid`

Authentication required

Check the documentation to install it on your system.
