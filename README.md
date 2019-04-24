# goOSC 
One Stop Clicking is a digital content marketplace, which provide kinds of downloadable content, such as movie, book, music, and mobile/desktop application. User will enjoy exploring this app because there is a preview feature that allow users to preview the content before buying it. To bring easiness for transaction, this app has two kind of payment method: Balance Payment and PayPal Payment.

## API
URL: https://goosc.herokuapp.com/

#### Registration
This API is used to register new Users.

* **URL** : `/registration`
* **Method** : `POST`
* **Header** : `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  ```javascript
  {
    "email": string,
    "firtsname": string,
    "lastname": string,
    "password": string
  }
  ```

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Successfully Created",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

#### Login
This API is used to login a user registered.

* **URL** : `/auth`
* **Method** : `POST`
* **Header** : `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  ```javascript
  {
    "email": string,
    "password": string
  }
  ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Login Successfully",
        "data": {
            "user": {
                "id": 18,
                "email": "email@gmail.com",
                "password": "",
                "firtsname": "firtname",
                "lastname": "lastname",
                "created_at": {
                    "Time": "2019-02-28T15:36:59.602646Z",
                    "Valid": true
                },
                "updated_at": {
                    "Time": "0001-01-01T00:00:00Z",
                    "Valid": false
                }
            },
            "token": "string token"
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `401`
  * **Content:**
    ```javascript
    {
        "code": 401,
        "message": "Email or Password is not valid",
        "data": []
    }
    ```
    
#### Login with Social Media
This API is used to login a user with social media like google, facebook and twitter.
If the login is successful, it is automatically registered as a user in the application

* **URL** : 
    - **Google** : `/auth/google`
    - **Facebook** : `/auth/facebook`
    - **Twitter** : `/auth/twitter`
* **Method** : `GET`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    `same as login resppnse`
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
#### Forgot Password
This API is used to forgot password action.

* **URL** : `/forgot_password`
* **Method** : `POST`
* **Header** : `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  ```javascript
  {
    "email": string
  }
  ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Check your email and follow the link to reset password",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
#### User
This API is used to get data User, Edit, delete and Change Password.

##### Get List User

* **URL** : `/user`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Optional:**
   - If URL params is empty, it will use the default configuration from application
   - `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "count": 2,
            "list": [
                {
                    "id": 18,
                    "email": "email@gmail.com",
                    "password": "",
                    "firtsname": "firtsname",
                    "lastname": "lastname",
                    "role_id": 1,
                    "role_name": "Admin",
                    "created_at": {
                        "Time": "2019-02-28T15:36:59.602646Z",
                        "Valid": true
                    },
                    "updated_at": {
                        "Time": "0001-01-01T00:00:00Z",
                        "Valid": false
                    }
                }
            ]
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `401`
  * **Content:**
    ```javascript
    {
        "code": 401,
        "message": "Unauthorized",
        "data": []
    }
    ```
    
    OR
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
##### Get List By ID

* **URL** : `/user/{id}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "id": 18,
            "email": "email@gmail.com",
            "password": "",
            "firtsname": "firtsname",
            "lastname": "lastname",
            "role_id": 1,
            "role_name": "Admin",
            "created_at": {
                "Time": "2019-02-28T15:36:59.602646Z",
                "Valid": true
            },
            "updated_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            }
        }
    }
    ```
 
* **Error Response:**
    `same as error response Get List User`

##### Create User

* **URL** : `/user`
* **Method** : `POST`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  ```javascript
  {
    "email": string,
    "firtsname": string,
    "lastname": string,
    "password": string,
    "role_id": int
  }
  ```

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Successfully Created",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Update User

* **URL** : `/user/{id}`
* **Method** : `PUT`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  ```javascript
  {
    "email": string,
    "firtsname": string,
    "lastname": string,
    "role_id": int
  }
  ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Successfully Updated",
        "data": {
            "id": 18,
            "email": "email@gmail.com",
            "password": "",
            "firtsname": "firtsname",
            "lastname": "lastname",
            "created_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            },
            "updated_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            }
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Change Password User

* **URL** : `/user`
* **Method** : `PUT`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  ```javascript
  {
    "email": string,
    "old_password": string,
    "new_password": string
  }
  ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Change Password Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Delete User

* **URL** : `/user/{id}`
* **Method** : `DELETE`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `301`
  * **Content:** 
    ```javascript
    {
        "code": 301,
        "message": "Delete Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

#### Category
This API is used to Get List, Create, Update and Delete Category Data.

##### Get List Category

* **URL** : `/category`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Optional:**
   - If URL params is empty, it will use the default configuration from application
   - `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "count": 2,
            "list": [
                {
                    "category_id": 5,
                    "category_name": "Games",
                    "created_at": {
                        "Time": "2019-03-04T15:56:51.438317Z",
                        "Valid": true
                    },
                    "updated_at": {
                        "Time": "2019-03-04T15:58:46.176686Z",
                        "Valid": true
                    }
                }
            ]
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `401`
  * **Content:**
    ```javascript
    {
        "code": 401,
        "message": "Unauthorized",
        "data": []
    }
    ```
    
    OR
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
##### Get List By ID

* **URL** : `/category/{id}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "category_id": 5,
			"category_name": "Games",
			"created_at": {
				"Time": "2019-03-04T15:56:51.438317Z",
				"Valid": true
			},
			"updated_at": {
				"Time": "2019-03-04T15:58:46.176686Z",
				"Valid": true
			}
        }
    }
    ```
 
* **Error Response:**
    `same as error response Get List Category`

##### Create Category

* **URL** : `/category`
* **Method** : `POST`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  ```javascript
  {
	"category_name":"Games"
  }
  ```

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Successfully Created",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Update Category

