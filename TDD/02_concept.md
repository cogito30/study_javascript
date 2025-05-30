# 테스트 개념

## 소개
- 테스트 종류: Unit Test, Functional Test, Integration Test, Component Test, Contract Test, E2E Test, A/B Test, Stress Test
- 테스트란
- 테스트 적용 시기 및 이유
- Test Pyramid
- TDD
- CI/CD

## Test란
- Testing: 제품(함수, 기능, UI, 성능, API 스펙)이 예상하는대로 동작하는지 확인 및 검증하는 과정

## Test 시기
- Dev -> QA -> Publish
- 개발과 동시에 테스트 작성시 자동화/시간절약/높은 커버리지의 장점이 있음

## Test 장점
1) 기능 정상 동작 확인
2) 요구사항 만족
3) 이슈에 대해 예측 가능
4) 버그를 빠르게 발견
5) 리팩토링 편리
6) 손쉬운 유지보수
7) 코드 품질 향상
8) 코드간 의존성의 낮춤
9) 좋은 문서화
10) 시간을 절약

## Test Pyramid
1) Unit Test: 함수, 모듈, 클래스 단위 테스트
2) Integration Test: 모듈들, 클래스들 묶음 테스트
3) E2E Test: UI 테스트, 사용자 테스트
- 숫자가 커질수록 Cost 증가
- 숫자가 커질수록 Speed 감소

## TDD
- TDD(Test-Driven Development): 개발전 테스트 코드를 먼저 작성
- Write the test -> Run Tests -> Write only enough Code 반복
- 완료 후 리팩토링
- 요구사항 분석 및 이해 -> 설계 -> TDD
- 장점: 모든 요구사항에 대해 점검/사용자 입장에서 코드를 작성(인터페이스 위주), 시스템 전반적인 설계 향상

## TDD 사용할 때
1) 요구사항이 명확할 떄
2) 비즈니스 로직일 경우
3) 협업시 명세서(문서) 역할
4) 설계에 대한 고민이 필요
5) merge전 테스트 코드 작성
6) 사용자에게 배포하기 전

## CI/CD
- Code > Build > Test > Release > Deploy
(Continuous Integration: 지속적인 통합)
1) 코드 변경 사항을 주기적으로 빈번하게 merge
2) 통합을 위한 단계(build, test, merge)의 자동화
=> 코드의 퀄리티 향상, 개발 생산성 향상, 버그수정 용이, 문제점을 빠르게 발견

(Continuous Delivery/Deployment: 지속적인 제공/배포)
1) Prepare Release
2) Deploy Release
- Jekins/Buildkite/GitHub Actions/GitLab CICD/CircleCi