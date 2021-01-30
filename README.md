# Denis Chernyavsky, first REST application

## Description

Rest application for library, where:

- User can get list of available books.
- User can reserve a book for himself (after the book reserved no one can see the book in list).
- User has personal account with info about reserved books.
- Registration by email and password.

Books a stored in the database (I'll add the route to schema and storage). Only authorized user can reserve a book from
list.

## User stories

### 1) As a User, I want to create an account.

Request:
`POST v1/FirstSpringApp/reader/sign-up`

```json
[
  {
    "email": "ivan@gamil.com",
    "password": "qwerty",
    "fullName": "John Paul Johnson",
    "gender": "male"
  }
]
```

Response:
`201 CREATED`

```json
[
  {
    "id": 1
  }
]
```

### 2) As a User, I want to log in system. If such user exist - then the user enter in system

Request:
`POST v1/FirstSpringApp/reader/sign-in`

```json
[
  {
    "email": "ivan@gmail.com",
    "password": "qawsedrf"
  }
]
```

Response:
`200 OK`

```json
[
  {
    "id": 1
  }
]
```

### 3) As a User, I want to get the list of available book for reservation.

Request:
`POST v1/FirstSpringApp/book/list`

Response:
`200 OK`

```json
[
  {
    "id": 1,
    "name": "For whom the bell tools",
    "author": "Ernest Hemingway",
    "reserved": false,
    "holder_user_id": null
  },
  {
    "id": 2,
    "name": "It",
    "author": "Stephan King",
    "reserved": true,
    "holder_user_id": 1
  }
]
```

### 4) As a User, I want to check out a page about book and reserve this one.

Request:
`PATCH v1/FirstSpringApp/book/${bookId}/reserve`
```json
[
  {
    "reserved": true
  }
]
```

Response:
`204 No Content`
