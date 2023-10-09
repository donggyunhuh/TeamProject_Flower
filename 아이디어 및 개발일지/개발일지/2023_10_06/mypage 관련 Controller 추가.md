<p>src/main/java/org/flower/controllers/user/mypage/Review/ReviewController.java</p>

```java
package org.flower.controllers.user.mypage.Review;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
@RequestMapping("/user/mypage/main/main_review")
public class ReviewController {
    @GetMapping
    public String main(){
        return "/front/mypage/main/main_review";
    }
}

```
<p>src/main/java/org/flower/controllers/user/mypage/inquire/InquireController.java</p>

```java
package org.flower.controllers.user.mypage.inquire;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
@RequestMapping("/user/mypage/main/main_inquire")
public class InquireController {
    @GetMapping
    public String main(){
        return "/front/mypage/main/main_inquire";
    }
}

```

<p>src/main/java/org/flower/controllers/user/mypage/orderlist/OrderListController.java</p>

```java
package org.flower.controllers.user.mypage.orderlist;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
@RequestMapping("/user/mypage/main/home")
public class OrderListController {

    @GetMapping
    public String main(){
        return "/front/mypage/main/home";
    }
}

```
