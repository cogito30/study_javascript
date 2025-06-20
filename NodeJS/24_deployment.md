# Deployment

## 1. 배포시 체크목록
- configuration에 중요 설정이 노출되었는지
- 중요내용이 출력되지 않는지
- 불필요 데이터나 민감한 내용을 응답하지 않는지
- API rate limit 설정

## 2. 배포시 기준 설정
- 필요요건: 웹서버/static hosting, 데이터베이스, CDN, File Storage, TLS, Location
- 운영기준
  - DIY: GCP, AWS, MS Azure
  - Full managed: Heroku, platform.sh, netlify

## 3. 배포
- frontend: HTTP v2 지원, CSR, Redirects -> netlify
- backend: HTTP v2 지원, NodeJS, MYSQL -> platform.sh
- cors 변수 설정

## Platform.sh
1) [platform.sh](https://platform.sh/) 접속
2) create empty project로 프로젝트 생성
3) CLI 복사해서 실행 
```
curl -sS https://platform.sh/cli/installer | php
```
4) SSH 키 등록
- 폴더내에서 키 생성
```
ssh-keygen 
```
- 키 복사
```
cat platform.sh.pub
```
5) 웝격 platform.sh 원격 설정
```
platform project:set-remote ...
```
6) YAML 설정 파일 생성
7) services.yaml 파일 설정
8) .platform.app.yaml 파일 설정
- NGINX 사용시 
```yaml
web: 
    locations:
        '/':
            passthru: true
```
9) .platform/routes.yaml 파일 설정
- ws 추가
```
'https://www.{default}/ws':
  type: upstream
  upstream: '프로젝트:http'
  cache:
    enabled: false
```
10) commit후 push
11) 환경변수 설정
- 환경변수 정보 확인
```
platform relationship
```
- platform.sh 사이트에서 settings의 variables 설정
- 로그 남기기
```
platform logs
```

## Netlify
1) [netlify](https://www.netlify.com/)에 접속
2) netlify 다운로드
- react 배포 준비
```
npm run build
```
- netlify 배포
```
npm install netlify-cli -g
netlify deploy
```
- publish directory는 build로 설정 
```
netlify deploy --prod
```
4) platform.sh 환경변수 설정의 CORS_ALLOW_ORIGIN에 URL 등록

## Heroku
1) [Heroku](https://www.heroku.com/)에 접속
2) Heroku Git을 사용한 배포
- heroku cli 설치
- heroku cli 로그인
- heroku remote 연결
3) postgreSQL로 변경
- heroku는 MYSQL을 사용하지 않음
4) 데이터베이스(postgreSQL) 생성
- 무료 데이터베이스 생성후 확인
```
heroku addons:create heroku-postgresql:hobby-dev
heroku config  // postgres://<username>:<password>@<host>:<port>/<database name>
```
5) 환경변수 설정
- dashbord > 프로젝트 > settings > config vars에서 변수 등록
6) postgreSQL 설치
```
npm install pg pg-hstore
```
7) Sequelize 옵션 수정
```javascript
new SQ.Sequelize(database, user, password, {
    host,
    port
    dialect: 'postgres',
    logging: false,
    dialectOptions: {
        ssl: {
            required: true,
            rejectUnauthorized: false,
        }
    }
})
```
8) Procfile 생성 및 설정
```
web: node app.js
```
9) `git push heroku 브랜치명:master`로 업로드
10) `heroku logs`로 서버 시작 확인