<p>src/main/resources/templates/error/401.html</p>

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org"
      xmlns:layout="http://www.ultraq.net.nz/thymeleaf/layout"
      layout:decorate="~{front/layouts/main}">
<section layout:fragment="content">
    <th:block th:replace="~{error/_message::message}"></th:block>
</section>
</html>
```
<p>src/main/resources/templates/error/403.html</p>

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org"
      xmlns:layout="http://www.ultraq.net.nz/thymeleaf/layout"
      layout:decorate="~{front/layouts/main}">
<section layout:fragment="content">
    <th:block th:replace="~{error/_message::message}"></th:block>
</section>
</html>
```
<p>src/main/resources/templates/error/404.html</p>

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org"
      xmlns:layout="http://www.ultraq.net.nz/thymeleaf/layout"
      layout:decorate="~{front/layouts/main}">
<section layout:fragment="content">
    <th:block th:replace="~{error/_message::message}"></th:block>
</section>
</html>
```
<p>src/main/resources/templates/error/500.html</p>

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org"
      xmlns:layout="http://www.ultraq.net.nz/thymeleaf/layout"
      layout:decorate="~{front/layouts/main}">
<section layout:fragment="content">
  <th:block th:replace="~{error/_message::message}"></th:block>
</section>
</html>
```
<p>src/main/resources/templates/error/_message.html</p>

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<th:block th:fragment="message">
    <div th:if="${status != null}" th:text="${status}"></div>
    <div class="message">
        <th:block th:if="${status == 401}" th:text="#{errors.status401}"></th:block>
        <th:block th:if="${status == 403}" th:text="#{errors.status403}"></th:block>
        <th:block th:if="${status == 404}" th:text="#{errors.status404}"></th:block>
        <th:block th:if="${status == 500}" th:text="#{errors.status500}"></th:block>
        <th:block th:if="${status == null && message != null}" th:text="${message}"></th:block>
    </div>
</th:block>

</html>
```
<p>src/main/resources/templates/error/common.html</p>

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org"
    xmlns:layout="http://www.ultraq.net.nz/thymeleaf/layout"
      layout:decorate="~{front/layouts/main}">
<section layout:fragment="content">
    <th:block th:replace="~{error/_message::message}"></th:block>
</section>
</html>
```