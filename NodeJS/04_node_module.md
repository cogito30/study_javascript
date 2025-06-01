# 04. Node Module

## 학습 문서
- [NodeJS Learn](https://nodejs.org/en/learn/getting-started/introduction-to-nodejs)
- [NodeJS Documentation](https://nodejs.org/docs/latest/api/)
- [](https://github.com/DefinitelyTyped/DefinitelyTyped/blob/9d59b7aadafb5ee2afac9c4440b82e692a7449c1/types/node/globals.global.d.ts)
 -[타입 정의](https://github.com/DefinitelyTyped/DefinitelyTyped/blob/9d59b7aadafb5ee2afac9c4440b82e692a7449c1/types/node/globals.d.ts#L97)

## global object
- browser에서는 window가 글로벌 객체
```javascript
console.log(global);

global.hello = () => {
    global.console.log("hello");
}
global.hello();
```

(타입 정의)
- [global 정의](https://github.com/DefinitelyTyped/DefinitelyTyped/blob/9d59b7aadafb5ee2afac9c4440b82e692a7449c1/types/node/globals.global.d.ts)
 -[타입 정의](https://github.com/DefinitelyTyped/DefinitelyTyped/blob/9d59b7aadafb5ee2afac9c4440b82e692a7449c1/types/node/globals.d.ts#L97)


```javascript
```