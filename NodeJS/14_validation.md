# Validation

- validation: 클라이언트가 서버에게 보내는 데이터가 유효한지, 정확한지 확인하는 과정

## Validation 라이브러리
- npm i express-validator
- handler는 배열 형태로 여러가지 등록 가능
- chainig으로 검사 가능
```javascript
import { body, validationResult } from 'express-validator';

app.post('/users', body('name').notEmpty().withMessage('name error').isLength({min: 2, max: 10}).withMessage('Error message'), (req, res, next) => {
    const errors = validationResult(req);
    if (!errors.isEmpty()) {
        return res.status(400).json({message: errors.array() });
    }
    res.sned("success");
});
```

```javascript
import { body, validationResult } from 'express-validator';

[
    body(필드명).notEmpty().withMessage('empty error')
        .isLength({ min: 2, max: 5}).withMessage('length error'),
    body(필드명).notEmpty()
        .isInt().withMessage('not integer error',)
    body(필드명).isEmail().withMessage(),
    body(필드명.필드명).isEmail().withMessage()
]

[
    param(필드명).isEmail().withMessage('이메일 입력')
]
```

## 리팩토링

```javascript
cosnt validate = (req, res, next) => {
    const errors = validationResult(req);
    if (errors.isEmpty()) {
        return next();
    }
    return res.status(400).json({ message: errors.arrya()[0].msg });
}

[
    body(필드명).notEmpty().withMessage('empty error')
        .isLength({ min: 2, max: 5}).withMessage('length error'),
    validate
]
```

## Sanitization
- 데이터를 표준화에 맞도록 변경. 유효성 검사전에 실행
- 공백 제거

```javascript
body(필드명).trim()
body(필드명).isEmail().withMessage('이메일 오류').normalizeEmail()
```

## 실습
- post, put 처리. 서버에서 정하는 규칙에 따라 달라짐
- middleware 폴더에 vlidator.js 생성
- 서버에서 validation을 통해 데이터서버 접근전 네트워크 시간/비용 절감
- sanitization과 normalization으로 데이터를 일관성 있게 보관
+) Contract Testing: Client와 Server간 테스트시 규격을 맞추는지
+) Proto-based Testing