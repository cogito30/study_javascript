# NPM

## NPM
- npm(node package manager): 라이브러리/패키지 관리자
- `npm init` 사용시 pakage.json 생성
- `npm install <pakcage>`로 라이브러리 설치. node_modules 폴더 생성
- 프로젝트 업로드시 node_modules 제외하고 pakage.json만 포함
- `npx`는 설치 없이 바로 실행
- `yarn`은 meta에서 개발한 npm 대체제

(npm 명령어)
```javascript
npm
npm -v  // 버전 확인
npm int --yes // package.json 생성
npm run <명령어>
npm i -h // 명령어 옵션 확인
npm i -g <package> // 전역으로 설치
npm list // 설치 패키지 목록 확인(현재)
npm list -g // 설치 패키지 목록 확인(전역)
npm list -g --depth=0// 설치 패키지 목록 확인(깊이 설정)
```

(pakage.json)
```javascript
"scripts" : {
    "start": "node app",
}
```

+) [npm CLI](https://docs.npmjs.com/cli/v7/commands)

## software license
- 라이센스 종류: ISC, Apache
+) [spdx](https://spdx.org/licenses/)
+) [license](https://www.olis.or.kr/license/Detailselect.do?lType=spdx&lId=1074)

## library version
- 버전 정보: Major.Minor.Pathc
- Patch: 이슈 및 오류 수정
- Minor: 기능 추가
- Major: 새로운 기능 대거 수정 및 개선 버전

+) [npm SemVer Calculator](https://semver.npmjs.com/)
+) [semantic versioning](https://docs.npmjs.com/about-semantic-versioning)

## npm 라이브러리 설치
- major 변경 업데이트시 확인 필수

(npm 라이브러리 설치 명령어)
```javascript
npm view <package> // 라이브러리 정보 확인
npm i <package>@<version> // 특정 버전 설치
npm uninstall <package> // 라이브러리 삭제
npm un <package> // 라이브러리 삭제
npm view <package> // 업데이트 정보 확인
npm outdated // 업데이트가 필요한 버전 확인
npm update <package> // 라이브러리 업데이트
```

## 개발 모드 환경
- nodemon: 변경시 자동 재시작 라이브러리
- 개발시 필요한 라이브러리는 --save-dev로 추가

```javascript
npm view nodemon
npm i --save-dev nodemon
```