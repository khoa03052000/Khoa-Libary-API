# Book API document - Khoalibary.com

## Resource
### The main entities/resources served by the API are
- Books
- Borrow
### Each resource managed by implementing the two main HTTP methods
- `GET` for getting all elements or searching if query specified or getting specified element if the id specified.
- `POST` for adding new element to the collection.
### HTTP status codes
- `200` - Success.
- `201` - Created. Returned on successful creation of a new resource. Include a 'Location' header with a link to the newly-created resource.
- `400` - Bad request. Data issues such as invalid JSON, etc.
- `404` - Not found. Resource not found on GET.
- `409` - Conflict. Duplicate data or invalid data state would occur.
## Accessing the API
### Books
#### Books - List
- List all book


`GET`
```
api/v1/books/
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
  "data":
    {
      "id": "1",
      "name": "Python Learn The Hard way",
      "author": "Zed Shaw",
      "category": "education",
      "shelve_code": "2A1",
      "department_id": "HN",
      "created_at": "2020-03-31T13:51:32",
      "updated_at": "2020-03-31T13:51:32",
      "delete_at": ""
    },
    {
      "id": "2",
      "name": "Python Crash Course: A Hands-On",
      "author": "Eric Matthes",
      "category": "education",
      "shelve_code": "2B2",
      "department_id": "Hồ Chí Minh",
      "created_at": "2020-03-13T14:12:32",
      "updated_at": "",
      "delete_at": ""
    },
    ...
  ],
  "meta": {
    "include": [
      "books"
    ],
    "custom": [],
    "pagination": {
      "total": 9,
      "count": 7,
      "per_page": 10,
      "current_page": 1,
      "total_pages": 1,
      "links": {}
    }
  }
}
```
#### Books - Retrieve

- Retrieve a single book


`GET`
```
/v1/books/:[field]
```
#### Header

Field | Type | Description
---------|----------|---------
 Accept-Language | String | User language
#### Parameters
Field | Type | Description
---------|----------|---------
 id | String | alphabets and numbers
#### Success-Response
```json
HTTP/1.1 200 OK
{
   "data":{
      "id":"1",
      "name":"Python Learn The Hard way",
      "author":"Zed Shaw",
      "category":"education",
      "shelve_code":"2A1",
      "department_id":"HN",
      "created_at":"2020-03-31T13:51:32",
      "updated_at":"",
      "delete_at":""
   }
}
```

### Borrows
#### Borrows - List
- List all borrow bill


`GET`
```
api/v1/borrows/bill
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
  "data":
    {
      "id": "1",
      "books_id": "1",
      "accounts_id": "1",
      "day_borrow": "2020-07-27",
      "day_return": "2020-07-31",
      "created_at": "2020-07-271T13:51:32",
      "updated_at": "",
      "delete_at": "",
      "is_expired: True
    },
    {
      "id": "2",
      "books_id": "2",
      "accounts_id": "2",
      "day_borrow": "2020-08-1",
      "day_return": "2020-07-21",
      "created_at": "2020-08-1T14:00:00",
      "updated_at": "",
      "delete_at": "",
      "is_expired: True
    },
    ...
  ],
  "meta": {
    "include": [
      "books"
    ],
    "custom": [],
    "pagination": {
      "total": 9,
      "count": 7,
      "per_page": 10,
      "current_page": 1,
      "total_pages": 1,
      "links": {}
    }
  }
}
```
### Borrows - Retrieve

- Retrieve a single borrow bill


`GET`
```
/v1/borrows/bill/:id
```
#### Header

Field | Type | Description
---------|----------|---------
 Accept-Language | String | User language
#### Parameters
Field | Type | Description
---------|----------|---------
 id | String | alphabets and numbers
#### Success-Response
```json
HTTP/1.1 200 OK
{
  "data":
    {
      "id": "1",
      "books_id": "1",
      "accounts_id": "1",
      "day_borrow": "2020-07-27",
      "day_return": "2020-07-31",
      "created_at": "2020-07-271T13:51:32",
      "updated_at": "",
      "delete_at": "",
      "is_expired: True
    },
}
```
### Borrow - Create
- Create new borrower


`POST`
```
/v1/borrows
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
##### Parameters
Field | Type | Description
---------|----------|---------
 accounts_id | String | User language
 book_id | String | alphabets and numbers
 day_borrow | String | date time (YYYY-MM-DD)
 day_return | String | date -time (YYYY-MM-DD)
#### Success-Response
```json
HTTP/1.1 201 OK
{
  "results": {
    "id": "1",
    "created_at": "2020-07-271T13:51:32",
  }
}
```
#### Error-Response
```json
 HTTP/1.1 422
{
  "errors": [
    {
      "message": "account_id is duplicate in database"
    }
  ]
}
```
### Accounts
#### Accounts-Staff-Create
- Create new staff account
 
 
`POST`
```
/v1/accounts/staff
```
##### Header

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
HTTP/1.1 201 OK
{
  "results": {
    "accounts_id": "1",
    "created_at": "2020-07-271T13:51:32",
  }
}
```
#### Error-Response
```json
 HTTP/1.1 409
{
  "errors": [
    {
      "message": "staffs_id is duplicate in database"
    }
  ]
}
```
#### Accounts-Readers-Create
- Create new readers account
 
 
`POST`
```
/v1/accounts/readers
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
HTTP/1.1 201 OK
{
  "results": {
    "accounts_id": "2",
    "created_at": "2020-07-271T13:51:32",
  }
}
```
#### Error-Response
```json
 HTTP/1.1 409
{
  "errors": [
    {
      "message": "readers_id is duplicate in database"
    }
  ]
}
```
