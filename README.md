# Book API document - Khoalibary.com
## Books
### Books-Book-List
List all book


`GET`
```
/v1/books/
```
#### Header

Field | Type | Description
---------|----------|---------
 Accept-Language | String | User language

#### Parameters
No parametes
#### Success-Response
```json
HTTP/1.1 200 OK
{
  "data": [
    {
      "object": "Post",
      "id": "1",
      "name": "Python Learn The Hard way",
      "author": "Zed Shaw",
      "category": "education",
      "shelve_code": "2A1",
      "department_id": "Hà Nội",
      "is_borrowed": "True"
    },
    {
      "object": "Post",
      "id": "2",
      "name": "Python Crash Course: A Hands-On",
      "author": "Eric Matthes",
      "category": "education",
      "shelve_code": "2B2",
      "department_id": "Hồ Chí Minh",
      "is_borrowed": "False"
    },
    ...
  ],
  "meta": {
    "include": [
      "posts"
    ],
    "custom": [],
    "pagination": {
      "total": 7,
      "count": 7,
      "per_page": 10,
      "current_page": 1,
      "total_pages": 1,
      "links": {}
    }
  }
}
```
### Books-Book-Retrieve

Retrieve a single book

`GET`
```
/v1/books/:id
```
#### Header

Field | Type | Description
---------|----------|---------
 Accept-Language | String | User language
#### Parameters
Field | Type | Description
---------|----------|---------
 id | String | alphabets and numbers
 name | String | User language
 author | String | User language
 category | String | User language
 shelve_code | String | alphabets and numbers
 departmen_id | String | alphabets and numbers
 is_borrowed | Boolean | True or False
#### Success-Response
```json
HTTP/1.1 200 OK
{
  "data":{
    "object": "Post",
    "id": "1",
    "name": "Python Learn The Hard way",
    "author": "Zed Shaw",
    "category": "education",
    "shelve_code": "2A1",
    "department_id": "Hà Nội",
    "is_borrowed": "True"
    },
  "meta": {
    "include": [
      "books"
    ],
    "custom": []
  }
}
```

## Borrows
### Borrow-Borrwer-List
List Borrower

`GET`
```
/v1/borrows/name
```
#### Header
Field | Type | Description
---------|----------|---------
 Accept-Language | String | User language

#### Parameters
No parametes
#### Success-Response
```json
HTTP/1.1 200 OK
{
  "data": [
    {
      "object": "Post",
      "id": "1",
      "name": "Khoa",
      "book_id": "1",
      "accounts_id": "gcd0705",
      "day_borrow": "2020-03-19T16:46:33.000000Z",
      "day_return": "2020-03-31T14:07:46.000000Z",
      "is_expired": "True"
    },
    {
      "object": "Post",
      "id": "2",
      "name": "Kim Huong",
      "book_id": "2",
      "accounts_id": "gcd9109",
      "day-borrow": "2020-03-20T17:02:13.000000Z",
      "day-return": "2020-04-1T8:07:23.000000Z",
      "is_expired": "False"
    },
    ...
  ],
  "meta": {
    "include": [
      "borrows"
    ],
    "custom": [],
    "pagination": {
      "total": 7,
      "count": 7,
      "per_page": 10,
      "current_page": 1,
      "total_pages": 1,
      "links": {}
    }
  }
}
```
### Borrows-Borrower-Retrieve

Retrieve a single borrower

`GET`
```
/v1/borrows/name/:id
```
#### Header

Field | Type | Description
---------|----------|---------
 Accept-Language | String | User language
#### Parameters
Field | Type | Description
---------|----------|---------
 id | String | alphabets and numbers
 name | String | User language
 book_id | String | alphabets and numbers
 accounts_id | String | alphabets and numbers
 day_borrow | Datetime | YYYY-MM-DD
 day_return | Datetime | YYYY-MM-DD
 is_expired | Boolean | True or False
#### Success-Response
```json
HTTP/1.1 200 OK
{
  "data":{
    "object": "Post",
    "id": "1",
    "name": "Khoa",
    "book_id": "1",
    "accounts_id": "gcd0705",
    "day_borrow": "2020-03-19T16:46:33.000000Z",
    "day_return": "2020-03-31T14:07:46.000000Z",
    "is_expired": "True"
    },
  "meta": {
    "include": [
      "borrow"
    ],
    "custom": []
  }
}
```
### Borrow-Brrower-Create
Create new borrower


`POST`
```
/v1/borrows/new-borrower?[field]=[values]
```
Example: 
```
/v1/borrows/new-borrower?name=Khoa
```
#### Header

Field | Type | Description
---------|----------|---------
 Cookie | String | <calculated when request is sent>
 Token | String | <calculated when request is sent>
 Content-Type | String | application/json
 Content-Length | String | <calculated when request is sent>
 Host | String | <calculated when request is sent>
 Accept-Encoding | String | gzip, deflate, br
 Connection | String | keep-alive