* **URL** : `/category/{id}`
* **Method** : `PUT`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  ```javascript
  {
      "category_name": "Movies"
  }
  ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Successfully Updated",
        "data": {
            "category_id": 6,
			"category_name": "Movies",
			"created_at": {
				"Time": "0001-01-01T00:00:00Z",
				"Valid": false
			},
			"updated_at": {
				"Time": "0001-01-01T00:00:00Z",
				"Valid": false
			}
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Delete Category

* **URL** : `/category/{id}`
* **Method** : `DELETE`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `301`
  * **Content:** 
    ```javascript
    {
        "code": 301,
        "message": "Delete Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
#### Sub Category
This API is used to Get List, Create, Update and Delete Sub Category Data.

##### Get List Sub Category

* **URL** : `/subcategory`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Optional:**
   - If URL params is empty, it will use the default configuration from application
   - `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "count": 2,
            "list": [
                {
                    "subcategory_id": 2,
                    "category_id": 3,
                    "category_name": "Movie",
                    "subcategory_name": "Horror",
                    "created_at": {
                        "Time": "2019-03-04T16:00:04.071584Z",
                        "Valid": true
                    },
                    "updated_at": {
                        "Time": "2019-03-04T16:01:42.446404Z",
                        "Valid": true
                    }
                }
            ]
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `401`
  * **Content:**
    ```javascript
    {
        "code": 401,
        "message": "Unauthorized",
        "data": []
    }
    ```
    
    OR
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
##### Get List Sub Category By ID

* **URL** : `/subcategory/{id}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "subcategory_id": 1,
            "category_id": 3,
            "category_name": "Movie",
            "subcategory_name": "Action",
            "created_at": {
                "Time": "2019-03-04T09:53:43.211Z",
                "Valid": true
            },
            "updated_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            }
        }
    }
    ```
 
* **Error Response:**
    `same as error response Get List Sub Category`

##### Create Sub Category

* **URL** : `/subcategory`
* **Method** : `POST`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  ```javascript
  {
	"category_id":3,
	"subcategory_name":"Horror"
  }
  ```

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Successfully Created",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Update Sub Category

* **URL** : `/subcategory/{id}`
* **Method** : `PUT`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  ```javascript
  {
	"category_id":3,
	"subcategory_name": "Horror Edit"
  }
  ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Successfully Updated",
        "data": {
            "subcategory_id": 4,
            "category_id": 3,
            "subcategory_name": "Horror Edit",
            "created_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            },
            "updated_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            }
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Delete Sub Category

* **URL** : `/subcategory/{id}`
* **Method** : `DELETE`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `301`
  * **Content:** 
    ```javascript
    {
        "code": 301,
        "message": "Delete Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

#### Product
This API is used to get data Product, Edit, and delete.

##### Get List Product

* **URL** : `/product`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Optional:**
   - If URL params is empty, it will use the default configuration from application
   - `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "count": 2,
            "list": [
                {
                    "id": "XKQHYDVP",
                    "category_id": 3,
                    "subcategory_id": 1,
                    "category": "Movie",
                    "subcategory": "Action",
                    "name": "Product name",
                    "description": "Product description",
                    "thumbnail": "TYQQJAMK.jpg",
                    "file": "HSALSOEH.jpg",
                    "created_at": {
                        "Time": "2019-03-05T13:22:14.409872Z",
                        "Valid": true
                    },
                    "updated_at": {
                        "Time": "0001-01-01T00:00:00Z",
                        "Valid": false
                    }
                }
            ]
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `401`
  * **Content:**
    ```javascript
    {
        "code": 401,
        "message": "Unauthorized",
        "data": []
    }
    ```
    
    OR
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
##### Get List By ID

* **URL** : `/product/{id}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[string]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "id": "CMFWSVQJ",
            "category_id": 3,
            "subcategory_id": 1,
            "category": "Movie",
            "subcategory": "Action",
            "name": "Product name",
            "description": "Product Description",
            "thumbnail": "JRVRAECY.jpg",
            "file": "YBYGPXDL.jpg",
            "created_at": {
                "Time": "2019-03-05T13:21:25.090907Z",
                "Valid": true
            },
            "updated_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            }
        }
    }
    ```
 
* **Error Response:**
    `same as error response Get List Product`

##### Create Product

* **URL** : `/product`
* **Method** : `POST`
* **Header**: 
   - `Authorization:Bearer [string-token]`
   - `Content-Type:application/x-www-form-urlencoded`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**

    | Form Fields | Type |
    | ------ | ------ |
    | name | string (*) |
    | description | string (*) |
    | thumbnail | file (*) |
    | file | file (*) |
    | preview | file |
    | subcategory_id | integer (*) |
    *) required

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Successfully Created",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Update Product

* **URL** : `/product/{id}`
* **Method** : `PUT`
* **Header**:
   - `Authorization:Bearer [string-token]`
   - `Content-Type:application/x-www-form-urlencoded`
*  **URL Params**
   **Required:**
   `id:[string]`

* **Data Params**

    | Form Fields | Type |
    | ------ | ------ |
    | name | string (*) |
    | description | string (*) |
    | thumbnail | file |
    | file | file |
    | preview | file |
    | subcategory_id | integer (*) |
    *) required

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Successfully Updated",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Delete Product

* **URL** : `/product/{id}`
* **Method** : `DELETE`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[string]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `301`
  * **Content:** 
    ```javascript
    {
        "code": 301,
        "message": "Delete Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

#### Role Management
This API is used to Get List, Create, Update and Delete Role Data.

##### Get List Role

* **URL** : `/role`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Optional:**
   - If URL params is empty, it will use the default configuration from application
   - `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "count": 2,
            "list": [
                {
                    "role_id": 1,
                    "role_name": "Admin",
                    "created_at": {
                        "Time": "2019-03-06T12:27:10.852531Z",
                        "Valid": true
                    },
                    "updated_at": {
                        "Time": "2019-03-06T12:35:30.074504Z",
                        "Valid": true
                    }
                }
            ]
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `401`
  * **Content:**
    ```javascript
    {
        "code": 401,
        "message": "Unauthorized",
        "data": []
    }
    ```
    
    OR
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
##### Get List By ID

* **URL** : `/role/{id}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "role_id": 1,
            "role_name": "Admin",
            "created_at": {
                "Time": "2019-03-06T12:27:10.852531Z",
                "Valid": true
            },
            "updated_at": {
                "Time": "2019-03-06T12:35:30.074504Z",
                "Valid": true
            }
        }
    }
    ```
 
* **Error Response:**
    `same as error response Get List Role`

##### Create Role

* **URL** : `/role`
* **Method** : `POST`
* **Header**: 
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  ```javascript
  {
	"role_name":"Administrator"
  }
  ```

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Successfully Created",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Update Role

