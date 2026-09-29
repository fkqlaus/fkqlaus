<div align="center">

<sub>JAVA · SPRING · BACKEND ENGINEERING</sub>

# 최광혁

### 데이터의 흐름을 이해하고, 선택의 이유를 설명합니다.

Java와 Spring으로 API와 데이터 처리 기능을 개발하는 백엔드 개발자입니다.

<a href="mailto:fkqlaus@naver.com"><img alt="Email" src="https://img.shields.io/badge/Email-2563EB?style=flat-square" /></a>
<a href="https://fkqlaus.tistory.com/"><img alt="Tech Blog" src="https://img.shields.io/badge/Tech%20Blog-263449?style=flat-square" /></a>
<a href="https://github.com/nhnacademy-be8-plzbuybook/bookstore-shoppingmall"><img alt="Featured Project" src="https://img.shields.io/badge/Featured%20Project-263449?style=flat-square&logo=github&logoColor=white" /></a>

<br />

[About](#about) &nbsp; / &nbsp; [Project](#project) &nbsp; / &nbsp; [Experience](#experience) &nbsp; / &nbsp; [Stack](#stack)

</div>

<br />

| BACKEND | DATA | SEARCH |
| :--- | :--- | :--- |
| **API · 외부 시스템 연계** | **도메인 · 데이터 모델링** | **Elasticsearch 기반 검색** |
| 공공 업무 시스템 개발 | 도서·판매 정보 분리 설계 | 다중 필드 검색과 가중치 적용 |

<br />

<a id="about"></a>
## 01 &nbsp; About

**공공 업무 시스템의 백엔드를 개발하고 있습니다.**
API, 데이터 처리, 외부 시스템 연계를 구현하며 데이터가 저장되고 조회되는 흐름을 살핍니다.

NHN Academy 팀 프로젝트에서는 **도서 도메인과 검색 기능**을 담당했습니다.
데이터 모델링, 조회 구조, 데이터 정합성을 중심으로 학습하고 기술 선택의 이유를 기록합니다.

<br />

<a id="project"></a>
## 02 &nbsp; Selected Project

### plzbuybook
**온라인 도서 쇼핑몰** &nbsp; · &nbsp; NHN Academy &nbsp; · &nbsp; 7인 팀

도서 검색부터 주문·결제까지 제공하는 온라인 서점입니다.
**도서·판매도서 관리, 계층형 카테고리, 검색 기능**을 담당했습니다.

<img alt="Java 21" src="https://img.shields.io/badge/Java%2021-263449?style=flat-square" /> <img alt="Spring Boot 3.3.6" src="https://img.shields.io/badge/Spring%20Boot%203.3.6-263449?style=flat-square&logo=springboot&logoColor=white" /> <img alt="JPA" src="https://img.shields.io/badge/JPA-263449?style=flat-square" /> <img alt="MySQL" src="https://img.shields.io/badge/MySQL-263449?style=flat-square&logo=mysql&logoColor=white" /> <img alt="Elasticsearch" src="https://img.shields.io/badge/Elasticsearch-2563EB?style=flat-square&logo=elasticsearch&logoColor=white" />

| 해결할 과제 | 설계와 구현 |
| :--- | :--- |
| **여러 속성으로 도서 찾기** | 제목·저자·카테고리·태그 검색. 제목 **3.0**, 저자 **1.5** 가중치 적용 |
| **기본 정보와 판매 정보 구분** | 팀원과 함께 `Book` · `SellingBook` 분리 모델 설계, 관련 API·관리자 기능 구현 |
| **여러 단계의 도서 분류 관리** | 부모·깊이를 갖는 카테고리 모델과 단계별 등록·조회·도서 연결 구현 |

[프로젝트 소개 ↗](https://github.com/nhnacademy-be8-plzbuybook) &nbsp; · &nbsp; [Backend ↗](https://github.com/nhnacademy-be8-plzbuybook/bookstore-shoppingmall) &nbsp; · &nbsp; [Frontend ↗](https://github.com/nhnacademy-be8-plzbuybook/bookstore-front)

<details>
<summary><b>설계 과정과 구현 코드 살펴보기</b></summary>

#### 1. 여러 도서 속성을 함께 사용하는 검색

- **요구사항:** 제목뿐 아니라 저자·카테고리·태그를 이용해 도서를 찾을 수 있어야 했습니다.
- **구현:** Elasticsearch의 여러 필드에 검색어를 적용하고, 제목에는 `3.0`, 저자에는 `1.5`의 가중치를 설정했습니다.
- **동작:** 하나의 키워드로 여러 속성을 검색하면서 필드별 가중치를 검색 점수에 반영하도록 구성했습니다.

[검색 쿼리](https://github.com/nhnacademy-be8-plzbuybook/bookstore-shoppingmall/blob/develop/src/main/java/com/nhnacademy/book/book/elastic/repository/BookInfoRepository.java) · [검색 결과 처리](https://github.com/nhnacademy-be8-plzbuybook/bookstore-shoppingmall/blob/develop/src/main/java/com/nhnacademy/book/book/service/Impl/BookSearchService.java)

#### 2. 도서 기본 정보와 판매 정보의 분리

- **요구사항:** ISBN·출판 정보와 판매 가격·재고·판매 상태를 구분해 관리해야 했습니다.
- **설계·구현:** 팀원과 함께 `Book`과 `SellingBook`을 분리한 모델을 설계하고, 관련 API와 관리자 기능을 구현했습니다.
- **동작:** 도서 기본 정보에 판매 정보를 연결하는 구조로 구성하고, 판매 도서로 등록되지 않은 도서를 관리자가 조회하는 기능을 구현했습니다.

[Book 모델](https://github.com/nhnacademy-be8-plzbuybook/bookstore-shoppingmall/blob/develop/src/main/java/com/nhnacademy/book/book/entity/Book.java) · [SellingBook 모델](https://github.com/nhnacademy-be8-plzbuybook/bookstore-shoppingmall/blob/develop/src/main/java/com/nhnacademy/book/book/entity/SellingBook.java)

#### 3. 계층형 카테고리와 도서 분류

- **요구사항:** 외부 도서 API의 분류 정보를 여러 단계의 카테고리로 저장하고 관리해야 했습니다.
- **구현:** 부모 카테고리와 깊이를 갖는 계층 모델을 사용하고, 단계별 카테고리 등록·조회와 도서 연결 기능을 구현했습니다.
- **동작:** 상위·하위 분류 관계를 관리하고, 카테고리별 도서 조회에 활용했습니다.

[카테고리 모델](https://github.com/nhnacademy-be8-plzbuybook/bookstore-shoppingmall/blob/develop/src/main/java/com/nhnacademy/book/book/entity/Category.java) · [팀 역할 분담](https://github.com/nhnacademy-be8-plzbuybook#최광혁)

</details>

<details>
<summary><b>프로젝트에서 정리한 기술 기록</b></summary>

- [Elasticsearch와 Nori 분석기](https://github.com/nhnacademy-be8-plzbuybook/bookstore-shoppingmall/issues/502)
- [Kibana](https://github.com/nhnacademy-be8-plzbuybook/bookstore-shoppingmall/issues/508)
- [Logstash](https://github.com/nhnacademy-be8-plzbuybook/bookstore-shoppingmall/issues/509)

</details>

<br />

<a id="experience"></a>
## 03 &nbsp; Experience

**(주)스페이스빌더스 · 개발팀** | 2025.05 ~ 재직 중

| 기간 | 프로젝트 | 소개 |
| --- | --- | --- |
| 2025.05 ~ 2025.06 | 회사 공식 홈페이지 | 기업·사업 소개, 게시판과 문의 기능을 제공하는 홈페이지 |
| 2025.06 ~ 2025.07 | 스마트 쉘터 콘텐츠 관리 시스템 | 버스 스마트쉼터의 홍보 이미지·영상을 수집·편성·재생하는 시스템 |
| 2025.07 ~ 2025.10 | 스마트통합관제센터 | 산업단지의 시설·안전·교통 정보를 지도와 관제 화면에서 관리하는 플랫폼 |
| 2025.11 ~ 2026.03 | 군청 재난안전 통합 플랫폼 | 위험성평가, 근로자 건강상담과 산업재해 업무를 지원하는 시스템 |
| 2026.07 ~ 2026.09 | 공간정보 플랫폼 고도화 | 지도 기반 공간정보 조회와 사용자 레이어·시설물 데이터 관리를 지원하는 플랫폼 |


<br />

<a id="stack"></a>
## 04 &nbsp; Tech Stack

**Backend**

<img alt="Java" src="https://img.shields.io/badge/Java-2563EB?style=flat-square" /> <img alt="Spring Boot" src="https://img.shields.io/badge/Spring%20Boot-263449?style=flat-square&logo=springboot&logoColor=white" /> <img alt="Spring MVC" src="https://img.shields.io/badge/Spring%20MVC-263449?style=flat-square" /> <img alt="Spring Data JPA" src="https://img.shields.io/badge/Spring%20Data%20JPA-263449?style=flat-square" /> <img alt="MyBatis" src="https://img.shields.io/badge/MyBatis-263449?style=flat-square" />

**Data & Search**

<img alt="MySQL" src="https://img.shields.io/badge/MySQL-263449?style=flat-square&logo=mysql&logoColor=white" /> <img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-263449?style=flat-square&logo=postgresql&logoColor=white" /> <img alt="Elasticsearch" src="https://img.shields.io/badge/Elasticsearch-263449?style=flat-square&logo=elasticsearch&logoColor=white" /> <img alt="Logstash" src="https://img.shields.io/badge/Logstash-263449?style=flat-square&logo=logstash&logoColor=white" /> <img alt="Kibana" src="https://img.shields.io/badge/Kibana-263449?style=flat-square&logo=kibana&logoColor=white" />

**Tools**

<img alt="Git" src="https://img.shields.io/badge/Git-263449?style=flat-square&logo=git&logoColor=white" /> <img alt="GitHub" src="https://img.shields.io/badge/GitHub-263449?style=flat-square&logo=github&logoColor=white" /> <img alt="Linux" src="https://img.shields.io/badge/Linux-263449?style=flat-square&logo=linux&logoColor=white" />

<br />

## 05 &nbsp; Education & Certification

| 기간 | 교육 · 자격 |
| :--- | :--- |
| 2025.03 | **SQLD** 취득 |
| 2025.02 | **NHN Academy** Java 백엔드 개발자 과정 수료 |
| 2025.02 | **조선대학교** 컴퓨터공학과 졸업 |

<br />

---

<div align="center">

**구현에서 끝나지 않고, 이유를 기록합니다.**

[기술 블로그](https://fkqlaus.tistory.com/) &nbsp; · &nbsp; [이메일](mailto:fkqlaus@naver.com) &nbsp; · &nbsp; [GitHub](https://github.com/fkqlaus)

</div>
