# 메인페이지 구현 상세 문서


## 메인 페이지
<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80/%EB%A9%94%EC%9D%B8%ED%8E%98%EC%9D%B4%EC%A7%80.jpg?raw=true">


## 개요
본 문서는 꽃 주문 웹 어플리케이션의 메인 페이지를 구성하는 HTML 및 CSS 구현에 대한 상세 내용을 정리한 마크다운 파일입니다.

## HTML 구조

### 공통 레이아웃 (`main.html`)
메인 페이지는 다음과 같이 구성되어 있습니다
- **헤더**: 사용자의 로그인 상태에 따라 로그인, 로그아웃, 회원가입, 마이페이지 등의 링크를 제공합니다.
- **메인 콘텐츠**: 추천(Recommendation), 주문(Order), 엽서(Postcard) 섹션으로 구성되며, 각각의 섹션은 배경 이미지와 중앙에 텍스트 오버레이로 구성됩니다.
- **푸터**: 개인정보 처리방침, 이용약관 링크와 함께 학교 정보를 표시했습니다.

### 헤더 (`header.html`)
- **로고**: 좌측 상단에 위치하며, 클릭 시 홈페이지로 이동합니다.
- **네비게이션**: 로그인/로그아웃, 회원가입/마이페이지 링크가 우측에 위치합니다.

### 푸터 (`footer.html`)
- **정책 링크**: 개인정보 처리방침, 이용약관에 대한 링크 제공.
- **회사 정보**: 학교명, 대표자, 사업자 번호, 연락처, 주소 등을 포함합니다.

## CSS 스타일링

### 공통 스타일 (`style.css`)
- 기본 마진, 패딩 제거 및 필수 HTML 태그에 대한 스타일을 정의합니다.
- 헤더와 푸터의 배경색, 높이, 패딩을 지정합니다.

### 메인 콘텐츠 스타일 (`style.css`)
- 메인 섹션에 대한 배경 이미지, 텍스트 오버레이 스타일을 지정합니다.
- 이미지 위에 오버레이 효과를 주어 텍스트가 눈에 띄게 합니다.

## 코드 예시

### `main.html`
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<!-- ... -->
<main layout:fragment="content">
    <!-- ... -->
</main>
</html>
```

### `header.html`
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<header th:fragment="common">
    <!-- ... -->
</header>
</html>
```

### `footer.html`
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<footer th:fragment="common">
    <!-- ... -->
</footer>
</html>
```

### `style.css`
```css
/* ... */
header, footer {
    background-color: #fff;
    padding: 10px 20px;
    height: 10vh;
}
/* ... */
```

## 개발 고려사항
- 모든 페이지에 공통적으로 적용될 수 있는 CSS 및 JavaScript 파일을 링크합니다.
- 사용자 경험을 고려하여 폰트와 색상을 선정했습니다.

## 결론
이 문서는 메인 페이지의 구성 및 스타일링에 관한 상세 내용을 제공하며, 향후 유지보수 및 확장성을 고려한 설계를 기술하고 있습니다.