#### Parameters
Field | Type | Description
---------|----------|---------
 name | String | User language
 book_id | String | alphabets and numbers
 accounts_id | String | alphabets and numbers
#### Success-Response
```json
HTTP/1.1 200 OK
{
    "args": {
        "name": "Khoa Huynh",
        "book_id": "1",
        "accounts_id": "gcd0705"
    },
    "data": {
        "method": "POST"
    },
    "headers": {
        "x-forwarded-proto": "https",
        "x-forwarded-port": "443",
        "host": "khoalibary.com",
        "x-amzn-trace-id": "Root=1-5f231a35-3d310456baf22caa7ff39fb8",
        "content-length": "21",
        "content-type": "application/json",
        "web-token": "96e0a497-3f9f-49ba-8ee4-3ba6bc9a7b01",
        "accept-encoding": "gzip, deflate, br",
        "cookie": "sails.sid=s%3AQq7Ohz-O6U3Tb86u6_kGH6Tga41MbwrE.A2Uf4pX7cKxM"
    },
    "json": {
        "method": "POST"
    },
    "url": "https://khoalibary.com/v1/borrows/new-borrower?name=Khoa%20Huynh&book_id=1&accounts_id=gcd0705"
}
```
## Accounts
### Accounts-Staff-Create
Create new staff account


`POST`
```
/v1/accounts/staff?[field]=[values]
```
Example: 
```
/v1/accounts/staff?name=gcd0705
```
#### Header

Field | Type | Description
---------|----------|---------
 Cookie | String | <calculated when request is sent>
 Token | String | <calculated when request is sent>
 Content-Type | String | application/json
 Content-Length | String | <calculated when request is sent>
 Host | String | <calculated when request is sent>
 Accept-Encoding | String | gzip, deflate, br
 Connection | String | keep-alive
#### Parameters
Field | Type | Description
---------|----------|---------
  name | String | User language, Lower case, no special characters
  password | String | passoword length min > 8 characters
  staff_id | String | 
#### Success-Response
```json
HTTP/1.1 200 OK
{
    "args": {
        "name": "khoadautay",
        "password": "khoa0305",
        "accounts_id": "gcd0705",
    },
    "data": {
        "method": "POST"
    },
    "headers": {
        "x-forwarded-proto": "https",
        "x-forwarded-port": "443",
        "host": "khoalibary.com",
        "x-amzn-trace-id": "Root=1-5f231a35-3d310456baf22caa7ff39fb8",
        "content-length": "21",
        "content-type": "application/json",
        "web-token": "96e0a497-3f9f-49ba-8ee4-3ba6bc9a7b01",
        "accept-encoding": "gzip, deflate, br",
        "cookie": "sails.sid=s%3AQq7Ohz-O6U3Tb86u6_kGH6Tga41MbwrE.A2Uf4pX7cKxM"
    },
    "json": {
        "method": "POST"
    },
    "url": "https://khoalibary.com/v1/accounts/staff?name=khoadautay&password=khoa0305&accounts_id=gcd0705"
}
```
### Accounts-Readers-Create
Create new reader account


`POST`
```
/v1/accounts/readers?[field]=[values]
```
Example: 
```
/v1/accounts/readers?name=gcd0705
```
#### Header

Field | Type | Description
---------|----------|---------
 Cookie | String | <calculated when request is sent>
 Token | String | <calculated when request is sent>
 Content-Type | String | application/json
 Content-Length | String | <calculated when request is sent>
 Host | String | <calculated when request is sent>
 Accept-Encoding | String | gzip, deflate, br
 Connection | String | keep-alive
#### Parameters
Field | Type | Description
---------|----------|---------
  name | String | User language, Lower case, no special characters
  password | String | passoword length min > 8 characters
  readers_id | String | 
#### Success-Response
```json
HTTP/1.1 200 OK
{
    "args": {
        "name": "readerkhoa",
        "password": "khoa2000",
        "accounts_id": "RHD7890",
    },
    "data": {
        "method": "POST"
    },
    "headers": {
        "x-forwarded-proto": "https",
        "x-forwarded-port": "443",
        "host": "khoalibary.com",
        "x-amzn-trace-id": "Root=1-5f231a35-3d310456baf22caa7ff39fb8",
        "content-length": "21",
        "content-type": "application/json",
        "web-token": "96e0a497-3f9f-49ba-8ee4-3ba6bc9a7b01",
        "accept-encoding": "gzip, deflate, br",
        "cookie": "sails.sid=s%3AQq7Ohz-O6U3Tb86u6_kGH6Tga41MbwrE.A2Uf4pX7cKxM"
    },
    "json": {
        "method": "POST"
    },
    "url": "https://khoalibary.com/v1/accounts/readers?name=readerkhoa&password=khoa2000&accounts_id=RHD7890"
}
```
