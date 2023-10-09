<p>src/main/resources/templates/admin/user/_submenu.html</p>

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<nav th:fragment="menus">
    <a th:href="@{/admin/user}" class="btn2">
        <i class="xi-list"></i>
        회원 목록
    </a>
</nav>
</html>
```
<p>src/main/resources/templates/admin/user/index.html</p>

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org"
      xmlns:layout="http://www.ultraq.net.nz/thymeleaf/layout"
      layout:decorate="~{admin/layouts/main}">
<section layout:fragment="content">
    <nav th:replace="~{admin/user/_submenu::menus}"></nav>
    <!--내용 집어넣으면 됨-->
</section>
</html>
```