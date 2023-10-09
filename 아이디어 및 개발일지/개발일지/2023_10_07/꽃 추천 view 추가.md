<p>src/main/resources/templates/front/recommend/loading.html</p>

```html
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <!--css 파일 적용하기-->
    <link rel="stylesheet" type="text/css" th:href="@{/front/recommend/css/style.css}">
    <link th:each="cssFile : ${addCss}" rel="stylesheet" type="text/css"
          th:href="@{/front/css/{file}.css(file=${cssFile})}">
    <th:block layout:fragment="addCss"></th:block>

    <!--js 파일 적용하기 -->
    <script th:src="@{/front/recommend/js/common.js}"></script>
    <script th:each="jsFile : ${addScript}" th:src="@{/front/js/{file}.js(file=${jsFile})}"></script>
    <th:block layout:fragment="addScript"></th:block>

    <!-- 어트리뷰트 pageTitle 속성에서 받아옴-->
    <title th:if="${pageTitle != null}" th:text="${pageTitle}"></title>
</head>
<body>
<h1>당신에게 어울릴 꽃을 찾고있어요...</h1>

<p>선택한 키워드:</p>
<ul>
    <!-- Thymeleaf를 사용하여 전달된 키워드를 렌더링 -->
    <li th:each="keyword : ${selectedKeywords}" th:text="${keyword}"></li>
</ul>

<!-- 나중에 여기에 추천 로직 진행 -->
</body>
</html>

```
<p>src/main/resources/templates/front/recommend/main.html</p>

```html
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org"
      xmlns:layout="http://www.ultraq.net.nz/thymeleaf/layout">
<head>
    <meta charset="UTF-8">
    <!--css 파일 적용하기-->
    <link rel="stylesheet" type="text/css" th:href="@{/front/recommend/css/style.css}">
    <link rel="stylesheet" type="text/css" th:href="@{/front/css/style.css}">
    <link th:each="cssFile : ${addCss}" rel="stylesheet" type="text/css"
          th:href="@{/front/css/{file}.css(file=${cssFile})}">
    <th:block layout:fragment="addCss"></th:block>

    <!--js 파일 적용하기 -->
    <script th:src="@{/front/recommend/js/common.js}"></script>
    <script th:each="jsFile : ${addScript}" th:src="@{/front/js/{file}.js(file=${jsFile})}"></script>
    <th:block layout:fragment="addScript"></th:block>

    <!-- 어트리뷰트 pageTitle 속성에서 받아옴-->
    <title th:if="${pageTitle != null}" th:text="${pageTitle}"></title>
</head>
<body>
<header th:replace="~{front/outlines/header::common}"></header>
<h1>마음에 드는 순서대로 키워드를 바구니에 드래그 해주세요!</h1>

<ul>
    <!-- Thymeleaf로 키워드 렌더링 -->
    <li th:each="keyword : ${keywords}"
        th:text="${keyword}"
        class="draggable"
        draggable="true"
        ondragstart="drag(event)">
    </li>
</ul>

<div id="basket" ondrop="drop(event)" ondragover="allowDrop(event)">
    <p>바구니에 담긴 키워드가 없습니다.</p>
    <ul></ul>
</div>

<form id="keywordsForm" method="post" action="/recommend/loading">
    <!-- 키워드를 담을 숨겨진 input 필드 -->
    <input type="hidden" name="selectedKeywords" id="selectedKeywords">
    <!-- CSRF 토큰을 포함 -->
    <input type="hidden" name="_csrf" th:value="${_csrf.token}">
</form>

<button id="recommendBtn">꽃 추천받기</button>

</body>
</html>

```