# DataBase(MYSQL)

## 1. MYSQL 설치하기
1) [MYSQL](https://www.mysql.com/downloads/) 접속
2) Community 버전 다운로드
  - MySQL Community Server와 MySQL Workbench 다운로드
3) 다운로드 파일 설치하기
4) MYSQL 실행 확인
- MacOS: System Settings > MYSQL에서 확인
5) MYSQL Workbench 실행

## 2. Schema 생성하기
1) Schema 탭에서 우클릭후 Create Schema로 Schema 생성
2) 생성된 Schema의 Tabels에 우클릭후 Create Table로 Table 생성
- Column/Datatype 설정
- PK(PrimanyKey)/NN(NotNull)/UQ(Unique)/BIN(Binary)/UN(Unsinged)/ZF(ZeroFill)/AI(AutoIncrease)/G 설정
3) Foreign Key 설정

## 3. Node에서 DB 다루기
1) mysql2 설치하기
- npm install mysql2
2) db
- db 폴더 생성
- database.js
- [MYSQL DOC](https://dev.mysql.com/doc/refman/8.0/en/)
- Node에서 DB에 연결하기
```javascript
import mysql from 'mysql2';

// 데이터베이스 관리 Pool 생성. MYSQL에 접속
const pool = mysql.createPool({
    host: 'localhost', // 접속 주소
    user: 'root',      // 접속 관리자
    database: '데이터베이스명',
    password: '비밀번호'
})

const db = pool.promise();

// 연결 완료시 출력
db.getConnection().then(connection => {
    console.log(connection);
});
```
- Table 조작하기
```javascript
// 테이블에 데이터 추가
db.execute('SQL 쿼리문')
db.execute('INSERT INTO 테이블명 (col1, ...) VALUES (?, ...)', [변수명, ...]).then((result) => {
    console.log(result);
    return result;
})

// 특정 데이터 선택 반환
db.execute('SELECT * FROM 테이블명 WEHRE 조건=?', [변수명]).then((result) => {
    console.log(result);
    return result;
})

db.execute('UPDATE 테이블명 SET col1=? WHERE id=?', [변수1, 변수2]).then(() => );

db.execute('DELETE FROM 테이블명 WHERE id=?')
```
- Join Table 사용하기
```javascript
db.execute('SELECT t1.col1, t1.col2, t2.col1 FROM 테이블1 as t1 JOIN 테이블2 as t2 ON t1.col1 = t2.col2 ORDER BY t1.col1 DESC').then((result) => {
    console.log(result);
})
```

