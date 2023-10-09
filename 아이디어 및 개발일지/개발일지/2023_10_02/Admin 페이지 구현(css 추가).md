<br>
<p>src/main/resources/templates/admin/layouts/main.html
</p>

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org"
        xmlns:layout="http://www.ultraq.net.nz/thymeleaf/layout">
<head>
    <!-- CSRF라는 해킹 공격을 막기 위한 보안 방법 -->
    <!-- 지금 얘 때문에 오류나서 공부하고 나서 적용하도록 합시다.-->
    <meta name="_csrf" th:content="${_csrf.token}">
    <meta name="_csrf_header" th:content="${_csrf.headerName}">

    <!-- 페이지 이름 설정 -->
    <title th:if="${pageTitle != null}" th:text="${pageTitle}"></title>

    <!-- 아이콘 적용하기 위한 코드 -->
    <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/xeicon@2.3.3/xeicon.min.css">

    <!-- css 적용하기 위한 코드 -->
    <link rel="stylesheet" type="text/css" th:href="@{/admin/css/style.css}">
    <link rel="stylesheet" type="text/css" th:each="cssFile : ${addCss}" \
          th:href="@{/admin/css/{file}.css(file=${cssFile})}">
    <th:block layout:fragment="addCss"></th:block>


    <!-- 자바 스크립트 적용하기 위한 코드 -->
    <script th:src="@{/admin/js/common.js}"></script>
    <script th:each="jsFile : ${addScript}" th:src="@{/admin/js/{file}.js(file=${jsFile})}"></script>
    <th:block layout:fragment="addScript"></th:block>
</head>
<body th:class="${bodyClass}">
    <!--타임리프 csrf 토큰 (임의로 추가)-->
    <input type="hidden" th:name="_csrf" th:value="${_csrf.token}"/>
    <!-- 위의 헤더 부분 -->
    <header th:replace="~{admin/outlines/header::common}"></header>

    <main>
        <!-- 왼쪽에 있는 사이드 바 부분 -->
        <aside th:replace="~{admin/outlines/side::menus}"></aside>

        <!-- 이곳이 메인 부분 -->
        <section id="main_content" layout:fragment="content"></section>
    </main>
<iframe name="ifrmProcess" class="dn"></iframe>
</body>
</html>
```
<br>
<p>src/main/resources/static/admin/css/style.css
<p>

```css
@import url('https://fonts.googleapis.com/css2?family=Gowun+Dodum&display=swap');
* {
    font-family: 'Gowun Dodum', sans-serif;
    box-sizing: border-box;
    color: #000; outline: none;
}
body {
    margin: 0;
}
a {
    text-decoration: none;
}
dl, dt, dd, ul, ol, li {
    margin: 0; padding: 0;
}
ul, ol {
    list-style: none;
}
img {
    border: 0;
}

input[type='text'],
input[type='number'],
input[type='password'],
input[type='email'] {
    width: 100%;
    height: 45px;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 0 10px;
}

