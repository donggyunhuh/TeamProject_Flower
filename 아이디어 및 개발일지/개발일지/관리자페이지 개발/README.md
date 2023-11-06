# 관리자 페이지 개요

관리자 페이지는 웹 사이트의 운영을 위한 핵심 기능을 제공하는 곳으로, 꽃 관리, 주문 처리, 사용자 정보 관리 등의 기능을 포함하고 있습니다. 이 페이지는 스프링 시큐리티를 통해 보안을 강화하였으며, 다음은 관리자 페이지의 개발 진행 상황과 설계 및 구현 내용을 소개합니다.

## 개발 진행 상황

- 꽃 관리 기능: 100% 완료 (꽃 추가, 수정, 삭제 구현 완료)
  - 그 외 키워드,  가중치 관리 기능
- 주문 처리 기능: 100% 완료 (주문 목록 조회 구현 완료)
  - 주문, 매장 리스트 추가 수정, 삭제 기능
- 사용자 정보 관리 기능: 100% 완료 (사용자 목록 조회 구현 완료)

## 설계 및 구현

관리자 페이지의 설계와 구현에는 다음과 같은 주요 요소가 사용되었습니다:

- **스프링 MVC 패턴**: 관리자 컨트롤러와 뷰를 분리하여 웹 애플리케이션의 구조를 관리하고, 요청과 응답을 처리하는데 사용되었습니다.

- **Thymeleaf 템플릿 엔진**: HTML 뷰를 생성하기 위해 Thymeleaf 템플릿 엔진을 활용하였습니다. 이를 통해 동적으로 페이지를 생성하고 데이터를 렌더링할 수 있습니다.

- **데이터베이스 트랜잭션 관리**: 스프링의 `@Transactional` 어노테이션을 적용하여 데이터베이스 트랜잭션을 관리하고, 데이터베이스 연산의 일관성을 유지하였습니다.

## 프로젝트 구조

프로젝트의 구조는 다음과 같이 정리되었습니다:

```
- src/
  - main/
    - java/
      - org.flower/
        - controllers.admin/ 
          - MainController.java
          - user/
            - UserController.java
          - recommend/
            - FlowerController.java
            - KeywordController.java
            - WeightController.java
          - order/
            - OrderController.java
            - StoreController.java
        - service/
          - flower/
            - FlowerInfoService.java
            - FlowerEditService.java
          - keyword/
            - KeywordInfoService.java
            - KeywordEditService.java
          - order/
            - OrderInfoService.java
            - OrderEditService.java
          - store/
            - StoreInfoService.java
            - StoreEditService.java
          - weight/
            - WeightInfoService.java
            - WeightEditService.java
           - user/
            - mypage/
              - OrderListService.java
            - UserEditService.java
            - UserEditInfoService
            - UserInfoService.java
            - UserSaveService.java
            - UserJoinService.java
            - LoginFailureHandler.java
            - LoginSuccessHandler.java
        - model/
          - UserInfo.java
          - UserEditInfo.java
          - FlowerInfo.java
          - KeywordInfo.java
          - WeightInfo.java
          - OrderInfo.java
          - OrderEditInfo.java
          - StoreInfo.java
          - StoreEditInfo.java       
        - repository/
          - FlowerRepository.java
          - KeywordRepository.java
          - WeightRepository.java
          - OrderRepository.java
          - StoreRepository.java
          - UserRepository.java
        - security/
          - SecurityConfig.java
        - AdminApplication.java
    - resources/
      - templates/
        - admin/
          - layouts/
            - main.html
          - main/
            - index.html
          - order/
            - _submenu.html
            - addorderlist.html
            - addstorelist.html
            - index.html
            - store.html
          - outlines/
            - header.html
            - side.html
          - user/
            - index.html
            - _submenu.html
          - recommend/
            - index.html
            - keyword.html
            - weight.html
            - flowerWeightList.html
            - _submenu.html
      - application.properties
```

## 사용 기술 스택

- Java 21
- Spring Boot 3.1.4
- Spring MVC
- Thymeleaf 3.2.1
- Spring Security
- MySQL (데이터베이스)

## 실행 방법

1. MySQL 데이터베이스를 설정하고 `application.properties` 파일에서 데이터베이스 연결 정보를 수정합니다.
2. 프로젝트를 빌드하고 실행합니다.

```
./mvnw spring-boot:run
```

3. 브라우저에서 `http://localhost:3001`으로 접속하여 관리자 페이지를 이용할 수 있습니다.

## 더 많은 정보

더 자세한 사용법과 개발 과정의 문서화는 프로젝트 내 다른 문서들에서 확인할 수 있습니다.

**프로젝트 관련 문의 및 지원은 아래 연락처로 문의 바랍니다:**

- 이메일: dohwada55@gmail.com

감사합니다. 