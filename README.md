# 🔍 Project Testing Guide

<br>
> 이 문서는 본 프로젝트에서 수행하는 테스트의 목적과 범위를 정의하고,  
각 테스트가 어떤 방식으로 소프트웨어의 품질과 신뢰성을 보장하는지 설명합니다.  <br>
단위 테스트(Unit Test)부터 통합 테스트(Integration Test), 보안 및 성능 테스트,  
그리고 CI/CD 파이프라인 자체의 검증에 이르기까지 전 범위의 테스트 전략을 포함합니다. <br>
모든 테스트는 자동화된 DevSecOps 환경을 기준으로 설계되며, <br> 
코드 작성 → 빌드 → 배포 → 운영까지의 전체 라이프사이클에서 신뢰성 있는 품질 관리를 목표로 합니다.

<br>

## 😎 Team
<br>

|<img src="https://avatars.githubusercontent.com/u/71498489?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/95984922?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/150774446?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/153366521?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/127267532?v=4" width="150" height="150"/>|
|:-:|:-:|:-:|:-:|:-:|
|[PM] HanJH<br/>[@letsgojh0810](https://github.com/letsgojh0810)|[PL] nahong_c<br/>[@HongChan1412](https://github.com/HongChan1412)|Kim YeJin<br/>[@yeejkim](https://github.com/yeejkim)|Park ji hye<br/>[@parkjhhh](https://github.com/parkjhhh)|Seok Hye Jin [@HyeJinSeok](https://github.com/HyeJinSeok)|

<br>

## 🎯 목적

<br>

- 코드 단위의 기능 정확성과 변경에 따른 회귀(regression) 오류 방지
- 서비스 간 연동 및 데이터 흐름의 정상 작동 여부 확인
- 이미지 및 의존성 수준에서의 보안 위협 사전 탐지
- 대량 트래픽, 장시간 부하 등 실 운영 환경 시뮬레이션을 통한 시스템 검증
- 배포 파이프라인(CI/CD)의 자동화 신뢰성 및 운영 가능성 검증

<br>

본 테스트 전략을 통해 다음과 같은 결과를 기대합니다:

- 배포 전 문제를 조기에 발견하여 수정 비용 최소화
- 고가용성 및 확장성을 고려한 안정적인 아키텍처 보장
- 보안 사고 예방 및 신속한 대응 체계 수립
- 사용자 관점에서의 품질 높은 서비스 제공 실현

<br>

## 📋 테스트 분류별 정리표

<br>

### ✅ 코드 품질/검사 테스트

| 테스트 항목 | 설명 | 도구 |
|-------------|------|------|
| 단위 테스트 | 서비스, 도메인, 유틸 등 함수 로직 검증 | JUnit, Mockito |
| 통합 테스트 | Controller ↔ Service ↔ DB 흐름 검증 | @SpringBootTest |
| 정적 코드 분석 | 코드 스타일, 버그, 보안 취약점 탐지 | SonarQube |
| 테스트 커버리지 측정 | 테스트가 얼마나 코드를 커버하는지 수치화 | JaCoCo |

<br>

---

### ✅ 보안 테스트

| 테스트 항목 | 설명 | 도구 |
|-------------|------|------|
| 이미지 취약점 검사 | Docker 이미지의 취약점 탐지 | Trivy |
| 의존성 보안 검사 | 의존성 라이브러리의 보안 취약점 탐지 | OWASP Dependency-Check, Snyk |
| 시크릿 유출 검사 | Git 커밋 내 민감정보 노출 여부 탐지 | GitGuardian, Gitleaks |

<br>

---

### ✅ 성능 테스트

| 테스트 항목 | 설명 | 도구 |
|-------------|------|------|
| 부하 테스트 (Load Testing) | 일정 시간 동안 지속적인 요청 부하 | K6, JMeter, Locust |
| 스트레스 테스트 (Stress Testing) | 시스템 한계까지 부하를 가해 처리 능력 측정 | K6, Locust, Gatling |
| 스파이크 테스트 (Spike Testing) | 짧은 시간 내 급격한 요청 증가에 대한 반응 평가 | K6, Artillery |
| 지속 테스트 (Soak Testing) | 장시간 부하 유지 시 안정성 및 리소스 누수 확인 | K6, Locust |
| 단순 HTTP API 부하 | 단일 엔드포인트 집중 부하 | Hey, Vegeta |

<br>

---

### ✅ CI/CD 파이프라인 검증 테스트

| 테스트 항목 | 설명 | 도구 |
|-------------|------|------|
| 파이프라인 자동 실행 검증 | Git push 시 파이프라인 자동 실행 여부 검증 | GitLab CI, Jenkins, GitHub Actions |
| Smoke 테스트 | 배포 후 `/health` 등 API 응답 여부 확인 | curl, HTTPie, RestAssured |

<br>

---

### ✅ 기타 테스트
| 테스트 항목 | 설명 | 도구 |
|-------------|------|----------------|
| 지연/응답 시간 테스트 | API나 기능 호출 시 응답 속도를 측정하여 성능 병목 발견 | k6, Apache Bench (ab), JMeter |
| 장애 내성 테스트 | 외부 서비스/API/DB 장애 발생 시 시스템이 복원되거나 graceful하게 동작하는지 검증 | Resilience4j, Spring Retry |
| 경계값 테스트 | 입력값의 최소/최대, 경계 근처 값에 대해 시스템이 정확히 동작하는지 검증 | JUnit, Postman, Newman |

<br>

## 목차
1. [테스트 환경](#-테스트-환경)
2. [사용 도구](#-사용-도구)
3. [테스트 구조](#-테스트-구조)
4. [테스트 시나리오](#-테스트-시나리오)
5. [실행 방법](#-실행-방법)
6. [결과 확인](#-결과-확인)
7. [기타 참고 사항](#-기타-참고-사항)


