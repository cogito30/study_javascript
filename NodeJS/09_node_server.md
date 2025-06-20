# 09 Node Server

## HTTP/HTTP2
- http2는 https와 함께 동작
```javascript
console.log(http.STATUS_CODES);
console.log(http.METHODS);

const server = http.CreateServer((req, res) => {
    console.log('hello...');
    consol.log(req.httpVersion);
    consol.log(req.url);
    consol.log(req.method);
    consol.log(req.headers);

    const url = req.url;
    if (url === '/') {
        res.setHeader('Content-Type', 'text/html; charset=UTF-8');
        res.write('<html>');
        res.write('<head><title>Hello</title></head>');
        res.write('<body><h1>Courses</h1></body>');
        res.write('</html>');
    } else {
        res.write('Not Found');
    }
    res.end();
});

server.listen(8080);
```

```javascript
const read = fs.createReadStream()
read.pipe(res);
```


## Template Engine
- Template Engines을 사용하면 레이아웃의 뼈대만 구성해두고 클라이언트 요청시 서버에서 가지고 있는 데이터에 맞게 페이지를 동적으로 생성
- 종류: ejs, pug
- 복잡한 서버사이드 렌더링시 React + Next.js 사용
- [EJS](https://ejs.co/)
- 확장자를 html이 아닌 ejs로 변경
```
<%= 변수명 %>
<% courses.forEach(course => { %>
    <li><%= course.name %></li>
<% >}) %>
```
- npm install ejs
```javascript
const ejs = require('ejs');
const name = "lee";
const courses = [{name: 'HTML'}, {name: 'CSS'}];
ejs.renderFile('./template/index.ejs', {name: name}).then(data => res.end(data));
ejs.renderFile('./template/course.ejs', {courses: courses}).then(data => res.end(data));
```

## JSON 보내주기/받기
- 
```javascript
const url = req.url;
const method = req.method;
if (url === '/course') {
    if (method === 'GET') {
        res.writeHead(200, {'Content-Type': 'application/json'});
        res.end(JSON.stringify(courses));
    } else if (method === 'POST') {
        const body = [];
        req.on('data', chunk => {
            console.log(chunk);
            body.push(chunk);
        })

        req.on('end', () => {
            const bodyStr = Buffer.concat(body).toString();
            const course = JSON.parse(bodyStr);
            courses.push(course);
            console.log(course);
            res.writeHead(201);
            res.end();
        });
    }
}
```