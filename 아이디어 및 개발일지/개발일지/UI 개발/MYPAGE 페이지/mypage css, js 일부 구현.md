<p>src/main/resources/static/front/mypage/css/style.css</p>

```css


.shippingStatusContainer{
    padding: 21px 16px;
    background-color: white;
    max-width: 600px;  /* 원하는 최대 너비 설정 */
    margin: 0 auto;
}

/* 주문/배송조회 타이틀 */
.shippingStatusContainer .title{
    font-size: 16px;
    font-weight: bold;
    margin-bottom: 15px;
}

/* 장바구니 결제완료 배송중 구매확정 [로우] */
.shippingStatusContainer .status{
    display: flex;
    justify-content: space-between;
    margin-bottom: 21px;
}
/* 장바구니 결제완료 배송중 구매확정 [아이템]  */
.shippingStatusContainer .item{
    display: flex;
}

.shippingStatusContainer .number{
    font-size: 31px;
    font-weight: 500;
    text-align: center;
}
.shippingStatusContainer .text{
    font-size: 12px;
    font-weight: normal;
    color: #c2c2c2;
    text-align: center;
}
.shippingStatusContainer .icon{
    display: flex;
    align-items: center;
    padding: 20px;
    width: 16px;
    height: 16px;
}

.block-link {
    display: block;
    color: inherit; /* 링크 색상을 상속 받음 */
    text-decoration: none; /* 밑줄 제거 */
}

.block-link:hover,
.block-link:focus {
    /* 호버 및 포커스 시 스타일 */
    background-color: #f0f0f0; /* 예시: 배경색 변경 */
}

.profile-container {
    display: flex;  /* Flexbox를 사용하여 내부 아이템들을 가로로 배치합니다 */
    align-items: center;  /* 아이템들을 세로 중앙에 배치합니다 */
    margin: 20px auto;
    padding: 20px;
    background-color: #fff;

    max-width: 500px;  /* 원하는 최대 너비 설정 */
    position: relative;
    border: none;
}

.profile-image {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    object-fit: cover;
    margin-right: 100px;  /* 이미지와 텍스트 사이의 간격 */
}

.profile-info {
    /* 여기에는 추가적인 스타일을 설정하지 않아도 됩니다, 필요하다면 추가하세요 */
}

.name, .rank {
    margin: 0;
    font-weight: bold;
}

.name {
    font-size: 18px;
    margin-right: 20px;
}

.rank {
    font-size: 14px;
    color: #888;
    margin-right: 20px;
}

ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    width: 25%;
    background-color: transparent;
    position: fixed;
    height: 100%;
    overflow: auto;
}

li a {
    display: block;
    color: #000;
    padding: 8px 16px;
    text-decoration: none;
}

li a.active {
    background-color: #f0f0f0;
    color: black;
}

li a:hover:not(.active) {
    background-color: #f0f0f0;
    color: black;
}

.content
{
    font-size: 16px;
    font-weight: bold;
    margin-left: 360px;
}

.content1
{
    font-size: 16px;
    font-weight: bold;
    margin-top: 260px;
    margin-left: 350px;
}


ul.sidebar {
    float: left;  /* 좌측으로 float 속성을 적용합니다. */
    width: 200px; /* 너비를 설정합니다. */
    margin-left: 150px;
    padding: 0;
    list-style-type: none;
}

ul.sidebar li {
    margin-bottom: 10px;
}

ul.sidebar li a {
    text-decoration: none;
    color: #000;
}

ul.sidebar li a.active {
    background-color: #f0f0f0;
    color: black;
}

.all {
    margin : auto;
    padding: initial;
}
```
<p>src/main/resources/static/front/mypage/js/common.js</p>

```javascript
function openTab(evt, tabName) {
    var i, tabcontent, tablinks;
    tabcontent = document.getElementsByClassName("tabcontent");
    for (i = 0; i < tabcontent.length; i++) {
        tabcontent[i].style.display = "none";
    }
    tablinks = document.getElementsByClassName("tablink");
    for (i = 0; i < tablinks.length; i++) {
        tablinks[i].className = tablinks[i].className.replace(" active", "");
    }
    document.getElementById(tabName).style.display = "block";
    evt.currentTarget.className += " active";
}

```