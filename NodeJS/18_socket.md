# Socket

- 실시간 동작
- HTTP는 Request/Response 방식. 요청이 있는 경우만 응답 전송
- Web Socket: Connection 생성되고나면 실시간을 양방향 데이터 전송 가능

## 기본 소켓 사용법
- 서버 설치: npm install socket.io
- 클라이언트 설치: npm install socket.io-client

(server)
```javascript
const server = app.listen(config.host.port);
const socketIO = new Server(server), {
    cors: {
        origin: '*',
    },
};

socketIO.on('connection ', (socket) => {
    console.log('Client is here');
    socketIo.emit('dwitter', 'Hello'); // 주제별 내용
})
```

(client)
```javascript
import socket from 'socket.io-client';

const socketIo = socket(baseURL);
socketIo.on('connect_error', (error) => {
    console.log('socket error', error);
});

socketIO.on('dwitter'. (message) => {
    console.log(message);
})
```

## broadcast