* **URL** : `/role/{id}`
* **Method** : `PUT`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  ```javascript
  {
      "role_name":"Admin"
  }
  ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Successfully Updated",
        "data": {
            "role_id": 3,
            "role_name": "User",
            "created_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            },
            "updated_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            }
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Delete Role

* **URL** : `/role/{id}`
* **Method** : `DELETE`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `301`
  * **Content:** 
    ```javascript
    {
        "code": 301,
        "message": "Delete Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

#### Rate
This API is used to get data Rate, Edit, and delete.

##### Get List Rate

* **URL** : `/rate`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Optional:**
   - If URL params is empty, it will use the default configuration from application
   - `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "count": 2,
            "list": [
                {
                    "id": 1,
                    "product_id": "XKQHYDVP",
                    "category_id": 3,
                    "subcategory_id": 1,
                    "category": "Movie",
                    "subcategory": "Action",
                    "product": "Alita: Battle Angel",
                    "index": 4,
                    "review": "Film is good, but we must waiting for next to get all of story",
                    "user_email": "email@yahoo.com",
                    "created_at": {
                        "Time": "2019-03-06T15:43:03.068Z",
                        "Valid": true
                    },
                    "updated_at": {
                        "Time": "0001-01-01T00:00:00Z",
                        "Valid": false
                    }
                }
            ]
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `401`
  * **Content:**
    ```javascript
    {
        "code": 401,
        "message": "Unauthorized",
        "data": []
    }
    ```
    
    OR
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
##### Get List By ID

* **URL** : `/rate/{id}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "id": 2,
            "product_id": "XKQHYDVP",
            "category_id": 3,
            "subcategory_id": 1,
            "category": "Movie",
            "subcategory": "Action",
            "product": "Alita: Battle Angel",
            "index": 3,
            "review": "In my opinion, this film is good",
            "user_email": "ahmadpuji.lestari@gmail.com",
            "created_at": {
                "Time": "2019-03-06T15:52:48.630224Z",
                "Valid": true
            },
            "updated_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            }
        }
    }
    ```
 
* **Error Response:**
    `same as error response Get List Product`

##### Create Rate

* **URL** : `/rate`
* **Method** : `POST`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**

    ```javascript
    {
    	"product_id": "XKQHYDVP",
    	"index": 4,
    	"review": "In my opinion, this film is good"
    }
    ```

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Successfully Created",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Update Rate

* **URL** : `/rate/{id}`
* **Method** : `PUT`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**

    ```javascript
    {
    	"product_id": "XKQHYDVP",
    	"index": 4,
    	"review": "In my opinion, this film is good"
    }
    ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Successfully Updated",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Delete Rate

* **URL** : `/rate/{id}`
* **Method** : `DELETE`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `301`
  * **Content:** 
    ```javascript
    {
        "code": 301,
        "message": "Delete Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
#### Voucher
This API is used to Get List, Create, Update and Delete Voucher Data.

##### Get List Voucher

* **URL** : `/voucher`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Optional:**
   - If URL params is empty, it will use the default configuration from application
   - `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
    * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "count": 1,
            "list": [
            {
                "voucher_id": 1,
                "voucher_name": "FREESHP",
                "voucher_desc": "Free shipping",
                "voucher_IsActive": "1",
                "voucher_startdate": "2019-03-13T00:00:00Z",
                "voucher_enddate": "2019-03-20T00:00:00Z",
                "voucher_discount": 0,
                "voucher_nominal": 50000,
                "voucher_createdate": {
                    "Time": "2019-03-13T13:10:04.300456Z",
                    "Valid": true
                },
                "voucher_updatedate": {
                    "Time": "0001-01-01T00:00:00Z",
                    "Valid": false
                },
                "voucher_deletedate": {
                    "Time": "2019-03-14T13:41:43.17502Z",
                    "Valid": true
                }
            }
            ]
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `401`
  * **Content:**
    ```javascript
    {
        "code": 401,
        "message": "Unauthorized",
        "data": []
    }
    ```
    
    OR
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
##### Get List By ID

* **URL** : `/voucher/{id}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
        "voucher_id": 1,
        "voucher_name": "FREESHP",
        "voucher_desc": "Free shipping",
        "voucher_IsActive": "1",
        "voucher_startdate": "2019-03-13T00:00:00Z",
        "voucher_enddate": "2019-03-20T00:00:00Z",
        "voucher_discount": 0,
        "voucher_nominal": 50000,
        "voucher_createdate": {
            "Time": "2019-03-13T13:10:04.300456Z",
            "Valid": true
        },
        "voucher_updatedate": {
            "Time": "0001-01-01T00:00:00Z",
            "Valid": false
        },
        "voucher_deletedate": {
            "Time": "2019-03-14T13:41:43.17502Z",
            "Valid": true
        }
        }
    }
    ```
 
* **Error Response:**
    `same as error response Get List Voucher`

##### Create Voucher

* **URL** : `/voucher`
* **Method** : `POST`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  ```javascript
  {          
            "voucher_name": "TGIFDISC4",
            "voucher_desc": "discount up to 25%",
            "voucher_IsActive": 1,
            "voucher_startdate":"2019-03-20T12:42:31Z",
            "voucher_enddate":"2019-03-23T12:42:31Z",
            "voucher_discount": 10,
        	"voucher_nominal": 0
    }
  ```

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Successfully Created",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Update Voucher

