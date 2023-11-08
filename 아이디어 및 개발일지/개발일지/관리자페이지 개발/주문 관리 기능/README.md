# 주문 관리 기능 설명


## 관리자 페이지_주문 관리
<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EA%B4%80%EB%A6%AC%EC%9E%90%20%ED%8E%98%EC%9D%B4%EC%A7%80/%EA%B4%80%EB%A6%AC%EC%9E%90%ED%8E%98%EC%9D%B4%EC%A7%80UI/%EC%A3%BC%EB%AC%B8%EA%B4%80%EB%A6%AC.png?raw=true">

<br>

해당 웹사이트의 주문 관리 기능은 다음과 같은 기능들을 포함하고 있습니다

## 1. 주문 리스트 조회

`OrderController`의 `orderList` 메소드를 통해, 관리자는 모든 주문 목록을 조회할 수 있습니다. `OrderInfoService`를 사용하여 데이터베이스에서 전체 주문 목록을 가져온 후, 이를 뷰에 전달하여 화면에 표시합니다.

```java
@GetMapping("/orderList")
public String orderList(Model model) {
    List<Order> orderList = orderInfoService.getAllOrders();
    model.addAttribute("orders", orderList);
    return "admin/order/index";
}
```

## 2. 주문 추가

### - 주문 추가 페이지 접근

`showAddOrderForm` 메소드를 통해 관리자는 주문을 추가할 수 있는 페이지로 이동할 수 있습니다.

```java
@GetMapping("/addOrderList")
public String showAddOrderForm() {
    return "admin/order/addorderlist";
}
```

### - 주문 추가 처리

`addOrderList` 메소드는 실제로 사용자 입력을 받아 새로운 주문을 추가합니다. 이 때 `OrderEditService`의 `addOrderList` 메서드를 호출하여 주문 정보를 저장합니다.

```java
@PostMapping("/addOrderList")
public String addOrderList(@ModelAttribute OrderInfo orderInfo, RedirectAttributes redirectAttributes) {
    // 주문 추가 로직 ...
}
```

## 3. 주문 수정

`editOrders` 메소드를 통해 관리자는 여러 주문의 상세 정보를 한 번에 수정할 수 있습니다. 이 메서드는 `@RequestBody`를 통해 JSON 형태로 받은 주문 정보를 `OrderEditService`의 `editOrderList` 메소드를 사용하여 데이터베이스에 반영합니다.

```java
@PostMapping("/editOrderList")
public ResponseEntity<?> editOrders(@RequestBody List<OrderInfo> orderInfo) {
    // 주문 수정 로직 ...
}
```

## 4. 주문 삭제

`deleteSelectedOrders` 메소드를 통해 관리자는 선택한 하나 또는 여러 주문을 삭제할 수 있습니다. 삭제할 주문의 ID 목록을 JSON 형태로 받아 `OrderEditService`의 `deleteOrders` 메소드를 통해 데이터베이스에서 해당 주문을 삭제합니다.

```java
@DeleteMapping("/deleteSelected")
public ResponseEntity<Map<String, String>> deleteSelectedOrders(@RequestBody List<Long> orderIds) {
    // 주문 삭제 로직 ...
}
```

## 5. 주문 관련 서비스 클래스들

### - `OrderInfoService`

주문 관련 조회 로직을 담당하며, 전체 주문 목록을 가져오거나 특정 사용자의 주문 목록을 조회하는 메서드를 제공합니다.

```java
@Service
public class OrderInfoService {
    // 주문 조회 관련 로직 ...
}
```

### - `OrderEditService`

주문 추가, 수정, 삭제 기능을 담당하며, 주문 정보를 실제로 데이터베이스에 반영하는 메서드를 제공합니다.

```java
@Service
public class OrderEditService {
    // 주문 추가, 수정, 삭제 로직 ...
}
```

## 6. 데이터베이스 접근을 위한 리포지토리

`OrderRepository` 인터페이스는 `JpaRepository`와 `QuerydslPredicateExecutor`를 상속받아 주문 엔티티에 대한 데이터베이스 접근을 추상화합니다. 사용자 번호로 주문을 조회하는 등의 쿼리 메서드를 제공합니다.

```java
public interface OrderRepository extends JpaRepository<Order, Long>, QuerydslPredicateExecutor<Order> {
    // 사용자 번호로 주문 조회 ...
}
```

이러한 기능들을 통해 웹사이트에서는 관리자가 주문 데이터를 효율적으로 관리할 수 있도록 돕습니다.