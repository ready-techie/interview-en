- REST/HTTP
- 면접질문 인기 리스트(?)에서 몇가지 추출

---

- `Memo`
  - Protocol based on TCP/IP communication
    - TCP/IP supports reliable connection
  - Request-responsive style: Client requests, server responses
  - Synchronous: Client waits server response
  - Stateless: This means a HTTP server needs not keep track of any state information
    - Server scalability
  - Methods: GET, POST, PUT, DELETE, HEAD, OPTIONS, TRACE, CONNECT
    - POST vs PUT: With POST, client cannot determine URL, so the server determines. (ex. Post twitter message). Client can determine URL via PUT (ex. Wiki), which means the resources can be overwritten if some exceptions are not handled. Because of this feature, using POST is preferred.
    - DELETE: (usually) doesn't have body on response
    - HEAD vs GET: GET gets resource, HEAD only gets header(meta-data) and does not include body on response
    - OPTIONS: responses the method list which the resource provides.
    - PATCH: considered a set of instructions on how to modify a resource (came out in 2010)
  - 멱등성 Idempotence: 어떤 조작을 몇 번을 반복해도 결과가 동일한 것 (PUT/DELETE/GET/HEAD)
  - 안전 Safe: 조작 대상의 리소스의 상태를 변화시키지 않는 것 / 조작대상인 리소스에 부작용이 없는 것 (GET/HEAD)

### HTTP?

`대본`

HTTP is a protocol based on TCP/IP communication. It has synchronous, stateless, and request-responsive style.

### HTTP Methods?

HTTP 메소드에 대해 아는 대로 말해주세요 ⇒ 9개 있다고 하고 주요2~4개 달달 외워야할듯..

`대본`

HTTP supports 9 methods (since 2010) and usually 2 of them are used.

GET, literally gets any resources requested.

POST, sends any data to Create or Update the data.

PUT, can update or override existing data.

DELETE, literally deletes

HEAD, only gets the data's header.

OPTIONS, responses the method list which the resource provides.

### HTTP Status Code?

HTTP Status code에 대해 아는 대로 말해주세요 ⇒ 대충 말하고 자주 나오는거 달달 외우기..

`대본`

Status code explains how server response on client request.

1xx: Processing (Status code starting with 1 means processing)

2xx: Success

- 200 OK - request succeeded
- 201 Created - Creating resource succeeded

3xx: Redirect

4xx: Client err

- 400 Bad request: message or parameters are wrong or any unknown status codes starting with 4
- 401 Unauthorized: tried redirection without proper authentication info
- 404 Not found: cannot find the requested resource, and includes message on response body

5xx: Server err

- 500 Internal server error: literally, includes message on response or any unknown status codes starting with 5
- 503 Service unavailable: cannot access server due to some server maintenance

### REST?

`대본`

REST, is one of a network system's architectural style for providing standards between computer systems on the web to communicate. Since it's based on HTTP protocol, it inherits features like statelessness, request-responsive.

REST also provides Cache,

Uniform interface, Request based on URL

Layered system: can add Load balancer or Proxy

Code on demand (optional): Download code from program server and process on client

### HTTP GET vs POST?

`대본`

By making a query string, including parameters, GET sends it through URL, which is visible.

POST sends data through HTTP message's body. So it's considered more safe.

### HTTP Communication Process? (Server-Client)

`대본`

User enters [www.google.com](http://www.google.com) on the address bar.

Browser prepares data packet based on HTTP protocol.

These packets are delivered to the region's ISP

as ISP also works as DNS, it checks [www.google.com](http://www.google.com) 's IP address

Browser knows [www.google.com](http://www.google.com)'s IP address is sth.sht~ and sends a HTTP request to that IP address

Google's web application server does some work.. and sends status codes & data that client requested, as HTTP response.

Now the client receives HTTP response, and changes the data into a proper structure.
