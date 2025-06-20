# Authentication

- 로그인, 인증
- 인증, 인증 방법 2가지
- 세션과 쿠키
- JWT 장단점과 구현 방법
- bcrypt로 안전한 패스워드

## 
- Authentication(인증, 로그인)
- HTTP는 Stateless 프로토콜
- Session: HTTP Only. 안전, Stateful
- Cookies: 
- JWT: JSON(Header + Payload + signature). stateful. 분산형 서버일 경우 session처럼 서버 통신 불필요
  - Headers: Authorization: Bearer JWT
  - 단점: 보안 위험성
- bcrypt: password-hashing function(algorithm + cost + salt/base64 + Hash). 암호화에만 이용. 역변환 불가
  - salt

## bcrypt 실습
- npm install bcrypt
- 길이는 8/10/12 추천
- [salt 길이별 성능](https://auth0.com/blog/hashing-in-action-understanding-bcrypt/)
```javascript
const bcrypt = require('bcrypt');

const password = 'abcd1234';
const hashed = bcrypt.hashSync(password, 10);
const result = bcrypt.compareSync(password, hashed); // 검사
```

## JWT 실습
- npm install jsonwebtoken
- [jwt](https://jwt.io/)
- 32byte의 키 권고
- 만료시간 설정 필수
```javascript
const jwt = require('jsonwebtoken');

const token = jwt.sign({
    id: 'userId',
    isAdmin: true, 
}, 'secretkey', {
    expiresIn: 2
})

jwt.verify(token, secretkey, (error, decoded) => {
    console.log(error, decoded);
})
```