# MongoDB

- Document 타입의 데이터베이스

## 1. MongoDB 설치하기
1) [MondoDB](https://www.mongodb.com/) 접속
- Community Server와 Compass 다운로드
- MondoDB Atlas에서 프로젝트 생성
2) [MongoDB Atlas](https://www.mongodb.com/products/platform/atlas-database)에서 프로젝트 생성
- 클러스트 설정
- Database Access 설정
- Network Access로 접속 IP 설정
- Cluster에 Connect 설정


## 2. NodeJS에 [MondoBD Atlas](https://www.mongodb.com/docs/drivers/node/current/quick-start/)를 연결
- Drivers의 NodeJS DOC 확인하기
1) mondobd 설치하기
- npm install mongodb

- mongodb 연결
```javascript
import MongoDb from 'mongodb';

let db;
const mongoDb = MongoDb.MongoClient.connect(url)
                .then((client) => { db = client.db(); });

mondoDb.then(db = > {console.log('init')}).catch(console.error);
```
- Collection 조작하기
```javascript
// 데이터 찾기
let query = {필드명: 값};
db.collection('컬렉션명').findOne(query, options).then((data) => {
    console.log(data);
    return data;
})

// id로 document 찾기: _id, OjbectId 주의하기
db.collection('컬렉션명').findOnd({ _id: new MongoDb.ObjectId(id) })
    .then((data) => {
        console.log(data);
        return {...data, id: data._id};
    })

// 데이터 추가
db.collection('컬렉션명').insertOne(user).then((data) => {
    console.log(data);
    return data.insertedId.toString();
})

// update 사용시 반환이 되지 않으므로 findOneAndUpdate 사용
db.collection('컬렉션명').findOneAndUpdate(
    { _id: new ObjectId(id) },
    { $set: { text }},
    { returnDocument: 'after' }
).then((result) => result.value);

// 삭제
db.collection('컬렉션명').deleteOne({ _id: new ObjectId(id) });
```
- Join Table 사용: 데이터 중복을 관계보다 우선시함
```javascript
db.collection('컬렉션명').find().sort({필드명: -1}).toArray().then((data) => {
    console.log(data);
    return data;
})
```
