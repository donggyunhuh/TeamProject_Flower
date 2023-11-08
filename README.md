# 개인 맞춤형 꽃 추천 및 주문 서비스 : DALL-E를 이용한 엽서 디자인

## 개요

이 웹 사이트는 사용자가 선택한 키워드를 기반으로 맞춤형 꽃을 추천하고 주문할 수 있는 플랫폼입니다. DALL-E를 활용하여 텍스트 프롬프트를 기반으로 한 엽서 이미지를 생성하고 주문을 단순화하는 서비스도 제공합니다.

<br>

## 🌼 꽃 추천 기능 서비스 예시

<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EC%B6%94%EC%B2%9C%EC%84%9C%EB%B9%84%EC%8A%A4.gif?raw=ture">

<br>

## ✔️ 주제를 선택한 이유와 기획서 확인하기

- ###  주제 선택 이유
  - 개인 맞춤형 상품(꽃다발, 케이크 등)을 예약하거나 구매할 경우 현재는 SNS를 통해 사장님에게 직접 연락해야 하는 불편함이 있습니다. 
  - 이를 개선하기 위해 선택한 주제로, 꽃 예약 사이트를 통해 사장님들의 수고를 덜어주고, 꽃 구매에 사용자 경험을 향상시키고 다양한 정보를 제공할 수 있도록 하기 위해서 입니다.

- ### [프로젝트 기획서](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B8%B0%ED%9A%8D%EC%84%9C/%EB%8F%84%ED%99%94%EB%8B%A4%20%EA%BD%83%20%EC%B6%94%EC%B2%9C%20%EB%B0%8F%20%EC%A3%BC%EB%AC%B8%20%EC%9B%B9%EC%82%AC%EC%9D%B4%ED%8A%B8%20%EA%B8%B0%ED%9A%8D%EC%84%9C.pdf)
- ### [아이디어 회의 일지](https://github.com/donggyunhuh/TeamProject_Flower/tree/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%ED%9A%8C%EC%9D%98%EC%9D%BC%EC%A7%80)

<br>

## ✔️ 기능 및 서비스

