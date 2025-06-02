# Rest API

## intro
- RestfulAPI 개념
- Restful System 6가지 원칙
- Desinging APIs

## RESTful API
- REST(Representational State Transfer): HTTP 메서드를 사용해서 URL을 디자인 하는 것
- api(Application Programming Interface): 사용하는 사람들이 쉽게 사용할 수 있는 인테페이스
- Software Architectural Style, Web Service Guidelines
- 네트워크 기반의 소프트웨어 아키텍처 정의

(RESTful System 6가지 가이드라인)
1) Client-Server Architecture: 서버는 다양한 클라이언트에 데이터 제공
2) Statelessness: 하나의 요청이 다른 요청과 연결되지 않게 독립적
3) Cacheability
4) Layered System: 공통된 API로 서버에 무관하게 지원
5) Code on demand:
6) Uniform interface
- 3, 4번은 HTTP와 동일한 특성

(Uniform Interface 4가지 특징)
1) Resource Identification in requests: 클라이언트 요청에서 서버의 어떤 데이터를 원하는지 식별 가능해야 함. 데이터 저장 형식과 별개로 클라이언트에 맞는 포맷으로 데이터 전송
2) Resource manipulation through representations: 받은 데이터를 처리하는 방법을 알 수 있어야 함
3) Self-descriptive messages: 클라이언트가 데이터를 어떻게 처리할 수 있는지 포함되어야 함
4) Hypermedia as the engine of application state(HATEOAS)

## Web APIs 디자인
- CRUD 동작 방식에 대한 
- Action(verb): Create(Post), Read(Get), Update(Put), Delete(Delete)
- What/Item(noun): 어떤 데이터, 어떤 도메인
- API 이름에는 action에 대한 이름 생략. 무엇을 할 것인지(what)만 사용
- what은 명확하게 작성하고 세부사항은 query를 작성

## RestAPI 예제 
- [Youtube Data API](https://developers.google.com/youtube/v3/docs/videos/list)
- [GitHub REST API](https://docs.github.com/en/rest?apiVersion=2022-11-28)
