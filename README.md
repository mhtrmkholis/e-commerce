# e-commerce
http://solid.mhtrmkholis.com
### Register :
```sh
URL: localhost:3000/users/register
METHOD : POST
Authenticated Required : NO
Authorized Required : NO
Data Input :
    {
        name: "kholis",
        email: "mhtrmkholis@gmail.com",
        password: "123123"
    }
Response Status : 201
Data Output :
    {
        "_id": "5ccf109c227c7e1387ab12f1",
        "name": "kholis",
        "email": "mhtrmkholis@gmail.com",
        "password": "$2a$10$BwEf3Bwsa8PJfliNr7UVOOoHPU0z8ucUdyt9JyJzM4KU3hdTwxHTW",
        "__v": 0
    }
Response Status : 400 Bad Request
Output :
    "User validation failed: name: Name is required, email: Email is required, password: Password is required"

Response Status : 500
Output :
    "Internal Server Error"
```
### Login :
```sh
URL: localhost:3000/users/login
METHOD : POST
Authenticated Required : NO
Authorized Required : NO
Data Input :
    {
        email: "mhtrmkholis@gmail.com",
        password: "123123"
    }
Response Status : 200
Data Output :
    {
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVjZDY2MjM1YjM5NWYxNDNmNzU5YzY3YiIsImVtYWlsIjoibmFydXRvQGdtYWlsLmNvbSIsImlhdCI6MTU1NzYxOTUwNywiZXhwIjoxNTU3NzA1OTA3fQ.ybuqEKrYVIzCJBGP6QjzD1Lcrd-lS08q5BOwNtnNFCo",
        "currentUser": {
            "UserId": "5cd66235b395f143f759c67b",
            "name": "kholis",
            "email": "mhtrmkholis@gmail.com"
        }
    }

Response Status : 400 Bad Request
Output :
    {
        "err": "email/password wrong!"
    }
Response Status : 500
Output :
    "Internal Server Error"
```
### list User :
```sh
localhost:3000/users
METHOD : GET
Authenticated Required : NO
Authorized Required : NO
Response Status : 200
[
    {
        "_id": "5cd66235b395f143f759c67b",
        "name": "kholis",
        "email": "kholis@gmail.com",
        "password": "$2a$10$NrYHAA94S/uCtYl2VsGqz.pbXqPqMbYtx.HyiaRbyMxy4VMu6JAoe",
        "__v": 0
    },
    {
        "_id": "5cd76100aaa5a74b2da055f6",
        "name": "kholis",
        "email": "kholis@gmail.com",
        "password": "$2a$10$.rsdx6VQImhJZ/e6hdgSAOtImrilnlGc80XU2RozzqfGzuBQr944i",
        "__v": 0
    },
    {...},{...}
]
Response Status : 500
Output :
    "Internal Server Error"
```
### Find By Id :
```sh
localhost:3000/users/5cd76100aaa5a74b2da055f6
METHOD : GET
Authenticated Required : NO
Authorized Required : NO
Data Input :
    {
        name: "kholis",
        email: "kholis@gmail.com"
    }
Response Status : 200
    {
        "_id": "5cd66235b395f143f759c67b",
        "name": "kholis",
        "email": "kholis@gmail.com",
        "password": "$2a$10$NrYHAA94S/uCtYl2VsGqz.pbXqPqMbYtx.HyiaRbyMxy4VMu6JAoe",
        "__v": 0
    }
Response Status : 500
Output :
    "Internal Server Error"
```
### Update By Id :
```sh
localhost:3000/users/5cd76100aaa5a74b2da055f6
METHOD : PUT
Authenticated Required : NO
Authorized Required : NO
Response Status : 200
    {
        "_id": "5cd66235b395f143f759c67b",
        "name": "kholis",
        "email": "kholis@gmail.com",
        "password": "$2a$10$NrYHAA94S/uCtYl2VsGqz.pbXqPqMbYtx.HyiaRbyMxy4VMu6JAoe",
        "__v": 0
    }
Response Status : 500
Output :
    "Internal Server Error"
```
### list Product:
```sh
http://localhost:3000/products
METHOD : GET
Authenticated Required : NO
Authorized Required : NO
Response Status : 200
[
    {
        "_id": "5cd6d56b2fc1c94b08fde8c9",
        "title": "kholis",
        "content": "kholissssss",
        "created_at": "2019-05-11T14:00:11.801Z",
        "author": {
            "_id": "5cd66235b395f143f759c67b",
            "name": "kholis",
            "email": "kholis@gmail.com",
            "password": "$2a$10$NrYHAA94S/uCtYl2VsGqz.pbXqPqMbYtx.HyiaRbyMxy4VMu6JAoe",
            "__v": 0
        },
        "image": "",
        "__v": 0
    },
    {...},{...},{...}
]
Response Status : 500
Output :
    "Internal Server Error"
```
### Create Product :
```sh
http://localhost:3000/products
METHOD : POST
Authenticated Required : YES
Authorized Required : NO
Data Input :
    {
        name: "Table",
        price: 1000000000
    }

Response Status : 200
Data Output :
    {
        "_id": "5cd767ebaaa5a74b2da055fc",
        "name": "Table",
        "price": "1000000000",
        "stock": 10,
        "__v": 0
    }

Response Status : 400 Bad Request
Output :
    "Product validation failed: title: Name is required, price: Price is required"

Response Status : 400 Bad Request
Output :
    "Token wrong!"
Response Status : 500
Output :
    "Internal Server Error"
```
### Delete Product :
```sh
http://localhost:3000/products/5cd767ebaaa5a74b2da055fc
METHOD : DELETE
Authenticated Required : YES
Authorized Required : YES
Response Status : 200
    {
        "_id": "5cd767ebaaa5a74b2da055fc",
        "name": "Table",
        "price": "1000000000",
        "__v": 0
    }
Response Status : 404
Output :
    {
        "msg": "You dont have access"
    }

Response Status : 400 Bad Request
Output :
    "Token wrong!"

Response Status : 500
Output :
    "Internal Server Error"
```
### Update Product :
```sh
http://localhost:3000/products/5cd6d56b2fc1c94b08fde8c9
METHOD : PUT
Authenticated Required : YES
Authorized Required : YES
Response Status : 200
    "Success"
Response Status : 404
Output :
    {
        "msg": "You dont have access"
    }

Response Status : 400 Bad Request
Output :
    "Token wrong!"
Response Status : 500
Output :
    "Internal Server Error"
```
### list Carts:
```sh
http://localhost:3000/carts
METHOD : GET
Authenticated Required : YES
Authorized Required : NO
Response Status : 200
[
    {
        "_id": "5cd6d56b2fc1c94b08fde8c9",
        "title": "kholis21",
        "content": "kholis211111111",
        "created_at": "2019-05-11T14:00:11.801Z",
        "author": {
            "_id": "5cd66235b395f143f759c67b",
            "name": "kholis",
            "email": "kholis@gmail.com",
            "password": "$2a$10$NrYHAA94S/uCtYl2VsGqz.pbXqPqMbYtx.HyiaRbyMxy4VMu6JAoe",
            "__v": 0
        },
        "image": "",
        "__v": 0
    },
    {...},{...},{...}
]
Response Status : 500
Output :
    "Internal Server Error"
```
### Create Product :
```sh
http://localhost:3000/carts
METHOD : POST
Authenticated Required : YES
Authorized Required : NO
Data Input :
    {
        name: "Table",
        price: 1000000000
    }

Response Status : 200
Data Output :
    {
        "_id": "5cd767ebaaa5a74b2da055fc",
        "name": "Table",
        "price": "1000000000",
        "__v": 0
    }

Response Status : 400 Bad Request
Output :
    "Product validation failed: title: Name is required, price: Price is required"

Response Status : 400 Bad Request
Output :
    "Token wrong!"
Response Status : 500
Output :
    "Internal Server Error"
```
### Delete Cart :
```sh
http://localhost:3000/products/5cd767ebaaa5a74b2da055fc
METHOD : DELETE
Authenticated Required : YES
Authorized Required : YES
Response Status : 200
    {
        "_id": "5cd767ebaaa5a74b2da055fc",
        "name": "Table",
        "price": "1000000000",
        "__v": 0
    }
Response Status : 404
Output :
    {
        "msg": "You dont have access"
    }

Response Status : 400 Bad Request
Output :
    "Token wrong!"

Response Status : 500
Output :
    "Internal Server Error"
```
### Delete Carts Belongs :
```sh
http://localhost:3000/carts/belongs/5cd767ebaaa5a74b2da055fc
METHOD : DELETE
Authenticated Required : YES
Authorized Required : YES
Response Status : 200
    {
        "_id": "5cd767ebaaa5a74b2da055fc",
        "name": "Table",
        "price": "1000000000",
        "__v": 0
    }
Response Status : 404
Output :
    {
        "msg": "You dont have access"
    }

Response Status : 400 Bad Request
Output :
    "Token wrong!"

Response Status : 500
Output :
    "Internal Server Error"
```
### List Transactions :
```sh
http://localhost:3000/transactions
METHOD : GET
Authenticated Required : YES
Authorized Required : YES (ADMIN)
Response Status : 200
    "Success"
Response Status : 404
Output :
    {
        "msg": "You dont have access"
    }

Response Status : 400 Bad Request
Output :
    "Token wrong!"
Response Status : 500
Output :
    "Internal Server Error"
```
### List User Transactions :
```sh
http://localhost:3000/transactions/user-transaction
METHOD : GET
Authenticated Required : YES
Authorized Required : NO
Response Status : 200
    "Success"
Response Status : 404
Output :
    {
        "msg": "You dont have access"
    }

Response Status : 400 Bad Request
Output :
    "Token wrong!"
Response Status : 500
Output :
    "Internal Server Error"
```
### Create Transaction :
```sh
http://localhost:3000/transactions
METHOD : POST
Authenticated Required : YES
Authorized Required : NO
Data Input :
    {
        name: "Table",
        price: 1000000000
    }

Response Status : 200
Data Output :
    {
        "_id": "5cd767ebaaa5a74b2da055fc",
        "name": "Table",
        "price": "1000000000",
        "__v": 0
    }

Response Status : 400 Bad Request
Output :
    "Product validation failed: title: Name is required, price: Price is required"

Response Status : 400 Bad Request
Output :
    "Token wrong!"
Response Status : 500
Output :
    "Internal Server Error"
```
### Update Transaction Status:
```sh
http://localhost:3000/transactions/delivered
METHOD : PATCH
Authenticated Required : YES
Authorized Required : YES
Response Status : 200
    {
        "_id": "5cd767ebaaa5a74b2da055fc",
        "name": "Table",
        "price": "1000000000",
        "__v": 0
    }
Response Status : 404
Output :
    {
        "msg": "You dont have access"
    }

Response Status : 400 Bad Request
Output :
    "Token wrong!"

Response Status : 500
Output :
    "Internal Server Error"
```
```
```
e-commerce
----
**Free Software, Yeah!**
