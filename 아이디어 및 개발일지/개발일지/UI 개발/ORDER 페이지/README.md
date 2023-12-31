# 주문 프로세스 개발일지

## 주문서 작성 및 주문 내역 확인 서비스

![주문서 작성 및 주문 내역 확인](https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EC%A3%BC%EB%AC%B8%EC%84%9C%EC%9E%91%EC%84%B1.gif?raw=ture)

## 개요
본 문서는 꽃 주문 서비스의 주문 프로세스 구현에 대한 상세 내용을 정리한 마크다운 파일입니다.

## 주문 프로세스

### 컨트롤러 (`OrderprocessController`)
- **주문서 작성 페이지 (`@GetMapping()`)**
    - 사용자가 로그인하지 않은 경우 로그인 페이지로 리다이렉트합니다.
    - 로그인한 사용자에게는 주문서 작성 페이지를 제공합니다.
    - <img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%A3%BC%EB%AC%B8/ordercontroller_getmapping.png?raw=true">

- **주문서 저장 및 주문 완료 페이지 (`@PostMapping("/submitOrder")`)**
    - 사용자가 작성한 주문서를 저장하고 주문 완료 페이지로 리다이렉트합니다.
    - <img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%A3%BC%EB%AC%B8/ordercontroller_postmapping.png?raw=true">

### 모델 (`OrderFormInfo`)
- 주문서 작성을 위한 정보를 담는 클래스입니다.
- 사용자 번호, 이름, 전화번호 등 주문에 필요한 정보를 포함합니다.

### 서비스 (`OrderFormService`)
- <img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EC%A3%BC%EB%AC%B8/orderformservice.png?raw=true">
- 주문 폼 정보를 바탕으로 새로운 주문 객체를 생성하고 저장하는 역할을 합니다.
- `@Transactional` 어노테이션을 통해 데이터베이스의 일관성을 유지합니다.

### HTML 페이지 (`orderForm.html`, `orderCompleted.html`)
- `orderForm.html`: 사용자가 주문 정보를 입력할 수 있는 폼을 제공합니다.
- `orderCompleted.html`: 주문 완료 후 주문 정보를 확인할 수 있는 페이지를 제공합니다.


## 개발 고려사항
- 주문 시스템은 Spring Security를 활용하여 인증된 사용자만 주문서 작성이 가능하도록 설정하였습니다.
- 주문 완료 후에는 주문 내역을 확인할 수 있는 링크를 제공하여 사용자의 편의성을 증진시켰습니다.

## 결론
이 개발일지는 주문 프로세스 구현에 대한 전반적인 흐름과 세부 구현 사항을 기술하고 있으며, 실제 사용자의 주문 경험을 향상시키기 위한 기능적 요소들을 중점적으로 다루고 있습니다.