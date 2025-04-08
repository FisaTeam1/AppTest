# 🔍 Project Testing Guide

> 이 문서는 본 프로젝트에서 사용한 테스트 전략과 도구(k6, Prometheus, Grafana)에 대해 정리한 가이드입니다.  
단위 테스트부터 부하 테스트, 성능 모니터링까지 전체 테스트 흐름을 다룹니다.

<br>

## 📄 개요
테스트 과정을 명확히 문서화함으로써 코드의 안정성과 유지보수성을 높이고,  협업 시 일관된 테스트 수행 기준을 제공합니다.

## 🎯 목적
k6로 부하를 생성하고, Prometheus와 Grafana를 통해 실시간 모니터링함으로써  
시스템의 안정성, 확장성, 성능 병목 지점을 사전에 파악하고 대응하는 것이 목적입니다.

## 😎 Team
|<img src="https://avatars.githubusercontent.com/u/71498489?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/95984922?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/150774446?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/153366521?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/127267532?v=4" width="150" height="150"/>|
|:-:|:-:|:-:|:-:|:-:|
|[PM] HanJH<br/>[@letsgojh0810](https://github.com/letsgojh0810)|[PL] nahong_c<br/>[@HongChan1412](https://github.com/HongChan1412)|Kim YeJin<br/>[@yeejkim](https://github.com/yeejkim)|Park ji hye<br/>[@parkjhhh](https://github.com/parkjhhh)|Seok Hye Jin [@HyeJinSeok](https://github.com/HyeJinSeok)|


## 목차
1. [테스트 환경](#-테스트-환경)
2. [사용 도구](#-사용-도구)
3. [테스트 구조](#-테스트-구조)
4. [테스트 시나리오](#-테스트-시나리오)
5. [실행 방법](#-실행-방법)
6. [결과 확인](#-결과-확인)
7. [기타 참고 사항](#-기타-참고-사항)

---