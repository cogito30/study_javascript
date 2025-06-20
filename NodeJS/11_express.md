# Express

## Express 주요포인트
- [express](https://expressjs.com/en/5x/api.html)
- get, post, put, delete, all, use
```javascript
const exprees = require('express');
const app = express();

app.get('/posts', (req, res, next) => {
    res.send(...);
});


app.listen(8080);
```

- express는 middleware의 연속

## 
- npm init --yes
- npm install express
- "start":  "nodemon app"
- "type": "module"
- npm i nodemon --save-dev

## 
- app.get('/sky/:id', (req, res, next) => {});

## request 알아보기
- path
- headers
- params
- query

## response 알아보기
- setHeader({'key':'value'})
- send()
- json()
- sendStatus(200)
- status(201).send(messgae)

## middleware 특징
- 등록 순서가 중요
- callback을 여러개 등록 가능
- next() 호출을 해야 다음 callback으로 넘어감
- next('route')로 다음 middleware로 넘어감
- next(new Error('error'))로 에러 전달
- app.use((error, req, res, next) => {}) 반드시 구현
- callback 당 1개의 send만 가능. return 추가 필요

(all vs use 차이)
- all: 정해진 특정 경로에 의해서만 호출
- use: 하위 경로 모두 호출

## post 처리
- req.body 사용
- app.use(express.jsoin()) 필요

## Error 처리(동기, 비동가)
- 동기적인 경우 에러처리 하지 않는 문제. try-catch 사용할것
- Promise 비동기 처리의 경우 catch로 처리 필요
- await, async 사용시 try-catch 사용
- express5부터 Promise에 error handler 이용 가능
- express5 이전의 경우 npm i express-async-errors 설치하여 처리

## 비동기 에러 처리(express5)
- async-await은 처리 가능
- Promise는 처리 불가. return, async를 붙여줌

## Router
- router 폴더 생성
- 모듈성 있게 작성
- app.route(경로).get((req, res, next) => {}).post()...
```javascript
- app.use('/경로', postRouter)
```
```javascript
import express from 'express';

const router = express.Router();

router.get('/', (req, res) => {
    ...
});

export default router;
```

## 유용한 Middleware
- app.use(express.json)는 RESTAPI -> BODY
- app.use(express.urlencoded({ extended: false }))는 HTML Form -> Body
- app.use(express.static('public', options))은 해당 폴더의 파일을 읽어서 제공
```javascript
const options = {
    dotfiles: 'ignore',
    etag: false,
    index: false,
    maxAge: '1d',
    redirect: false,
    setHeaders: function (res, path, stat) {
        res.set('x-timestamp', Date.now());
    },
};
```
## CORS?
- Cross-origin resource sharing: 다른 IP일때 데이터 금지
- Access-Control-Allow-Origin을 Headers에 추가
```javascript
app.use((req, res, next) => {
    res.setHeader('Access-Control-Allow-Origin', 'http://...');
    res.setHeader('Access-Control-Allow-Methods', 'OPTIONS, GET, POST, PUT, DELETE');
    next();
});
```

- npm install cors
- app.use(cors({
    origin: ['http://127.0.0.1:5500'],
    optionsSuccessStatus: 200,
    credentials: true,      // Access-Control-Allow-Credentials: true
})) 등록

## 외부 Middleware
- app.use(express.json())으로 req.bocy
- app.use(cookieParser()) 등록으로 req.cookies 확인
- req.cookies로 확인
- morgan: 요청에 대한 정보를 로그로 남김
- app.use(morgan('combined'));
- helmet: 
- app.use(helmet())