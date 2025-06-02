# 19. DataBase

## Intro
- Database 개념과 종류
- SQL, RDB
- NoSQL 종류
- ORM/ODM
- SQL vs NoSQL

## Database
- 컴퓨터 File System에서 관련 있는 것들끼리 모아둔 것
- Flat-File Database -> DBMS
- Flat-File: 파일마다 데이터를 저장해서 사용. Simpe Data
- DBMS: 데이터를 저장하고 찾고 업데이트에 최적화. Optimise, complex data. security. concurrent access

(DBMS 종류)
- SQL(=RDBMS): schema(row+column). 데이터끼리 관계를 표현

```sql
SELECT * FROM 테이블 WHERE 조건
```

- NoSQL: schema가 정해지지 않음. Key-Value, Document, Wide-Column, Graph

- 해결하는 문제에 맞추어 Database 선택

## RDB와 쿼리 언어
- SQL Database는 row와 column으로 이루어진 Table로 구성됨
- Table의 열마다 각가의 데에터 타입 지정
- 여러가지 속성 지정
- record는 행별 데이터 하나를 의미
- schema
- ACID 특징: data integrity
- Primary Key, Foreign Key
- DBMS 종류: Oracle, SQLite, PostgreSQL, MySQL, MSSQL Server

(SQL)
```sql
SELECT * -- 어떤 행의 정보를 가져올지
FROM 테이블 -- 어떤 테이블인지
WHERE 조건 -- 필터링 조건
```

## NoSQL
- Object형 테이터베이스 탄생 - > Big Data 처리
- NoSQL: schema-less / Non-relatinoal / Address specific problems
- NoSQL 종류: Key-Value(dynamoDB, Redis) / Document(mongoDB) / Wide-Column(cassandra, cloud bigtable) / Graph(neo4j)
- MondoDB는 Document와 Collection으로 구성
- 정보 저장시 일관성 필요


## ORM / ODM
(ORM: Object Relational Mapping)
- ORM은 Code상의 Schema 정의를 DB에 자동으로 생성하고 기록
- ORM은 DataBase를 추상화
- ORM 장점: 비즈니스 로직에 집중. 반복된 쿼리 감소. 데이터베이스 추상화. 스키마 변경시 자동 migration
- ORM 단점: 복잡한 SQL 작성이 어려움. ORM별로 사용법이 다름. SQL 성능 및 최적화가 DB에 비해 낮음
- ORM 종류: TypeORM, Sequelize, Prisma

(ODM: Object Document Mapping)
- Object를 Document로 매핑하여 사용
- ODM 종류: mongoose

## SQL vs NoSQL

| 기준 | SQL | NoSQL |    
| :---: | :---: | :---: |    
| Getting Started | Medium | Easy |    
| Data Structure | Rigid/Fixed | undefined/Flexible |    
| Data Lookup | Easy | Easy |    
| Aggregate Queries | Easy | Difficult |    
| Sliciing & Dicing Data | Easy | Difficult |    
| RUnning cost | costly | cheap |

- Scaling: Vertical Up/Down, Horizontal Out/In

(DB 선택 기준)
1) Data Type
2) Data의 양
3) Data가 서로 관계가 있는지

- SQL 사용 예시: Accounting Software / E-Commerce Platforms / Customer Relationship Software(CRM)
- NoSQL 사용 예시: Social Network(Graph) / Distributed cache(Key-Value) / content management systems(Document) / Real-time analytics(Wide-Column)
- Hybrid approach: 필요에 따라 부분적으로 사용