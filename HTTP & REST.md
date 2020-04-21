# HTTP & REST

## HTTP
*Hyper Text Transfer Protocol*

- Apps using HTTP use the *Client-Server* model
- HTTP requests are transfered via TCP 

|HTTP Method |Request Has Body	|Response Has Body	|Safe	|Idempotent	|Cacheable	|Function|
|--------|---------|---------|---------|--------|---------|--------|
|GET	|No	|Yes	|Yes	|Yes	|Yes	|Retrieve a resource|
|HEAD	|No	|No	|Yes	|Yes	|Yes	|Like GET but headers only|
|POST	|Yes	|Yes	|No	|No	|Yes	|Create a resource|
|PUT	|Yes	|Yes	|No	|Yes |No	|Update a resource|
|DELETE	|No	|Yes	|No	|Yes	|No	|Delete a resource|
|CONNECT	|Yes	|Yes	|No	|No	|No	|Create TCP/IP tunnel|
|OPTIONS	|Optional	|Yes	|Yes	|Yes	|No	|Returns supported methods for a URL|
|TRACE	|No	|Yes	|Yes	|Yes	|No	|Echos |retrieved |request|
|PATCH	|Yes	|Yes	|No	|No	|No	|Partial modification of resource|

- `Safe` only used for information retrieval and should not change the server state.
- `Idempotent` methods means if two identical requests are made they should get an identical response.
- `Cacheable` means the client should be able to cache the response.

**Example HTTP Request**

> POST /api/note HTTP/1.1

> Host: api.example.com

> Origin: www.example.com

> Authorization: Bearer bHVsIHRoaXMgaXMgYSBmYWtlIHNlY3JldCB0b2tlbg==

> Accept: application/json

> Content-Type: application/json; charset=UTF-8

> Content-Length: 58

> {"title":"kata","content":"get 100 points on hacker rank"}

----------

**Example HTTP Response**

> HTTP/1.1 200 OK

> Date: Tue, 22 Aug 2017 06:34:16 GMT

> Content-Type: application/json; charset=UTF-8

> Content-Encoding: UTF-8

> Content-Length: 82

> Last-Modified: Mon, 21 Aug 2017 12:10:38 GMT

> Server: Apache/1.3.3.7 (Unix) (Red-Hat/Linux)

> ETag: "3f80f-1b6-3e1cb03b"

> Connection: close

> {"id":"1234123412341324","title":"kata","content":"get 100 points on hacker rank"}

-----------

## REST
*Representational State Transfer*

|REST Method	|CRUD Operation	|Function|
|-------|-------|-------|
|GET	|READ	|Retrieve 1 or More Records|
|POST	|CREATE	|Create a new record|
|PUT	|UPDATE	|Update a record through replacement (Put it back)|
|PATCH	|UPDATE	|Update a record (just the parts that changed|
|DESTROY	|DELETE	|Remove a record|

- Most **REST** endpoints will deliver data in **JSON** format. 



