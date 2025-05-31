# 03. Unit Test

## Unit Test
- Test Runner + Assertion
- Test Runner: 테스트를 실행하 결과 확인(Mocha)
- Assertion: 테스트 조건, 비교를 통한 테스트 로직(Chai, expect.js, better-assert)
- Jest는 Test Runner + Assertion

## [Jest](https://jestjs.io/)
- 설정없이 간편한 사용, snapshots, 독립적 테스트
1) 환경설정
- `npm init --yes`하면 package.json 생성
- `npm install jest --global`
- `jest --init`하면 jest.config.js 생성
- `npm install --save-dev jest`을 개발 의존성에 추가

2) 테스트
- test 폴더를 만들어 `파일명.test.js` 추가
- `npm install @types/jest`로 타입 확인 패키지 설치
- `jest.config.js`에서 collectCoverage 수정으로 테스트 커버리지 시각화 설정
- `npm run test`로 테스트 실행
- `jest --coverage`로 커버리지 확인


```javascript
const add = require('../add.js');

test('테스트명', () => {
    expect(테스트 내용).toBe(결과값);
});
```

- 각각의 테스트는 독집적으로 작성. 객체 생성시 beforeEach 사용
```javascript
beforeEach(() => {
    //객체 생성
});
```

```javascript
describe('테스트명', () => {
    it('테스트명', () => {
        ...
        expect(테스트내용).toBe(결과값);
    });
});
```

```javascript
describe('테스트명', () => {
    describe('테스트명', () => {
        it('테스트명', () => { 
            /// 테스트
        });
        it('테스트명', () => { 
            /// 테스트
        });
    });
});
```

- 에러발생
```javascript
it('테스트명', () => {
    ...
    expect(() => {
        // 에러 발생 코드
    }).toThrow(에러메시지);
});
```

- 비동기 테스트(Promise): 끝나는 시점 명시
- 비동기 테스트(Promise): done() 사용
```javascript
it('테스트명', (done) => {
    비동기함수().then(item => {
        expect(item).toEqual(결과값);
        done();
    });
});
```

- 비동기 테스트(Promise): return 사용
```javascript
it('테스트명', () => {
    return 비동기함수().then(item => {
        expect(item).toEqual(결과값);
    });
});
```

- 비동기 테스트(Promise): await 사용
```javascript
it('테스트명', async () => {
    const 반환값 = 비동기함수();
    return 반환값.then(item => {
        expect(item).toEqual(결과값);
    });
});
```

- 비동기 테스트(Promise): resolves/reject 사용
```javascript
it('테스트명', async () => {
    return expect(비동기함수()).resolves.toEqual(결과값);
});

it('테스트명', async () => {
    return expect(비동기함수()).rejects.toBe(결과값);
});
```

3) 자동 테스트
- `package.json`에서 `jest --watchAll` 추가하여 자동 재실행
- `jest --watch`사용시 변경된 내용만 테스트(git commit 되지 않은 파일만 수행)

## [Mock](https://jestjs.io/docs/mock-functions)
- Mock 함수 생성
```javascript
function check(fn1, fn2, fn3) {
    if (fn1()) {
        fn2('yes');
    } else {
        fn3('no');
    }
}
module.exports = check;
```

```javascript
describe('테스트명', () => {
    let func1;
    let func2;

    beforeEach(() => {
        func1 = jest.fn();
        func2 = jest.fn();
    });

    it('테스트명', () => {
        check(() => true, func1, func2);
        expect(func1.mock.calls.length).toBe(1);  // mock 함수 호출횟수
        expect(func1.mock.calls[0][0]).toBe('yes');  // mock 함수 전달인자
        expect(func1).toHaveBeenCalledTimes(호출횟수);
        expect(func1).toHaveBeenCalledWith(전달인자);
    });
});
```