* **URL** : `/voucher/{id}`
* **Method** : `PUT`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  ```javascript
  {          
            "voucher_name": "TGIFDISC5",
            "voucher_desc": "discount up to 25%",
            "voucher_IsActive": 1,
            "voucher_startdate":"2019-03-20T12:42:31Z",
            "voucher_enddate":"2019-03-23T12:42:31Z",
            "voucher_discount": 10,
        	"voucher_nominal": 0
  }
  ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
    "code": 200,
    "message": "Successfully Updated",
    "data": {
        "voucher_id": 25,
        "voucher_name": "TGIFDISC5",
        "voucher_desc": "discount up to 15%",
        "voucher_IsActive": 1,
        "voucher_startdate": "2019-03-20T12:42:31Z",
        "voucher_enddate": "2019-03-23T12:42:31Z",
        "voucher_discount": 10,
        "voucher_nominal": 0,
        "voucher_createdate": {
            "Time": "0001-01-01T00:00:00Z",
            "Valid": false
        },
        "voucher_updatedate": {
            "Time": "0001-01-01T00:00:00Z",
            "Valid": false
        },
        "voucher_deletedate": {
            "Time": "0001-01-01T00:00:00Z",
            "Valid": false
        }
    }
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Delete Voucher

* **URL** : `/voucher/{id}`
* **Method** : `DELETE`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `301`
  * **Content:** 
    ```javascript
    {
        "code": 301,
        "message": "Delete Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

#### Permission
This API is used to Get List, Create, Update and Delete Permission Data.

##### Get List Permission

* **URL** : `/Permission`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `None`
   **Optional:**
   - If URL params is empty, it will use the default configuration from application
   - `?page=[integer start from 0]&size=[integer]`


* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
    * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "count": 1,
            "list": [
                {
                    "id": 16,
                    "role_id": 3,
                    "role_name": "User",
                    "endpoint": "/cart",
                    "allow_get": true,
                    "allow_post": true,
                    "allow_put": false,
                    "allow_delete": true,
                    "permission_createdat": {
                        "Time": "2019-03-31T00:00:00Z",
                        "Valid": true
                    },
                    "permission_updatedat": {
                        "Time": "0001-01-01T00:00:00Z",
                        "Valid": false
                    },
                    "permission_deletedat": {
                        "Time": "0001-01-01T00:00:00Z",
                        "Valid": false
                    }
                }
            ]
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `401`
  * **Content:**
    ```javascript
    {
        "code": 401,
        "message": "Unauthorized",
        "data": []
    }
    ```
    
    OR
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
##### Get List By ID

* **URL** : `/Permission/{id}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "id": 16,
            "role_id": 3,
            "role_name": "User",
            "endpoint": "/cart",
            "allow_get": true,
            "allow_post": true,
            "allow_put": false,
            "allow_delete": true,
            "permission_createdat": {
                "Time": "2019-03-31T00:00:00Z",
                "Valid": true
            },
            "permission_updatedat": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            },
            "permission_deletedat": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            }
        }
    }
    ```
 
* **Error Response:**
    `same as error response Get List Permission`

##### Create Permission

* **URL** : `/Permission`
* **Method** : `POST`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  ```javascript
      {
        "role_id": 1,
        "endpoint": "/permission/test",
        "allow_get": true,
        "allow_post": true,
        "allow_put": true,
        "allow_delete": true
      
     }
  ```

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Successfully Created",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Update Permission

* **URL** : `/Permission/{id}`
* **Method** : `PUT`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  ```javascript
    {
        "role_id": 2,
        "endpoint": "/permission/test",
        "allow_get": true,
        "allow_post": true,
        "allow_put": true,
        "allow_delete": true
      
    }

  ```

* **Success Response:**

  * **Code:** `200` 
  * **Content:** 
    ```javascript
    {
    "code": 200,
    "message": "Successfully Updated",
    "data":  {
        "role_id": 1,
        "endpoint": "/permission/test1",
        "allow_get": true,
        "allow_post": true,
        "allow_put": true,
        "allow_delete": true
      
    }
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Delete Permission

* **URL** : `/Permission/{id}`
* **Method** : `DELETE`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `301`
  * **Content:** 
    ```javascript
    {
        "code": 301,
        "message": "Delete Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

#### Guest View
This module is prepared for the first interaction between user and application. All features in this module will be available for users even though they have not logged in.

##### Homepage

* **URL** : `/homepage`
* **Method** : `GET`
* **Header**: `None`
*  **URL Params**
   **Not Required:**
   `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": [
            {
                "id": "SVVCOWJB",
                "name": "Spiderman"
            },
            {
                "id": "HVSTMOON",
                "name": "Harvest Moon"
            },
            {
                "id": "LUMGUQDI",
                "name": "Captain Marvel"
            }
        ],
        "length": 3
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Show All Product

* **URL** : `/guest/product`
* **Method** : `GET`
* **Header**: `None`
*  **URL Params**
   **Not Required:**
   `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": [
            {
                "id": "SVVCOWJB",
                "name": "Spiderman"
            },
            {
                "id": "HVSTMOON",
                "name": "Harvest Moon"
            },
            {
                "id": "LUMGUQDI",
                "name": "Captain Marvel"
            }
        ],
        "length": 3
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Search Product By Name

* **URL** : `/guest/product/search`
* **Method** : `GET`
* **Header**: `None`
*  **URL Params**
   **Not Required:**
   `?q=[string]&page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": [
            {
                "id": "LUMGUQDI",
                "name": "Captain Marvel"
            }
        ],
        "length": 1
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Show Product Detail

* **URL** : `/guest/product/detail`
* **Method** : `GET`
* **Header**: `None`
*  **URL Params**
   **Required:**
   `?id=[string]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "id": "HVSTMOON",
            "category_id": 4,
            "subcategory_id": 20,
            "category": "Music",
            "subcategory": "Pop",
            "name": "Harvest Moon",
            "description": "Ini adalah deskripsi product harvest moon",
            "thumbnail": "HARVEST.jpg",
            "file": "title.MP3",
            "product_preview": "/static/files/title.MP3",
            "preview_file_type": "audio",
            "created_at": {
                "Time": "2019-03-12T13:47:19.538467Z",
                "Valid": true
            },
            "updated_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            },
            "view_count": 519,
            "like_count": 202
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Show All Category

* **URL** : `/guest/category`
* **Method** : `GET`
* **Header**: `None`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": [
            {
                "category_id": 5,
                "category_name": "Book",
                "sub_category": [],
                "created_at": {
                    "Time": "2019-03-04T15:56:51.438317Z",
                    "Valid": true
                },
                "updated_at": {
                    "Time": "2019-03-04T15:58:46.176686Z",
                    "Valid": true
                }
            },
            {
                "category_id": 4,
                "category_name": "Music",
                "sub_category": [
                    {
                        "subcategory_id": 20,
                        "category_id": 4,
                        "category_name": "Music",
                        "subcategory_name": "Pop",
                        "created_at": {
                            "Time": "2019-03-12T08:42:02.752355Z",
                            "Valid": true
                        },
                        "updated_at": {
                            "Time": "2019-03-12T08:44:41.558751Z",
                            "Valid": true
                        }
                    }
                ],
                "created_at": {
                    "Time": "2019-03-04T15:12:11.868225Z",
                    "Valid": true
                },
                "updated_at": {
                    "Time": "2019-03-04T15:15:53.122611Z",
                    "Valid": true
                }
            }
        ]
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Show Sub Category By Category ID

* **URL** : `/guest/subcategory`
* **Method** : `GET`
* **Header**: `None`
*  **URL Params**
   **Required:**
   `?id=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": [
            {
                "subcategory_id": 1,
                "category_id": 3,
                "category_name": "Movie",
                "subcategory_name": "Action",
                "created_at": {
                    "Time": "2019-03-04T09:53:43.211Z",
                    "Valid": true
                },
                "updated_at": {
                    "Time": "0001-01-01T00:00:00Z",
                    "Valid": false
                }
            }
        ]
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Subscribe To Content Provider

* **URL** : `/guest/subscribe`
* **Method** : `POST`
* **Header**: `None`
*  **URL Params**
   `None`

* **Data Params**

    | Form Fields | Type |
    | ------ | ------ |
    | useremail | string (*) |
    | provideremail | string (*) |
    *) required

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": null
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Like Product

* **URL** : `/guest/product/like`
* **Method** : `POST`
* **Header**: `None`
*  **URL Params**
   **Required:**
   `?id=[string]`

* **Data Params**
    `None`

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "You Liked This Product",
        "data": null
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

#### Promote
This API is used to get data Promote, Edit, and delete.

##### Get List Promote

* **URL** : `/promote`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Optional:**
   - If URL params is empty, it will use the default configuration from application
   - `?page=[integer start from 0]&size=[integer]`


* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": [
            {
                "id": 2,
                "product_id": "MSVMJHLV",
                "category_id": 3,
                "subcategory_id": 1,
                "category": "Movie",
                "subcategory": "Action",
                "product": "Ant-Man (film)",
                "title": "Promote Ant-Man (film)",
                "start_date": "2019-03-15T00:00:00Z",
                "end_date": "2019-03-20T23:59:59Z",
                "position": 1,
                "created_at": {
                    "Time": "2019-03-15T14:53:34.980542Z",
                    "Valid": true
                },
                "updated_at": {
                    "Time": "0001-01-01T00:00:00Z",
                    "Valid": false
                }
            }
        ]
    }
    ```
 
