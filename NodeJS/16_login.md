# Login 구현

1. session
2. jwt

(jwt 사용 이유)
- restful api 서버(다양한 클라이언트를 위함)
- MSA/분산형 시스템일 경우 서비스 확장성을 위함
- 서버 확장이 쉬워짐

## Login 설계 및 구현
1) Rest API 디자인하기
- signup/signin(login)/me(기존 토큰 검사)
2) Postman 셋업
3) Rest API 구현하기
4) Auth 미들웨어 구현하기
5) User Tweets 모델 분리하기