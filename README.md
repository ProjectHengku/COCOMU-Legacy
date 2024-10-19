# 프로젝트 꼬꼬무

> 꼬리에 꼬리를 무는 무비(영화)

좋아하는 장르를 기반으로 영화를 추천받고, 보고싶은 영화를 가성비 있게 볼 수 있는 방법을 추천받는 영화 감상 취미를 이어가는데 도움을 주는 서비스

## 프로젝트 타겟

영화 감상을 취미로 가지고 있고, 새로운 영화를 찾기를 원하거나 영화를 보는 비용을 줄이고싶은 사람

## 기획의도

1. 영화를 보려고 찾아보는데, 요즘 영화 관련 서비스가 너무 많음
2. 많은 영화들이 각각 사이트들에 서로 다르게 서비스되고 있어서 정보를 찾기 쉽지 않음
3. 구독만으로 볼 수도 있고 대여나 소장해야 하는 경우도 있어서 돈 계산이 어려움
4. 이런 사항들에 대한 개선을 할 수 없을까?

> 영화의 정보를 통합해서 조회하고 내가 좋아하는 스타일로 즐길 수 있는 최선의 경우를 추천 받게 하자

## 기능 소개

### 회원 기능

기본 회원 정보와 선호하는 장르, 기사용중인 OTT 서비스 정보를 수집

-   일부 정보는 수정 가능

### 영화 세부 정보 소개

영화의 제목, 줄거리, 출연 배우 등의 정보를 제공함

-   TMDB API와 이를 통하여 사전 수집한 DB를 혼용

### 찜목록 기능

보고싶은 영화를 찜목록에 추가할 수 있음

-   UX 향상을 위해 영화 목록이나 세부 정보가 주어지는 모든 페이지에 접근 경로 준비
-   UI 가독성을 위해 마우스 호버시에만 버튼이 활성화되도록 구현

### 영화 추천 알고리즘

#### 초기 기획안

2D Vectorization을 이용한 정보 합산의 결과로 선호 장르를 파악하려고 함

하지만 다음의 이유로 적용하기 힘들다고 판단

-   여러 장르를 고르게 좋아하는 경우, 결과물 신뢰도가 낮아짐 (벡터 크기가 작음)
-   데이터 모수가 양이 적을 경우 결과물 신뢰도가 낮아짐
-   시간 관계상 데이터 수집을 위한 페이지 구현의 난이도가 높다고 판단함

#### 최종안

가입시 받은 선호 장르 정보를 이용

-   DB 내의 영화 정보들을 가져옴
-   선호 장르를 포함하는 영화들을 선별
-   선별된 영화 목록을 무작위로 섞음
    -   다양한 영화를 겹치지 않게 추천하고자 함
-   이상의 과정으로 얻은 영화 목록 상위 4개를 보여줌
-   사용자 요청시 4개씩 추가로 보여줌

### 최적 요금 알고리즘

가입시 받은 이용 중인 서비스 정보를 이용

찜목록 기능에서 수집한 영화 목록 정보를 사용

-   찜목록 내의 영화 정보들을 가져옴
-   해당 정보들의 서비스 제공자 정보를 가져옴
-   서비스 제공 가능한 서비스의 개수와 서비스의 제공 콘텐츠 수, 서비스 비용으로 가격 대비 효용(가성비)을 계산하여 최종 합산시 가장 저렴한 경우를 취함
-   위 정보를 바탕으로 단일 서비스 이용시 가장 가격 대비 효용이 좋은 서비스를 추천함
-   기사용중인 서비스는 기회비용이 추가적으로 지출하지 않는다고 판단, 0원으로 예외처리함

### AI 연관 영화 추천 알고리즘

Chat GPT API를 이용

영화 세부 정보 페이지에서 제공함

-   현재 조회 중인 영화와 비슷한 영화의 제목들을 List 형식으로 받아서 순회하며 python 내에서 처리
-   처리된 데이터를 DB 나 TMDB API 로 조회하여 영화 데이터 확보
-   데이터를 가공해서 사용자에게 결과물 제공

## 최적화

-   파이썬 자체 라이브러리를 이용해 상세영화 조회 캐싱
-   부분적인 로드 속도 향상 결과 얻음

## 사용 기술

### 구현

Python, Django, HTML, CSS, Bootstrap, Vue.js(with pinia, vue-router), axios, Django DB via SQLite, dotenv

### 일정 관리

Notion, Jira

### 버전 관리, 페어 프로그래밍

gitLab, VSCode Live Share

## 구현

### 일정

5월 14일 (화)

-   사전 미팅
-   초기 기획서 작성

5월 16일 (목)

-   기획, 초기 디자인

5월 17일 (금)

-   ERD 작성
-   초기 작업 착수

5월 18일 (토)

-   개인 일정

5월 19일 (일)

-   구현
-   기반 서버 코드 작성
-   메인 페이지 등 구현

5월 20일 (월)

-   구현
-   FE 기반 기능 코드 작성
-   핵심 서버 코드 완성

5월 21일 (화)

-   구현
-   FE 기반 기능 코드 완성
-   서버 추가 요구 기능 구현

5월 22일 (수)

-   구현, 디버깅
-   웹 페이지 디자인
-   FE 추가 요구 기능 구현

5월 23일 (목)

-   디버깅
-   QA 작업 및 주요 오류 수정
-   웹 페이지 디자인 완성
-   발표 준비

5월 24일 (금)

-   제출 마감
-   발표