* **Error Response:**

  * **Code:** `401`
  * **Content:**
    ```javascript
    {
        "code": 401,
        "message": "Unauthorized",
        "data": []
    }
    ```
    
    OR
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
##### Get List By ID

* **URL** : `/promote/{id}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "id": 2,
            "product_id": "MSVMJHLV",
            "category_id": 3,
            "subcategory_id": 1,
            "category": "Movie",
            "subcategory": "Action",
            "product": "Ant-Man (film)",
            "title": "Promote Ant-Man (film)",
            "start_date": "2019-03-15T00:00:00Z",
            "end_date": "2019-03-20T23:59:59Z",
            "position": 1,
            "created_at": {
                "Time": "2019-03-15T14:53:34.980542Z",
                "Valid": true
            },
            "updated_at": {
                "Time": "0001-01-01T00:00:00Z",
                "Valid": false
            }
        }
    }
    ```
 
* **Error Response:**
    `same as error response Get List Promote`

##### Create Promote

* **URL** : `/promote`
* **Method** : `POST`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `None`

* **Data Params**

    ```javascript
    {
    	"product_id": "UBIBKCVF",
    	"title": "Promote Stranger Things 6",
    	"start_date": "2019-03-15T00:00:00Z",
    	"end_date": "2019-03-20T23:59:59Z",
    	"position": 3
    }
    ```

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Successfully Created",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Update Promote

* **URL** : `/promote/{id}`
* **Method** : `PUT`
* **Header**:
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**

    ```javascript
    {
    	"product_id": "UBIBKCVF",
    	"title": "Promote Stranger Things 6",
    	"start_date": "2019-03-15T00:00:00Z",
    	"end_date": "2019-03-20T23:59:59Z",
    	"position": 3
    }
    ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Successfully Updated",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Delete Promote

* **URL** : `/promote/{id}`
* **Method** : `DELETE`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id:[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `301`
  * **Content:** 
    ```javascript
    {
        "code": 301,
        "message": "Delete Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
#### Payment Process 
This API is used to do Payment Process 

##### Payment Overview
This API is used to show payment overview of a product 

* **URL** : `/cart/overview/{product id}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `product id:[string]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "id": "HVSTMOON",
            "name": "Harvest Moon",
            "description": "",
            "price": 75000,
            "currency": "IDR"
        }
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```

##### Add To Cart

* **URL** : `/cart/{product id}`
* **Method** : `POST`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `product id:[string]`
* **Data Params**
    `None`

* **Success Response:**
  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Product has been added to your cart",
        "data": []
    }
    ```
 
* **Error Response:**
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

##### Show List Cart

* **URL** : `/cart`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   `None`
* **Data Params**
    `None`

* **Success Response:**
  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": [
            {
                "id": "34",
                "product_id": "HVSTMOON",
                "product_name": "Harvest Moon",
                "price": 75000,
                "cprovider_email": "contentprovider@email.com",
                "created_at": {
                    "Time": "2019-03-21T10:13:59.570729Z",
                    "Valid": true
                },
                "updated_at": {
                    "Time": "0001-01-01T00:00:00Z",
                    "Valid": false
                }
            }
        ]
    }
    ```

* **Error Response:**
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

##### Delete Cart

* **URL** : `/cart/{cart id}`
* **Method** : `DELETE`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `cart id:[integer]`
* **Data Params**
    `None`

* **Success Response:**
  * **Code:** `301`
  * **Content:** 
    ```javascript
    {
        "code": 301,
        "message": "Product has been deleted from your cart",
        "data": []
    }
    ```

* **Error Response:**
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
##### Voucher Validation

* **URL** : `/cart/voucher?voucher={voucher code}`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `voucher code:[string]`
* **Data Params**
    `None`

* **Success Response:**
  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Voucher Valid",
        "data": {
            "voucher": "AKHIRBLN",
            "description": "Discount 50%, maximal potongan 20.000 Rupiah",
            "discount": 50,
            "nominal": 20000,
            "total": 0,
            "final_price": 0
        }
    }
    ```

* **Error Response:**
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

##### Cart Summary

* **URL** : `/cart/summary`
* **Method** : `GET`
* **Header**: 
    `Authorization:Bearer [string-token]`
    `Content-Type:application/json`
*  **URL Params**
   `None`
* **Data Params**
    ```javascript
    {
    	"voucher":"AKHIRBLN",
    	"payment_type":"balance"
    }
    
    *Note: 
        payment type: only 'balance' or 'paypal' will be accepted 
    ```
