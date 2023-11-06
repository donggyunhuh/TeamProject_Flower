# 관리자 페이지 회원 관리 기능

## UserController (org.flower.controllers.admin.user)

`UserController` 클래스는 관리자 페이지에서 회원 관리 기능을 처리하는 컨트롤러입니다.

<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EA%B4%80%EB%A6%AC%EC%9E%90%20%ED%8E%98%EC%9D%B4%EC%A7%80/%ED%9A%8C%EC%9B%90%EA%B4%80%EB%A6%AC/usercontroller.png?raw=true">

- `@GetMapping`으로 정의된 `index` 메서드를 통해, 관리자는 `/admin/user` 경로로 접속하여 모든 사용자 목록을 볼 수 있습니다.
- `getAllUsers` 메서드는 `UserInfoService`를 통해 모든 사용자 정보를 조회합니다.
- 반환된 사용자 목록과 현재 날짜/시간 정보를 모델에 추가하여 뷰로 전달합니다.

## UserRepository (org.flower.repositories)

`UserRepository` 인터페이스는 데이터베이스 작업을 추상화합니다.

- `JpaRepository`를 상속받아 기본 CRUD 연산을 제공합니다.
- `QuerydslPredicateExecutor`를 통해 QueryDSL을 사용할 수 있습니다.
- `findByUserEmail`, `findByUserNo`, `findByUserNickNm` 메서드를 통해 특정 사용자 정보를 조회할 수 있습니다.
- `isUserExists`와 `isNickNmExists` 메서드는 이메일과 닉네임의 중복 여부를 체크합니다.

## UserInfo (org.flower.models.user)

<img src="https://github.com/donggyunhuh/TeamProject_Flower/blob/main/%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%EC%82%AC%EC%A7%84/%EA%B4%80%EB%A6%AC%EC%9E%90%20%ED%8E%98%EC%9D%B4%EC%A7%80/%ED%9A%8C%EC%9B%90%EA%B4%80%EB%A6%AC/userinfo.png?raw=true">

`UserInfo` 클래스는 `UserDetails` 인터페이스를 구현합니다.

- Spring Security에서 사용자의 정보를 담는 역할을 하며, 사용자 인증에 필요한 정보와 권한을 제공합니다.
- 클래스는 Lombok 어노테이션을 사용해 보일러플레이트 코드를 최소화합니다.

## UserInfoService (org.flower.models.user)

`UserInfoService` 클래스는 `UserDetailsService` 인터페이스를 구현합니다.

- `loadUserByUsername` 메서드를 오버라이드하여 사용자 이름으로 사용자 정보를 로드합니다.
- 사용자 정보가 데이터베이스에 존재하지 않으면 `UsernameNotFoundException`을 던집니다.
- 사용자의 권한 정보를 `GrantedAuthority` 리스트로 생성합니다.

## LoginFailureHandler (org.flower.models.user)

`LoginFailureHandler` 클래스는 `AuthenticationFailureHandler` 인터페이스를 구현하여 로그인 실패 시의 로직을 처리합니다.

- 로그인 실패 시, 사용자에게 적절한 에러 메시지를 플래시 속성을 통해 전달합니다.
- 사용자가 로그인 페이지로 리다이렉트됩니다.

## LoginSuccessHandler (org.flower.models.user)

`LoginSuccessHandler` 클래스는 `AuthenticationSuccessHandler` 인터페이스를 구현하여 로그인 성공 후의 로직을 처리합니다.

- 세션에서 불필요한 속성을 제거하고, 사용자 정보를 세션에 추가합니다.
- 사용자를 웹 애플리케이션의 메인 페이지로 리다이렉트합니다.
