##  RAML 

1. RAML 头部文件格式如下(缩进是2个字符)：

   ```
    %RAML 1.0

    title: e-BookMobile API
    baseUri: http://api.e-bookmobile.com/{version}
    version: v1
   ```

2. 资源定位

   * method

     GET: Retrieve the information defined in the request URI

     PUT: Replace the addressed collection

     POST: Create a new entry in the collection

     DELETE: Delete the information defined in the request URI

     eg:

     ```
     /books:
       get:
       post:
       put:
     ```

   * URI params

     *http://api.e-bookmobile.com/v1/books/Stiff*

     ``` 
     /books:
       /{bookTitle}:
     ```

     more

     ```
     /books:
       get:
       put:
       post:
       /{bookTitle}:
         get:
         put:
         delete:
         /author:
           get:
         /publisher:
           get:
     ```

   * query params

     ```
     /books:
       get:
         queryParamters:
           author:
           publicationYear:
           rating:
           isbn:
        put:
          queryParamters:
            access_token:
        post:
     ```

   More:

   ```
   /books:
     /{bookTitle}
       get:
         queryParameters:
           author:
             displayName: Author
             type: String
             description: A author's full name
             example: Mary Roach
             required: false
           publicationYear:
             displayName: Pub Year
             type: number
             description: The year released for the first time in the US
             example: 1984
             required: false
           rating:
             displayName: Rating
             type: number
             description: Average rating (1-5) submitted by users
             example: 3.14
             required: false
           isbn:
             displayName: ISBN
             type: string
             minLength: 10
             example: 0321736079?
       put:
         queryParameters:
           access_token:
             displayName: Access Token
             type: string
             description: Token giving you permission to make call
             required: true
   ```

   To make a PUT call, URI: *http://api.e-bookmobile.com/books/Stiff?access_token=ACCESSTOKEN

3. 返回值

   ```
   /books:
     /{bookTitle}:
       get:
         description: Retrieve a specific book title
         responses:
           200:
             body:
               application/json:
                 example: |
                   {
                     "data": {
                       "id": "SbBGk",
                       "title": "Stiff: The Curious Lives of Human Cadavers",
                       "description": null,
                       "datetime": 1341533193,
                       "genre": "science",
                       "author": "Mary Roach",
                       "link": "http://e-bookmobile.com/books/Stiff",
                     },
                     "success": true,
                     "status": 200
                   }
   ```

   ​

   ​

