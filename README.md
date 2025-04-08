# 🔍 Project Testing Guide

> 이 문서는 본 프로젝트에서 사용한 테스트 전략과 도구(k6, Prometheus, Grafana)에 대해 정리한 가이드입니다.  
단위 테스트부터 부하 테스트, 성능 모니터링까지 전체 테스트 흐름을 다룹니다.

<br>

## 😎 Team
|<img src="https://avatars.githubusercontent.com/u/71498489?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/95984922?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/150774446?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/153366521?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/127267532?v=4" width="150" height="150"/>|
|:-:|:-:|:-:|:-:|:-:|
|[PM] HanJH<br/>[@letsgojh0810](https://github.com/letsgojh0810)|[PL] nahong_c<br/>[@HongChan1412](https://github.com/HongChan1412)|Kim YeJin<br/>[@yeejkim](https://github.com/yeejkim)|Park ji hye<br/>[@parkjhhh](https://github.com/parkjhhh)|Seok Hye Jin [@HyeJinSeok](https://github.com/HyeJinSeok)|

## 📄 개요
이 문서는 본 프로젝트에서 수행하는 테스트의 목적과 흐름을 정리한 가이드입니다.  
단위 테스트, 통합 테스트, 성능 테스트, 부하 테스트를 포함하며  
각 테스트는 코드의 안정성과 시스템의 신뢰성을 확보하기 위해 계획되었습니다.

## 🎯 목적
기능 단위의 정확성부터, 시스템 전반의 성능과 확장성까지 검증함으로써  
문제 발생 가능성을 사전에 줄이고, 품질 높은 소프트웨어를 제공하는 것을 목표로 합니다.

## 🛠️ 사용 도구 (Testing Tools)

| 테스트 종류       | 목적                                                       | 사용 도구                                      |
|------------------|------------------------------------------------------------|------------------------------------------------|
| 단위 테스트       | 개별 기능 단위의 동작을 빠르게 검증하여 코드 정확성 확보               | JUnit                                           |
| 통합 테스트       | 구성 요소 간의 실제 연동을 테스트하여 시스템 전체의 동작 확인          | SpringBootTest                                 |
| 성능 테스트       | 시스템의 응답 시간 및 처리량 등을 측정하여 성능 병목 파악               | k6                                              |
| 부하 테스트       | 고부하 상황에서의 안정성, 확장성, 리소스 소비 등을 실시간으로 모니터링 | k6 + Prometheus + Grafana                      |




## 목차
1. [테스트 환경](#-테스트-환경)
2. [사용 도구](#-사용-도구)
3. [테스트 구조](#-테스트-구조)
4. [테스트 시나리오](#-테스트-시나리오)
5. [실행 방법](#-실행-방법)
6. [결과 확인](#-결과-확인)
7. [기타 참고 사항](#-기타-참고-사항)

---