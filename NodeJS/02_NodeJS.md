# 02. NodeJS

## NodeJS
- V8(JIT 지원)
- NodeJS: V8 엔진을 이용한 JavaScript runtime 환경
- Frontend(Web APIs): React, Vue, Svelte
- Backend(Node APIs): Express, Nest

## NodeJS 장점
1) JavaScript로 브라우저와 서버 모두 구현 가능
2) NodeJS 사용량이 높음
3) 대기업이 NodeJS 사용: kakaoTalk, coupang, naver, ebay, netflix, uber, reddit, aws, nasa
4) 러닝 커브가 낮고 생산성이 좋고 성능이 좋음
5) 커뮤니티가 존재
6) 많은 도구(라이브러리)들이 존재: npm으로 다운로드

## 노드의 4가지 특징
1) JavaScript Runtime: V8 엔진, C++ 사용
2) Single Thread
3) Non-Blocking I/O
4) Event-Driven
=> I/O 처리에는 적합, CPU에는 적합하지 않음(NodeJS12+부터 worker threads 지원)

## 노드 동작 방식(내부 구조)
- NodeJS App: Memory Heap + Call Stack
- Node APIs(Multi-Thread): setTImeout, http, file, event
- Task Queue: callback을 넣어두는 장소
- Event Loop: Call Stack이 비어있을 때 Task Queue의 요소를 가져옴
=> callback 코드는 가벼운 일들만 작성되어야 함

(NodeJS APIs가 가진 모듈)
- JavaScript Engine: V8(c++)
- Non-Blocking I/O: Libuv(c)
- HTTP parsing: llhttp(TypeScript, c)
- tls, crypto: Open SSL(c)
- async DNS request: c-ares, zlib


## 노드 서버의 장/단점
- Traditional Server: Thread Pool을 가지고 요청마다 Thread 생성
- NodeJS Server: 요청이 들어올 경우 필요한 일을 처리하는 곳에 위임하여 처리
- Node로 무거운일 처리시 분산처리 혹은 aws lambda 활용