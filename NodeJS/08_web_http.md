# Web 기본

## 소개
- HTTP/HTTPS/HTTP(v1)/HTTP(v2)/HTTP(v3) 특성
- Request/Response
- Status Code
- Request URL, Method
- HTTP Headers, Session & Cookies

## HTTP/HTTPs
- HTTP(Hypertext Transfer Protocol)
- HTTP는 Request/Response로 구성된 protocol
- HTTPS(HTTP Secure): 데이터 전송시 SSL/TLS로 암호화
- HTTP(1098) - HTTPS(1994) - HTTP:v1(1997) - HTTP:v2(2015) - HTTP:v3(2019-)

(HTTP: v1)
- HTTP + HTTPS
- text-based
- uncompressed headres
- one file at a time

(HTTP: v2)
- HTTP + HTTPS. 대부분 HTTPS로 동작
- binary based protocol
- header compression
- multiplexing
- stream prioritization

(HTTP: v3)
- HTTPS
- TCP -> UDP로 개선

(정리)
- 3way-hand shaking
- request/response message 구조
- HTTP 버전별 특징

## Status Code
- 상태코드는 처리된 정보에 대한 결과를 의미
- 1xx: Informational
- 2xx: Successful
- 3xx: Redirection
- 4xx: Client error
- 5xx: Server error

(주요 상태 코드)
- 1xx: 100(Continue), 102(Processing)
- 2xx: 200(Ok), 201(Created), 204(No Content)
- 3xx: 301(Moved Permanently), 302(Fount), 303(See Other, get요청), 307(Temporary Redirect), 308(Permanent Redirect)
- 4xx: 400(Bad Request), 401(Unauthorized), 403(Forbidden), 404(Not Found), 405(Method Not Allowed), 409(Conflict)
- 5xx: 500(Internal Server Error), 502(Bad Gateway), 503(Service Unavailable)

+) [HTTP Response Status Code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status)
+) [HTTP Status Code](https://developer.mozilla.org/ko/docs/Web/HTTP/Reference/Status)

## Request Method
- URL(Uniform Resource Locator): 서버 요청시 특정 요청의 경로
- URL 구조: scheme(=protocol)://domain(=hostname)::port/path?parameters(=query)#fragment
- request method: get, post, put, delete, patch, head, options, trace
- get status code: 200, 401, 403, 404, 405
- post status code: 201, 401, 403, 404, 409
- put/delete/patch status code: 200, 204, 403, 404, 405
- head/options/trace: 200, 401, 403, 404, 405
- 서버 데이터 변경하지 않는 요청: get, head, options, trace
- 서버 데이터 변경 요청: post, put, delete, patch
- get(safe, idempotent, cacheable)/post(cacheable)/put(idempotent)/patch

+) [HTTP Request Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods)
+) [HTTP Request Methods](https://developer.mozilla.org/ko/docs/Web/HTTP/Reference/Methods)
+) [멱등성](https://developer.mozilla.org/ko/docs/Glossary/Idempotent)

## HTTP Headers
- Headers안에 Standard와 Custom(X- 대신 domain-key) 사용
1) Stateless Protocol
2) Sessions && Cookies: set-cookie, cookie, cache-control, user-agent, authorization, content-length, content-type, content-language

+) [HTTP Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers)
+) [HTTP Headers](https://developer.mozilla.org/ko/docs/Web/HTTP/Reference/Headers)