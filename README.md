Hint API
==========

API specification for the hint API 
<br>
<br>
<br>

## Authetication
<br>
I'm going to send the API key as an Authorization header in the Http request on every request

`Authorization=<API key>`
<br>
<br>

## Creating a user

<br>

I'm going to send POST request to the `/user` endpoint
<br>

`[POST] /user`

<br>

### Request Body
```json
{
    "uName": "username",
    "uMail": "userEmail",
    "uPhone": "User phone number"
}
```
<br>

### Expected response (success)

<br>

Code:
`201` (created)

<br>

### Response Body

<br>

```json
{
    "uId": "userID"
}
```
<br>

### Expected response (Duplicate user)

<br>

Code:
`409` (conflict)

<br>

### Response Body

<br>
<br>

```json
{
    "message": "User exists"
}
```

<br>
<br>

## Modify User Proferences

<br>

`[POST] /modify-preferences/:userId`

<br>

### Request Body

<br>

```json
[ "Male", "Female", "Neflix", "Light Comedy"  ] // Any Key word from the keywords array
```

<br>

### Response

<br>

`200` (OK)

<br>

## Save feedback

<br>

`[POST] /save-feedback`

<br>

### Request Body
<br>

```json
    {
        "movieID": "tt304958658"
        "feedback": "LIKE" // Possibilities [LIKE, DISLIKE, SHOW_MORE, SHOW_LESS, SEEN]
    }
```
<br>

### Expected response (Recommend movie)

<br>

Code:
`204` (No Content)

## Get movie recommendation for user

<br>

`[GET] /recommend/:userId`

<br>

### Expected response

Code:
`200` (OK)

```json
    {
        "movieID": "tt304958658",
        "name": "Movie name",
        "imageUrl": "Image url",
        "triggers": ["Male", "Female", "Neflix", "Light Comedy"],
        "durationMins": 120,
        "editorial": "This is a great movie"
    }
```

<br>

