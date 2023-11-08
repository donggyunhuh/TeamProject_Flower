# 마이페이지 기능 구현 상세 문서


## 마이페이지
<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EB%A7%88%EC%9D%B4%ED%8E%98%EC%9D%B4%EC%A7%80.png?raw=true">


## 개요
이 문서는 꽃 주문 웹 어플리케이션의 마이페이지 관련 기능을 구현하는 컨트롤러, 서비스 및 HTML 레이아웃에 대한 상세 내용을 정리한 마크다운 파일입니다.

## 마이페이지 기능

### 컨트롤러 (`MypageHomeController`, `ProfileController`)
- `MypageHomeController`: 마이페이지 홈과 주문 내역을 보여주는 뷰를 반환합니다.
- `ProfileController`: 프로필 페이지를 보여주고, 닉네임 중복 체크와 업데이트 기능을 담당합니다.

### 서비스 (`OrderListService`)
- `OrderListService`: 사용자의 주문 내역을 조회하는 서비스 로직을 포함합니다.

### HTML 레이아웃 (`mypage.html`, `orderlist.html`, `profilePage.html`)
- `mypage.html`: 마이페이지의 메인 홈을 나타내는 레이아웃으로, 사용자의 닉네임과 주문 내역 확인 버튼을 제공합니다.
- `orderlist.html`: 사용자의 주문 내역을 테이블 형태로 보여주는 레이아웃을 구성합니다.
- `profilePage.html`: 사용자 프로필과 관련된 정보를 수정할 수 있는 폼을 제공합니다.

## 코드 상세

### `MypageHomeController.java`
```java
@Controller
@RequestMapping("/user/mypage")
public class MypageHomeController {
    // 서비스 및 레포지토리 의존성 주입
    // ...

    // 마이페이지 홈 뷰 반환
    @GetMapping
    public String showMyNickname(Model model) {
        // ...
    }

    // 주문 내역 뷰 반환
    @GetMapping("/main/home/orderlist")
    public String showMyOrder(Model model) {
        // ...
    }
}
```

### `ProfileController.java`
```java
@Controller
@RequestMapping("/user/mypage/profile")
public class ProfileController {
    // 서비스 및 레포지토리 의존성 주입
    // ...

    // 프로필 페이지 뷰 반환
    @GetMapping("/profilePage")
    public String showMyPage(Model model) {
        // ...
    }

    // 닉네임 중복 체크
    @GetMapping("/check/checkNickNm")
    public Map<String, Boolean> checkNickname(@RequestParam String newNickname) {
        // ...
    }

    // 닉네임 업데이트
    @PostMapping("/profilePage/update/updateNickname")
    public ResponseEntity<?> updateNickname(@RequestBody UserEditInfo userEditInfo) {
        // ...
    }
}
```

### `orderlist.html`
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<!-- ... -->
<body>
    <!-- 헤더 및 기타 레이아웃 -->
    <!-- 주문 내역 테이블 -->
    <div class="content">
        <table class="order-table">
            <!-- ... -->
        </table>
    </div>
</body>
</html>
```

## 개발 고려사항
- 스프링 시큐리티를 활용하여 인증된 사용자만 마이페이지에 접근할 수 있도록 합니다.
- 사용자 경험을 고려하여 프론트엔드 디자인과 인터랙션을 설계합니다.

## 결론
이 문서는 마이페이지의 주요 기능 구현에 대한 상세 설명과 코드 예시를 제공하여 개발자들이 참고하고 이해할 수 있도록 도와줍니다.