# 06. Debugging

## Debugging
- 디버깅: 코드에서 문제가 발생할 부분을 예상하여 버그를 찾고 문제를 해결하는 과정
- 디버깅에서 문제정의가 중요
- 원하는 목표와 현재 상태의 차이를 줄여가는 과정
- logic, performance, costs를 개선
- unit test, integration test, control flow analysis, log file analysis, interactive debugging, profiling

## VSCode Debugger
- 원하는 코드 라인에 breakpoint를 설정
- Run and Debug를 실행
- 다음 breakpoint로 이동/step over(코드 한줄씩 진행, 함수 호출만)/step into(함수내부로 진입)/step out(함수외부로 나옴)/재시작/정지
(좌측 패널)
- variables: 변수의 값 확인
- watch: 관심있는 변수 관찰 가능
- callstack: 호출된 함수 순서 확인
- load script: 로딩된 스크립트
- breakpoint: 브레이크 포인트 목록

## 디버거 팁
- 실시간으로 데이터(변수값)를 변경해가면서 확인
- watch에서 조건을 설정하여 값 확인
- breakpoint에서 우클릭으로 edit breakpoint로 조건 설정/호출횟수 설정

## 자동 재시작
- `create a launch.json`을 생성

(launch.json 설정)
```javascript
{
    "version": "0.2.0",
    "configurations": [ 
       {
            "type": "pwa-node",
            "request": "launch",
            "name": "Launch Program",
            "skipFiles": [
                "<node_internals>/**"
            ],
            "program": "${workspaceFolder}/3-debug/main.js",
            "runtimeExecutable": "nodemon"
            "restart": true,
        }
    ]
}
```

+) runtimeExecutable의 PATH 에러시 runtimeExecutable에 "${workspaceRoot}/debug/node_modules/.bin/nodemon"입력