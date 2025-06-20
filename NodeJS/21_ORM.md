# Sequelize ORM

## 1. Sequelize 설치하기
- [Sequelize](https://sequelize.org/docs/v6/)
- npm install --save sequalize

## 2. Schema 생성
- DB 접속
```javascript
import SQ from 'sequelize';

const sequelize = new SQ.Sequelize('데이터베이스명', '접속관리자', '비밀번호', {
    host: '접근주소',
    dialect: 'mysql',
    logging: false,   // 데이터베이스 로그 끄기
});

// DB 연결 확인
sequelize.sync().then((client) => {
    console.log(client);
})
```

- 테이블 생성
```javascript
import SQ from 'sequelize';

const DataTypes = SQ.DataTypes;

const 테이블명 = sequealize.define('테이블명', {
    id: {
        type: DataTypes.INTEGER,
        autoIncrement: true,
        allowNull: false,
        primaryKey: true,
    },
    필드명: {
        type: DataTypes.STRING(128),
        allowNull: false
    },
    url: DataTypes.TEXT,
}, { timestamps: false }); // createAt, updateAt 자동 생성 끄기
```

```javascript
//  조건 탐색
테이블명.findOne({where: {username: username}});
테이블명.findByPK(id).then(data => {
    // data.destroy();
    return data.save(); // Promise로 리턴
})

// 데이터 생성
테이블명.create(user).then(data => {
    console.log(data);
    return data; 
});
```
- FK 생성 및 처리
```javascript
import SQ from 'sequelize';

테이블명2.belongsTo(테이블명1)
```

```javascript
테이블명.findAll().then((data) => {});

// 중첩된 데이터까지 가져오기
const Sequelize = SQ.Sequelize;
테이블명.findAll({
    attributes: [
        '필드명1', ...,
        [Sequelize.col('user.name'), 'name'], // user.name의 값을 name으로 flat 하게 처리
        ...
    ],
    include: {
        model: User,
        attributes: []
        where: {username: username}
    },
    order: [['createdAt', 'DESC']]   // 순서 설정
})
```