* **Success Response:**
  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Summary Payment",
        "data": {
            "voucher": "AKHIRBLN",
            "payment_type": "balance",
            "total": 75000,
            "total_discount": 20000,
            "final_price": 55000,
            "currency": "IDR",
            "product_list": [
                {
                    "id": "35",
                    "product_id": "HVSTMOON",
                    "product_name": "Harvest Moon",
                    "price": 75000,
                    "cprovider_email": "contentprovider@email.com",
                    "created_at": {
                        "Time": "2019-03-21T10:48:23.582004Z",
                        "Valid": true
                    },
                    "updated_at": {
                        "Time": "0001-01-01T00:00:00Z",
                        "Valid": false
                    }
                }
            ]
        }
    }
    ```

* **Error Response:**
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Submit Payment
* I have created the page for demo. Please use this URL for payment page:
**http://your-domain/payment/{token}**

* There is two payment method, if you choose "balance" then application will check your  balance availability, if insufficient then application shows error message and application will not continue process to the next step but if balance is ok then application will do submit payment.
* If you choose "paypal" payment method, then application will show paypal button and you should login to your paypal account after that paypal will do payment transaction, if transaction succeed then application will do submit payment.

##### Submit Payment API List
Submit payment page used several API, that is:
1. Submit Payment
    * **URL** : `/cart/dopayment`
    * **Method** : `POST`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
       `None`
    * **Data Params**
    
        | Form Fields | Type |
        | ------ | ------ |
        | token | string (*) |
        | payment-type | string (**) |
        | voucher-name | string |
        *) required
        **) 'paypal' or 'balance'

    * **If you choose balance payment type:**
        **- Success Response**
        * **Code:** `200`
        * **Content:** 
            ```javascript
            {
                "Data": {
                    "ammount": "",
                    "payment_data": "",
                    "paypal": false
                },
                "message": "Success",
                "success": true
            }
            ```
        
        **- Error Response**
        * **Code:** `500`
        * **Content:**
            ```javascript
            {
                "code": 500,
                "message": "string message",
                "data": []
            }
            ```
    * **If you choose paypal payment type:**
        **- Success Response**
        * **Code:** `200`
        * **Content:** 
            ```javascript
            {
                "Data": {
                    "ammount": 3.89,
                    "payment_data": {
                        "payment_code": "FGQBPTVHIL",
                        "email": "roleuser@email.com",
                        "voucher": "AKHIRBLN",
                        "payment_type": "paypal",
                        "total": 5.3,
                        "total_discount": 1.42,
                        "final_price": 3.89,
                        "payment_amount": 3.89,
                        "currency": "USD",
                        "pre_balance": 0,
                        "post_balance": 0,
                        "payment_status": "",
                        "product_list": [
                            {
                                "id": "37",
                                "product_id": "HVSTMOON",
                                "product_name": "Harvest Moon",
                                "price": 5.3,
                                "cprovider_email": "contentprovider@email.com",
                                "created_at": {
                                    "Time": "2019-03-21T12:02:12.150585Z",
                                    "Valid": true
                                },
                                "updated_at": {
                                    "Time": "0001-01-01T00:00:00Z",
                                    "Valid": false
                                }
                            }
                        ]
                    },
                    "paypal": true
                },
                "message": "",
                "success": true
            }
            ```
        
        **- Error Response**
        * **Code:** `500`
        * **Content:**
            ```javascript
            {
                "code": 500,
                "message": "string message",
                "data": []
            }
            ```
2. Get Paypal Payment ID
    * **URL** : `/paypalpayment?ammount={total price}`
    * **Method** : `POST`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
       **Required:**
       `total price:[double]`
    * **Data Params**
        `None`
    
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {"id":"PAYID-LSJR3MQ7UW78376HY3637410"}
        ```
    
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
3. Callback Paypal Payment
    * **URL** : `/paypalpaymentcallback?paymentID={pay-id}&payerID={payer-id}&payment={payment-data}`
    * **Method** : `POST`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
       **Required:**
       `pay-id:[string] : get this id from paypal payment id API`
       `payer-id:[string] : get this data after login to paypal`
       `payment-data:[string json] : get this data from Submit Payment API`
    * **Data Params**
        `None`
    
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
			"PaymentState":   "approved",
			"PaymentMessage": "Payment Succeed",
			"PaymentID":      "string payment id",
			"PayerName":      "string payer name",
		}
        ```
    
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
		{
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
##### Download Product
* I have created the page for demo. Please use this URL for download page:
**http://your-domain/download/{token}**
There is one textfield that must be filled: {Product ID}

##### Download Product API List
Download product page used several API, that is:
1. Download Token & Maximum Download Amount Validation
    * **URL** : `/cart/downloadvalidation?productid={product id}`
    * **Method** : `GET`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
      **Required:**
       `product id: [string]`
    * **Data Params**
        `None`
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "filename": "filename.extension",
            "message": "OK",
            "success": true
        }
        ```
    
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
2. Download File
    * **URL** : `/cart/downloadfile?productid={product id}`
    * **Method** : `GET`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
      **Required:**
       `product id: [string]`
    * **Data Params**
        `None`
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        Return BLOB
    
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```

#### User Balance Management
This API is used to Get List, Create and Update user balance data.

##### Get List User Balance

* **URL** : `/balance`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Optional:** If URL params is empty, that will be using default configuration from application.
   `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "count": 2,
            "list": [
                {
                    "id": 3,
                    "user_email": "roleuserdummy@email.com",
                    "user_balance": 100000,
                    "created_at": {
                        "Time": "2019-03-22T09:29:04.771847Z",
                        "Valid": true
                    },
                    "updated_at": {
                        "Time": "2019-03-22T09:35:34.864162Z",
                        "Valid": true
                    }
                }
            ]
        }
    }
    ```
 
* **Error Response:**
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
##### Get Balance By Email

* **URL** : `/balance/detail`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `?email=[string]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "id": 1,
            "user_email": "roleuser@email.com",
            "user_balance": 200000,
            "created_at": {
                "Time": "2019-03-01T00:00:00Z",
                "Valid": true
            },
            "updated_at": {
                "Time": "2019-03-22T13:25:41.930225Z",
                "Valid": true
            }
        }
    }
    ```
 
* **Error Response:**
    `same as error response Get List User Balance`

##### Create User Balance

* **URL** : `/balance`
* **Method** : `POST`
* **Header**: 
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   `None`

* **Data Params**
    ```javascript
    {
        "user_email":"roleuserdummy@email.com",
        "user_balance":100000
    }
    ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Created Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
##### Update User Balance
This API used to increase user balance

* **URL** : `/balance/{id}`
* **Method** : `PUT`
* **Header**: 
  - `Authorization:Bearer [string-token]`
  - `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `id=[integer]`

* **Data Params**
    ```javascript
    {
    	"user_balance":1000
    }
    ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Created Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

##### Admin Dashboard List
Admin dashboard page used several API, that is:
1. Payment Statistic Chart
    * **URL** : `/dashboard/admin/paymentstatistic`
    * **Method** : `GET`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
      **Optional:**
      - if not using param, it will use current date for the default value
      - `?start=[date]&end=[date]`
    * **Data Params**
        `None`
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Data Received Successfully",
            "data": [
                {
                    "date": "2019-03-10T00:00:00Z",
                    "balance": 0,
                    "paypal": 0
                },
                ...
                {
                    "date": "2019-03-31T00:00:00Z",
                    "balance": 0,
                    "paypal": 0
                }
            ]
        }
        ```
    
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
2. Payment Report
    * **URL** : `/dashboard/admin/paymentreport`
    * **Method** : `GET`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
      **Optional:**
       - if not using param, it will use current date for the default value
       - `?start=[date]&end=[date]`
    * **Data Params**
        `None`
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Data Received Successfully",
            "data": [
                {
                    "date": "2019-03-21T00:00:00Z",
                    "payment_type": "balance",
                    "total_price": 500000,
                    "total_discount": 90000,
                    "final_price": 410000,
                    "payment_amount": 410000,
                    "currency": "IDR"
                }
            ]
        }
        ```
    
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```

3. Payment Report Detail
    * **URL** : `/dashboard/admin/paymentreport/detail`
    * **Method** : `GET`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
      **Optional:**
       - if not using param, it will use current date for the default value
       - `?start=[date]&end=[date]&page=[integer start from 0]&size=[integer]`
    * **Data Params**
        `None`
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Data Received Successfully",
            "data": {
                "count": 7,
                "list": [
                    {
                        "payment_code": "MSIGLCDRSD",
                        "user_email": "roleuser@email.com",
                        "user_name": "Role User",
                        "date": "2019-03-21T08:18:41.767967Z",
                        "type": "balance",
                        "total_price": 75000,
                        "total_discount": 20000,
                        "final_price": 55000,
                        "payment_amount": 55000,
                        "currency": "IDR",
                        "voucher_code": "AKHIRBLN",
                        "voucher_name": "Discount 50%, maximal potongan 20.000 Rupiah",
                        "user_prebalance": 195000,
                        "user_postbalance": 140000
                    }
                ]
            }
        }
        ```
    
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
        