### 꽃 추천 기능
- [꽃 추천 알고리즘](https://github.com/donggyunhuh/TeamProject_Flower/tree/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%BD%83%20%EC%B6%94%EC%B2%9C%20%EA%B8%B0%EB%8A%A5%20%EA%B0%9C%EB%B0%9C)
- #### [가중치 모델링](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EA%B4%80%EB%A6%AC%EC%9E%90%20%ED%8E%98%EC%9D%B4%EC%A7%80/%EA%BD%83%EA%B4%80%EB%A6%AC/%EA%B0%80%EC%A4%91%EC%B9%98%EB%AA%A8%EB%8D%B8%EB%A7%81.png)

사용자가 선택한 키워드를 기반으로 가중치를 설정하고, 이를 활용하여 꽃을 추천합니다. 사용자가 선택한 키워드를 우선 순위대로 정렬하고, 이에 따라 꽃 종류와 정보를 추천합니다.

### DALL-E 엽서 디자인 기능
- [OpenAI의 DALL·E 를 사용한 엽서 제작 서비스 개발일지](https://github.com/donggyunhuh/TeamProject_Flower/tree/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EC%BB%A4%EC%8A%A4%ED%85%80%20%EC%97%BD%EC%84%9C%20%EC%A0%9C%EC%9E%91%20%EA%B8%B0%EB%8A%A5%20%EA%B0%9C%EB%B0%9C)

사용자가 제공한 텍스트 프롬프트를 기반으로 DALL-E API를 사용하여 엽서 이미지를 생성합니다. 이를 통해 사용자는 원하는 내용의 엽서를 만들고 주문할 수 있습니다.

### 주문서 작성 및 주문 내역 확인 기능
- [ORDER 화면](https://github.com/donggyunhuh/TeamProject_Flower/tree/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/UI%20%EA%B0%9C%EB%B0%9C/ORDER%20%ED%8E%98%EC%9D%B4%EC%A7%80)
  - 주문서를 입력받아 데이터 베이스에 저장하고 주문 완료 화면으로 넘어갑니다.
  - 결제API를 사용하여 주문서 작성을 완료한 후 결제 화면으로 넘어가는 기능을 구현중입니다. 
- [MyPage 화면](https://github.com/donggyunhuh/TeamProject_Flower/tree/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/UI%20%EA%B0%9C%EB%B0%9C/MYPAGE%20%ED%8E%98%EC%9D%B4%EC%A7%80)
  - 사용자의 경우
    - 자신이 주문한 주문 내역을 확인할 수 있습니다. 
    - 주문 상태를 확인하고 주문 취소를 요청할 수 있습니다. 
    - 개인 정보를 관리하고 닉네임을 변경할 수 있습니다.
  - 사장의 경우 
    - 매장에 들어온 모든 주문 내역을 확인할 수 있습니다. 
    - 주문을 확인하고 완료 처리할 수 있습니다

### 관리자 페이지
- [관리자페이지 개발일지](https://github.com/donggyunhuh/TeamProject_Flower/tree/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B4%80%EB%A6%AC%EC%9E%90%ED%8E%98%EC%9D%B4%EC%A7%80%20%EA%B0%9C%EB%B0%9C)
  - 관리자 페이지는 웹 사이트의 운영을 위한 핵심 기능을 제공하는 곳으로,
  - 개발은 꽃 관리, 주문 처리, 사용자 정보 관리 기능들을 100% 완료 상태로 구현하였으며, 
  - 스프링 MVC 패턴과 Thymeleaf 템플릿 엔진을 사용하여 설계 및 구현하였습니다. 
  - 보안 강화를 위해 스프링 시큐리티를 통합하였고, 프로젝트 구조와 실행 방법을 확인하시려면 링크로 이동해주세요.


- 꽃 관리 기능: 꽃의 추가, 수정, 삭제를 관리합니다. 키워드와 가중치를 관리합니다.
  - [꽃 관리 기능 개발일지](https://github.com/donggyunhuh/TeamProject_Flower/tree/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B4%80%EB%A6%AC%EC%9E%90%ED%8E%98%EC%9D%B4%EC%A7%80%20%EA%B0%9C%EB%B0%9C/%EA%BD%83%20%EA%B4%80%EB%A6%AC%20%EA%B8%B0%EB%8A%A5)
- 주문 처리 기능: 주문 목록을 조회하고 주문을 추가, 수정, 삭제합니다. 매장 리스트를 관리합니다.
  - [주문 관리 기능 개발일지](https://github.com/donggyunhuh/TeamProject_Flower/tree/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B4%80%EB%A6%AC%EC%9E%90%ED%8E%98%EC%9D%B4%EC%A7%80%20%EA%B0%9C%EB%B0%9C/%EC%A3%BC%EB%AC%B8%20%EA%B4%80%EB%A6%AC%20%EA%B8%B0%EB%8A%A5)
- 사용자 정보 관리 기능: 사용자 목록을 조회하고 관리합니다. 사용자의 닉네임을 변경할 수 있습니다.
  - [회원 관리 기능 개발일지](https://github.com/donggyunhuh/TeamProject_Flower/tree/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B4%80%EB%A6%AC%EC%9E%90%ED%8E%98%EC%9D%B4%EC%A7%80%20%EA%B0%9C%EB%B0%9C/%ED%9A%8C%EC%9B%90%20%EA%B4%80%EB%A6%AC%20%EA%B8%B0%EB%8A%A5)

### UI 디자인
- [도화다 UI](https://www.figma.com/file/tWJizqxXmYMFLOvOuNIm2K/dohwada?type=whiteboard&node-id=0-1&t=bSqZV1XA4xeeeR4x-0)

Figma를 사용하여 사용자 인터페이스를 구상하고 디자인하였습니다.

### 데이터베이스
- [데이터베이스 모델링](https://github.com/donggyunhuh/TeamProject_Flower/tree/main/%EC%95%84%EC%9D%B4%EB%94%94%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EA%B0%9C%EB%B0%9C%EC%9D%BC%EC%A7%80/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%20%EA%B0%9C%EB%B0%9C)


꽃 추천 웹사이트의 데이터베이스 설계를 담고 있으며, 사용자(User), 주문(Order), 매장(Store) 등의 엔터티들과 그 관계를 ER 다이어그램으로 설명하였습니다. 개발 내용은 엔터티 설계의 상세한 설명과 함께 이루어졌으며, 이후로 서비스 및 리포지토리 계층의 구현이 진행되었습니다.

## 기능 구현 예시
- gif 파일이 표시되는데 시간이 걸릴 수 있습니다. 양해해주시면 감사하겠습니다.
### 🌼 꽃 추천 기능 서비스

![꽃 추천 기능](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EC%B6%94%EC%B2%9C%EC%84%9C%EB%B9%84%EC%8A%A4.gif?raw=ture)

### 🌼 주문서 작성 및 주문 내역 확인 서비스

![주문서 작성 및 주문 내역 확인](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EC%A3%BC%EB%AC%B8%EC%84%9C%EC%9E%91%EC%84%B1.gif?raw=ture)

### 🌼 엽서 디자인 서비스

![엽서_디자인_서비스](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EC%97%BD%EC%84%9C%20%EC%A0%9C%EC%9E%91%20%EA%B8%B0%EB%8A%A5%20%EC%98%88%EC%8B%9C.gif?raw=true)

### 🌼 관리자 페이지 작동 예시

![관리자 페이지 작동](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EA%B4%80%EB%A6%AC%EC%9E%90%ED%8E%98%EC%9D%B4%EC%A7%80%EC%9E%91%EB%8F%99%EC%98%88%EC%8B%9C.gif?raw=true)

### 🌼 회원가입/로그인 예시

![회원가입/로그인_예시](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%ED%9A%8C%EC%9B%90%EA%B0%80%EC%9E%85%EB%A1%9C%EA%B7%B8%EC%9D%B8.gif?raw=true)

### 🌼닉네임 변경 예시

![닉네임_변경_예시](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EB%8B%89%EB%84%A4%EC%9E%84%EB%B3%80%EA%B2%BD%EC%98%88%EC%8B%9C.gif?raw=true)

## ✔️ 사용 기술 스택

```
- Java 21
- Spring Boot 3.1.4
- Spring MVC
- Thymeleaf 3.2.1
- Spring Security
- MySQL (데이터베이스)
```
- 프로젝트를 개발 하기 위해서 스프링 프레임워크를 이용하였습니다.


- **스프링 MVC 패턴**으로 컨트롤러와 뷰를 분리하여 웹 애플리케이션의 구조를 체계화하여 관리하고, 요청과 응답을 처리하는데 사용합니다.


- **Thymeleaf 템플릿 엔진**을 활용하여 HTML 뷰를 생성할 수 있었습니다. 이를 통해 동적으로 페이지를 생성하고 데이터를 렌더링할 수 있습니다.


- **데이터베이스 트랜잭션 관리**: 스프링의 `@Transactional` 어노테이션을 적용하여 데이터베이스 트랜잭션을 관리하고, 데이터베이스 연산의 일관성을 유지하였습니다.


- 이외에도 스프링부트에서 지원하는 어노테이션으로 getter와 setter 등을 서술하지 않는 편리성을 이유로 이러한 언어를 사용하였습니다.




## 프로젝트 GitHub Repository

[프로젝트 소스코드 GitHub Repository 바로가기](https://github.com/donggyunhuh/TeamProjectFlower_Sourcecode)

### [프로젝트 별 이슈](https://github.com/donggyunhuh/TeamProjectFlower_Sourcecode/issues)
- 깃허브의 프로젝트 기능의 칸반보드를 활용하여 각 기능 개발하였습니다. 첨부한 링크로 이동하면 이슈마다 자세한 개발 과정을 확인하실 수 있습니다.

    <img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%B9%B8%EB%B0%98%EB%B3%B4%EB%93%9C.png?raw=true">

## 프로젝트 팀 구성

- 팀장: 허동균
- 팀원: 구대윤, 김진우, 이도경

## 개발 일정

- 프로젝트 시작일: 2023년 9월 18일
- 프로젝트 완료 예정일: 2023년 11월 27일



## 마치며

이 프로젝트는 사용자에게 개인 맞춤형 꽃 추천 및 주문 서비스를 제공함으로써 꽃을 구매하고 싶은 사람들에게 더 나은 경험을 제공하고자 합니다. 관심을 가져주셔서 감사드리며 언제든지 문의하시면 자세한 정보를 제공해 드리겠습니다.

감사합니다.