select { width: 100%; height: 45px; border: 1px solid #ccc; border-radius: 5px; }
textarea {
    width: 100%;
    min-height: 150px;
    border: 1px solid #ccc;
    border-radius: 5px;
    resize: none;
}
.dn {
    display: none !important;
}

.error {
    box-shadow: 2px 5px 5px #414141;
    padding: 10px;
    border-radius: 3px;
    margin: 5px 0;
    color : red;
}

.form dl{
    display: flex;
    margin-bottom: 10px;
    align-items: center;
}

.form dl dt{
    width: 150px;
}

.form dl dd{
    flex-grow: 1;
}

/** 공통 버튼 */
.btn1, .btn2{
    border: 1px solid #000;
    display: inline-block;
    padding: 7px 20px;
    border-radius: 5px;
    cursor: pointer;
    font-size: 13px;
    background: #fff;
}

.btn2{
    background: #fff;
    font-size: 14px;
    font-weight: bold;
}

.btn1:hover{
    background: #000;
    color: #fff;
}

.btn2:hover{
    background: orange;
}

.submit_btn{
    color: #fff;
    border-radius: 5px;
    min-width: 250px;
    background: #000;
    height: 45px;
    font-size: 16px;
    font-weight: bold;
    text-align: center;
    cursor: pointer;
    border: 0;
    margin: 10px auto;
    display: block;
    line-height: 45px;
}

.submit_btn > a {color: #fff;}


/** 관리자 헤더 영역  S */
header{
    padding: 0 20px;
    display: flex;
    justify-content: space-between;
    height: 70px;
    background: #ffffff;
    border-bottom: 2px solid #000;
}
header > section{
    display: flex;
    align-items: center;
}
header .btn1{
    margin-left: 5px;
}
/** 관리자 헤더 영역 E */


/** 관리자 메인 영역 > side 부분 S */
main{
    display: flex;
    min-height: 900px;
}
main > aside{
    width: 200px;
    background: #e0e0e0;
    border-right: 2px solid #000;
}
main > aside a{
    display: block;
    padding: 25px 20px;
    text-align: center;
    border-bottom: 1px solid #000;
    font-size: 20px;
    font-weight: bold;
    background: #fff;
}
main > aside a *{
    font-size: 20px;
}
main > aside a:hover,
main > aside a.on,
main > aside a:hover *,
main > aside a.on *{
    background: #000;
    color: #fff;
}

main > section{
    flex-grow: 1;
    padding: 50px 20px 20px 50px;
    background: #fff;
}

main nav{
    margin-bottom: 25px;
}
main nav.sub_menus{
    margin-bottom: 20px;
}
/** 관리자 메인 영역  > side 부분 E */
 left
/** 관리자 테이블 공통 부분 S */
.table-rows { padding: 0; border-spacing: 0; width: 100%; }
.table-rows th { padding: 10px; border-bottom: 1px solid #d5d5d5; border-top: 1px solid #d5d5d5; background: #f8f8f8; }
.table-rows td { padding: 10px; border-bottom: 1px solid #d5d5d5; }
.table-action { padding: 10px; border-bottom: 1px solid #d5d5d5; }

/** 관리자 테이블 공통 부분 E */

/** 페이징 공통 */
.pagination { text-align: center; margin: 20px 0; }
.pagination li { display: inline-block; }
.pagination a { font-size: 12px; border: 1px solid #dbdbdb; color: #363636; display: block; padding: 5px 10px; }
.pagination li.on a { background-color: #212121; border-color: #212121; color: #fff; }

/** 검색 양식 */
.search_form dl { display: table; width: 100%; border-bottom: 1px solid #d5d5d5; }
.search_form dl:first-of-type { border-top: 1px solid #d5d5d5; }
.headline { border-bottom: 2px solid #222; margin-bottom: 5px; }
.search_form dl dt { display: table-cell; width: 120px; padding: 10px; background: #f8f8f8; }
.search_form dl dd { display: table-cell; padding: 10px; }
.search_btn { margin: 10px auto 30px; display: block; min-width: 150px; padding: 10px; background: #212121; color: #fff; border: 0; font-size: 15px; border-radius: 3px; cursor: pointer; }

/** 양식 스타일 */
.form_style1 dl { align-items: stretch; border-bottom: 1px solid #d5d5d5; display: flex; width: 100%; margin: 0; align-items: center;  }
.form_style1 dl > dt { background: #f8f8f8; padding: 10px; width: 130px; }
.form_style1 dl > dd { padding: 10px; width: calc(100% - 130px); margin: 0; }

.layout_width { max-width: 1140px; min-width: 1000px; margin: 0 auto; }

/** 메인 공통 S */
main.layout_width { padding-top:20px; max-width: 1140px; min-width: 1000px; margin: 0 auto; }
/** 메인 공통 E */
```