4. Download Statistic
    * **URL** : `/dashboard/admin/downloadstatistic`
    * **Method** : `GET`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
      **Optional:**
       - if not using param, that's using current date for default value
       - `?start=[date]&end=[date]`
    * **Data Params**
        `None`
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Data Received Successfully",
            "data": [
                {
                    "date": "2019-03-10T00:00:00Z",
                    "total": 0
                },
                ...
                {
                    "date": "2019-03-21T00:00:00Z",
                    "total": 0
                }
            ]
        }
        ```
    
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
        
5. Download Report
    * **URL** : `/dashboard/admin/downloadreport`
    * **Method** : `GET`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
      **Optional:**
       - if not using param, it will use current date for the default value
       - `?start=[date]&end=[date]`
    * **Data Params**
        `None`
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Data Received Successfully",
            "data": [
                {
                    "date": "2019-03-21T00:00:00Z",
                    "product_id": "HVSTMOON",
                    "product": "Harvest Moon",
                    "total": 1
                },
                {
                    "date": "2019-03-21T00:00:00Z",
                    "product_id": "LUMGUQDI",
                    "product": "Captain Marvel",
                    "total": 11
                }
            ]
        }
        ```
    
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
##### User Dashboard List
Admin dashboard page used several API, that is:

1. User Data
    This API used to get user data
    * **URL** : `/dashboard/user`
    * **Method** : `GET`
    * **Header**: 
        `Authorization:Bearer [string-token]`
    *  **URL Params**
      `None`
    * **Data Params**
        `None`
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Data Received Successfully",
            "data": [
                {
                    "user_email": "roleuserdummy@email.com",
                    "firts_name": "Role",
                    "last_name": "User",
                    "user_balance": 0,
                    "join_date": "2019-03-11T08:31:23.368642Z"
                }
            ]
        }
        ```
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
        
2. Activate User Balance
    This API used to activate user balance, actually this API just create user balance data. Before user do top up balance, they have to activate their balance. This API can only be accessed by role user.

    * **URL** : `/dashboard/user/activatebalance`
    * **Method** : `POST`
    * **Header**: 
        `Authorization: Bearer [string-token]`
        `Content-Type: application/json`
    *  **URL Params**
      `None`
    * **Data Params**
        ```javascript
        {
        	"user_email":"roleuserdummy@email.com"
        }
        ```
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Activated Successfully",
            "data": []
        }
        ```
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
3. Get Top Up Ammount List
    This API used to get ammount list for top up balance.  
    * **URL** : `/dashboard/user/topupammount`
    * **Method** : `GET`
    * **Header**: 
        `Authorization: Bearer [string-token]`
    *  **URL Params**
      `None`
    * **Data Params**
        `None`
    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Data Received Successfully",
            "data": [
                50000,
                100000,
                250000,
                500000,
                1000000
            ]
        }
        ```
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
4. Submit Top Up Order
    This API used to submit top up balance order.  
    * **URL** : `/dashboard/user/topuporder`
    * **Method** : `POST`
    * **Header**: 
        `Authorization: Bearer [string-token]`
    *  **URL Params**
      `None`
    * **Data Params**
        | Form Fields | Type |
        | ------ | ------ |
        | receipt | file (*) |
        | ammount | string (*) |
        *) required

    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Submited Successfully",
            "data": []
        }
        ```
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```

5. List Top Up Order (Admin)
    This API used by admin to get top up balance order which submitted by user.  
    * **URL** : `/balance/topuporder`
    * **Method** : `GET`
    * **Header**: 
        `Authorization: Bearer [string-token]`
    *  **URL Params**
        **Optional:** If URL params is empty, that will be using default configuration from application.
        `?page=[integer start from 0]&size=[integer]`
    * **Data Params**
        `None`

    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Data Received Successfully",
            "data": {
                "count": 1,
                "list": [
                    {
                        "id": 9,
                        "user_email": "roleuserdummy@email.com",
                        "ammount": 250000,
                        "transfer_receipt": "/static/transfer-receipt/SLXEMCVP.jpg",
                        "first_name": "Role",
                        "last_name": "User",
                        "order_date": "2019-03-26T08:07:08.105729Z"
                    }
                ]
            }
        }
        ```
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```
6. Accept Top Up Request (Admin)
    This API used by admin to accept top up balance order which submitted by user. When  submitted, then user balance will increased by nominal same as user request.
    * **URL** : `/balance/accepttopup`
    * **Method** : `POST`
    * **Header**: 
        `Authorization: Bearer [string-token]`
    *  **URL Params**
        **Required:** Order id
        `?id=[integer]`
    * **Data Params**
        `None`

    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Confirmed Successfully",
            "data": []
        }
        ```
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```

7. Accept Top Up Request With Reason and Nominal Accepted (Admin)
    This API used by admin to accept top up balance order with reason and nominal accepted. When  submitted, then user balance will increased by nominal same as admin input.
    * **URL** : `/balance/rejecttopup`
    * **Method** : `POST`
    * **Header**: 
        `Authorization: Bearer [string-token]`
    *  **URL Params**
        **Required:** Order id
        `?id=[integer]`
    * **Data Params**
        | Form Fields | Type |
        | ------ | ------ |
        | ammount | string (*) |
        | reason | string (*) |
        *) required

    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Confirmed Successfully",
            "data": []
        }
        ```
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```

8. Get Balance History
    This API used to get list of user balance history.
    * **URL** : `/dashboard/user/balancehistory`
    * **Method** : `GET`
    * **Header**: 
        `Authorization: Bearer [string-token]`
    *  **URL Params**
        `None`
    * **Data Params**
        `None`

    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Data Received Successfully",
            "data": {
                "count": 2,
                "list": [
                    {
                        "user_email": "roleuserdummy@email.com",
                        "debit": 250000,
                        "credit": 0,
                        "date": "2019-03-25T14:37:34.779659Z"
                    },
                    {
                        "user_email": "roleuserdummy@email.com",
                        "debit": 0,
                        "credit": 125000,
                        "date": "2019-03-25T14:45:55.288196Z"
                    }
                ]
            }
        }
        ```
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```

9. Get Download History
    This API used to get list of user download history.
    * **URL** : `/dashboard/user/downloadhistory`
    * **Method** : `GET`
    * **Header**: 
        `Authorization: Bearer [string-token]`
    *  **URL Params**
        `None`
    * **Data Params**
        `None`

    * **Success Response:**
      * **Code:** `200`
      * **Content:** 
        ```javascript
        {
            "code": 200,
            "message": "Data Received Successfully",
            "data": {
                "count": 2,
                "list": [
                    {
                        "user_email": "roleuser@email.com",
                        "product_id": "HVSTMOON",
                        "product_name": "Harvest Moon",
                        "download_date": "2019-03-25T14:56:58.737909Z"
                    },
                    {
                        "user_email": "roleuser@email.com",
                        "product_id": "LUMGUQDI",
                        "product_name": "Captain Marvel",
                        "download_date": "2019-03-25T14:55:24.873744Z"
                    }
                ]
            }
        }
        ```
    * **Error Response:**
      * **Code:** `500`
      * **Content:**
        ```javascript
        {
            "code": 500,
            "message": "string message",
            "data": []
        }
        ```

#### Top Up Ammount Management
This API is used to Get List, Create, Update and Delete Top Up Ammount List.

**1. Get List Top Up Ammount**

* **URL** : `/topupammount`
* **Method** : `GET`
* **Header**: `Authorization:Bearer [string-token]`
*  **URL Params**
   **Optional:** If URL params is empty, that will be using default configuration from application.
   `?page=[integer start from 0]&size=[integer]`

* **Data Params**
  `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": {
            "count": 5,
            "list": [
                {
                    "id": 1,
                    "ammount": 50000,
                    "created_at": {
                        "Time": "2019-03-26T09:33:02Z",
                        "Valid": true
                    },
                    "updated_at": {
                        "Time": "0001-01-01T00:00:00Z",
                        "Valid": false
                    }
                }
            ]
        }
    }
    ```
 
* **Error Response:**
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String message",
        "data": []
    }
    ```
    
