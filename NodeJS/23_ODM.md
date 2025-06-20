# mongoose ODM

## 1. Mongoose 설치하가ㅣ
- [mongoose](https://mongoosejs.com/docs/guide.html) 
- npm install mongoose

## 2. DB 접속
```javascript
import Mongoose from 'mongoose';

// mongoose 두번쨰 인자는 4.x 이후 생략 가능
const mongoose = Mongoose.connect(url, {
    useNewUrlParser: true,
    useUnifiedTopology: true,
    useFindAndModify: false
});

mongoose.then(() => {
    console.log('init');
})
```
- Schema 생성
```javascript
const 컬렉션명Schema = new Mongoose.Schema({
    필드명1: {type: STring, required: true},
    필드명2: {type: STring, required: true},
    url: String
}, { timestamps: true}); // createdAt, updatedAt 자동 추가

// _id -> id. 읽어올 때 가상의 요소 적용. 저장되지 않음
컬렉션명Schema.virtual('id').get(() => {
    this._id.toString();
})
컬렉션명Shema.set('toJSON', {virtuals: true}); // JSON 변환시 설정 추가
컬렉션명Schema.set('toObject', {virtuals: true});

// 모델 생성
const 컬렉션명 = Mongoose.model('컬렉션명', 컬렉션명Schema);
```
- Table 조회
```javascript
컬렉션명.findOne({ username });
컬렉션명.findById(id);
컬렉션명(데이터).save().then((data) => {
    data.id;
});
컬렉션명.find({필드명}).sort({필드명: -1});
컬렉션명.findByIdAndUpdate(id, {text}, { returnOriginal: false}); // returnOriginal로 업데이트 반환 설정
컬렉션명.findByIdAndDelete(id);
```