# Veryfyd API

**BASE URL** `https://api.veryfyd.info/v1`


## Create User's Account

Create an Account for the authenticated User if an Account for that User does
not already exist. Each User can only have one Account.

**URL** : `/auth/signup`

**Method** : `POST`

**Request Body** :

| Field    | Description     | Required |
|----------|-----------------|----------|
| name     | String          | true     |
| email    | valid email     | true     |
| password | minimum 6 chars | true     |


Sample Request

```json
{
    "name": "ABC Technologies",
    "name": "abc@tech.com",
    "password": "password"
}
```

**Sample Response**
```json
{
    "user": {
        "name": "ABC Technologies",
        "email": "abc@tech.com",
        "apiKey": "9dbf585a-680e-43f7-b074-528b749c498b",
        "requestCount": 0
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MTQxOTY4NGI1NzQ3MDQ1OWYwZGY4NmQiLCJpYXQiOjE2MzE2ODgzMjUsImV4cCI6MTY2MzIyNDMyNX0.cu2RShELfTVGuBaOc7Z5DInJ3dCTtAayeWo8kdBnxow"
}
```

## Success Response

**Condition** : If everything is OK and an Account didn't exist for this User.

**Code** : `201 CREATED`

**Content example**

```json
{
    "id": 123,
    "name": "Build something project dot com",
    "url": "http://testserver/api/accounts/123/"
}
```

## Error Responses

**Condition** : If Account already exists for User.

**Code** : `303 SEE OTHER`

**Headers** : `Location: http://testserver/api/accounts/123/`

**Content** : `{}`

### Or

**Condition** : If fields are missed.

**Code** : `400 BAD REQUEST`

**Content example**

```json
{
    "name": [
        "This field is required."
    ]
}
```