**2. Create Top Up Ammount**

* **URL** : `/topupammount`
* **Method** : `POST`
* **Header**: 
    `Authorization:Bearer [string-token]`
    `Content-Type:application/json`
*  **URL Params**
   `None`

* **Data Params**
    ```javascript
    {
    	"ammount":[integer]
    }
    ```

* **Success Response:**

  * **Code:** `201`
  * **Content:** 
    ```javascript
    {
        "code": 201,
        "message": "Created Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
**3. Update Top Up Ammount**
* **URL** : `/topupammount/{id}`
* **Method** : `PUT`
* **Header**: 
    `Authorization:Bearer [string-token]`
    `Content-Type:application/json`
*  **URL Params**
   **Required:**
   `id=[integer]`

* **Data Params**
    ```javascript
    {
    	"ammount":[integer]
    }
    ```

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Updated Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```
    
**4. Delete Top Up Ammount**
* **URL** : `/topupammount/{id}`
* **Method** : `DELETE`
* **Header**: 
    `Authorization:Bearer [string-token]`
*  **URL Params**
   **Required:**
   `id=[integer]`

* **Data Params**
    `None`

* **Success Response:**

  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Deleted Successfully",
        "data": []
    }
    ```
 
* **Error Response:**

  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "String Message",
        "data": []
    }
    ```

#### Chat

This is list of the API can be used to build chat application

##### 1. Chat Service
The chat service using [Websocket](https://www.websocket.org) technology
* **URL** : `/ws`
* **Method** : `GET`
* **Header**: 
    `none`
*  **URL Params**
  **Required:**
   - `?useremail=[string]&destemail=[string]&username=[string]&chatid=[string]&type=[admin/cp]`
   - `useremail` is email of current user
   - `destemail` is email of destination user
   - `username` is name of current user
   - `type` is type of chat {admin/cp}

##### 2. Get Chat List

* **URL** : `/chat`
* **Method** : `GET`
* **Header**: 
    `Authorization:Bearer [string-token]`
*  **URL Params**
  **Optional:**
   `none`
* **Data Params**
    `None`
* **Success Response:**
  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": [
            {
                "destination_email": "roleuser@email.com",
                "destination_name": "Role User",
                "unread_chat": 1,
                "chat_id": "QWERTY",
                "type_chat": "admin"
            }
        ]
    }
    ```

* **Error Response:**
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "string message",
        "data": []
    }
    ```
##### 3. Chat Detail

* **URL** : `/chat`
* **Method** : `POST`
* **Header**: 
    `Authorization:Bearer [string-token]`
*  **URL Params**
  **Optional:**
   `none`
* **Data Params**
    ```javascript
    {
        "useremail": "user@email.com",
        "destination_email": "dest@email.com"
    }
    ```
* **Success Response:**
  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "code": 200,
        "message": "Data Received Successfully",
        "data": [
            {
                "chat_id": "QWERTY",
                "useremail": "roleuser@email.com",
                "username": "Role User",
                "destination_email": "",
                "destination_name": "",
                "message": "Halo admin",
                "chat_date": "2019-03-28T13:07:30.401377Z",
                "read": true
            },
            {
                "chat_id": "QWERTY",
                "useremail": "gweaja@yahoo.com",
                "username": "Den Ahmad",
                "destination_email": "",
                "destination_name": "",
                "message": "Halo role",
                "chat_date": "2019-03-28T13:12:10.495573Z",
                "read": true
            },
        ]
    }
    ```

* **Error Response:**
  * **Code:** `500`
  * **Content:**
    ```javascript
    {
        "code": 500,
        "message": "string message",
        "data": []
    }
    ```

##### 4. Sample Chat UI
This is sample of chat using this chat API
* **URL** : `/chat/form`
* **Method** : `GET`
* **Header**: 
    `none`
*  **URL Params**
  **Required:**
   - `?type=[admin/cp]&product=[string productID]`
   - `type` is mandatory
   - `product` is optional when `type=admin`, but if `type=cp` it's mandatory

##### 5. Sample Chat List UI
This is sample of chat list and conversation history
* **URL** : `/chat/list`
* **Method** : `GET`
* **Header**: 
    `none`
*  **URL Params**
   `None`

##### 6. Get Product Info
This is used to get product info for chat with content provider on mobile device
* **URL** : `/chat/data`
* **Method** : `GET`
* **Header**: 
    `none`
*  **URL Params**
  **Required:**
   - `?type=[admin/cp]&product=[string productID]`
   - `type` is mandatory
   - `product` is optional when `type=admin`, but if `type=cp` it's mandatory
* **Data Params**
    `none`
* **Success Response:**
  * **Code:** `200`
  * **Content:** 
    ```javascript
    {
        "host": "ws://172.19.16.148:9000",
        "message": "",
        "product_detail": "http://172.19.16.148:9000/guest/product/detail?id=CNMEXQQU",
        "product_name": "One Flew Over the Cuckoo's Nest",
        "product_price": 25000,
        "product_thumbnail": "http://172.19.16.148:9000/static/images/RNWMCNOX.jpg",
        "success": true,
        "title": "Chat With Content Provider"
    }
    ```
