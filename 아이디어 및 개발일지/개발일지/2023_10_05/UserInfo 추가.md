<p>src/main/java/org/flower/models/user/UserInfo.java</p>

```java
package org.flower.models.user;

import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;
import org.springframework.security.core.GrantedAuthority;
import org.springframework.security.core.userdetails.UserDetails;

import java.util.Collection;

/*
 * 스프링 시큐리티 UserDetails 재정의
 * */
@Data          // getter, setter, equals(), hashCode(), toString() 메서드를 지원
@Builder        // Builder 패턴을 사용하여 객체를 생성할 수 있음
                // 이 패턴은 객체의 생성 과정과 표현 방법을 분리하여 동일한 생성 절차서 서로 다른 표현 결과를 만들 수 있게 함
@NoArgsConstructor      // 인자 없는 기본 생성자를 생성
@AllArgsConstructor     // 모든 필드를 인자로 받는 생성자를 생성
public class UserInfo implements UserDetails {

    private Long userNo;            // 회원번호
    private String userEmail;       // 아이디(이메일)
    private String userPw;          // 비밀번호
    private String userPwCk;        // 비밀번호 체크
    private String userNm;          // 회원명
    private String userNickNm;      // 닉네임
    private String cellPhone;       // 전화번호
    private String address;          // 주소

    private Collection<GrantedAuthority> authorities;

    /*
    * 사용자에게 부연된 권한들을 저장하는 컬렉션
    * GrantedAuthority는 Spring Security에서 권한을 표현함
    * */
    @Override
    public Collection<? extends GrantedAuthority> getAuthorities() {
        return authorities;
    }

    @Override
    public String getPassword() {   // 사용자의 비밀번호를 반환
        return userPw;
    }

    @Override
    public String getUsername() {   // 사용자의 아이디(이메일)을 반환
        return userEmail;
    }

    @Override
    public boolean isAccountNonExpired() {      // 계정이 만료되지 않았는지를 반환
        return true;
    }

    @Override
    public boolean isAccountNonLocked() {       // 계정이 잠기지 않았는지를 반환
        return true;
    }

    @Override
    public boolean isCredentialsNonExpired() {  // 사용자의 인증 정보(비밀번호)가 만료되지 않았는지를 반환
        return true;
    }

    @Override
    public boolean isEnabled() {                // 사용자가 활성화 상태인지를 반환
        return true;
    }
}

```
<p>src/main/java/org/flower/models/user/UserInfoService.java</p>

```java
package org.flower.models.user;

import org.flower.entities.User;
import org.flower.repositories.UserRepository;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.security.core.GrantedAuthority;
import org.springframework.security.core.authority.SimpleGrantedAuthority;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.core.userdetails.UsernameNotFoundException;
import org.springframework.stereotype.Service;

import java.util.Arrays;
import java.util.List;

@Service        // 스프링이 이 클래스를 서비스로 인식하고 관리하도록 하는 어노테이션
public class UserInfoService implements UserDetailsService {
    /*
    * implements UserDetailService
    * UserDetailService 인터페이스를 구현, 이 인터페이스의 loadUserByUsername 메서드를 오버라이드하여 사용자의 정보를 불러옴
    * */

    @Autowired      // 스프링의 의존섭 주입 기능을 사용하여 UserRepository 타입의 빈을 자동으로 주입
    private UserRepository repository;  // 사용자 정보를 데이터 소스에서 조회하는 데 사용

    /*
    * loadUserByUsername()
    * UserDetailService 인터페이스의 메서드로, 주어진 사용자명으로 사용자 정보를 조회하고 UserDetails 객체로 반환
    * */
    @Override
    public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {
        User user = repository.findByUserEmail(username);       // username 을 매개변수로 받아, 해당 사용자의 정보를 데이터 소스에서 조회

        if(user == null){       // 조회된 상용자 정보가 null인 경우, UsernameNotFoundException 발생
            throw new UsernameNotFoundException(username);
        }

        /*
        * 권한 정보 생성
        * 권한 정보를 GrantedAuthrity 타입의 리스트로 생성.
        * SimpleGrantedAuthrity를 사용하여 사용자의 역할 정보 (user.getRole())를 GrantedAuthority로 변환
        * */
        List<GrantedAuthority> authorities= Arrays.asList(new SimpleGrantedAuthority(user.getRole().toString()));

        /*
        * UserInfo 클래스의 빌더를 사용하여 UserDetails 객체를 생성하고 반환.
        * user 객체에서 추출한 정보를 UserInfo 객체의 필드에 할당한다.
        * */
        return UserInfo.builder()
                .userNo(user.getUserNo())
                .userEmail(user.getUserEmail())
                .userNm(user.getUserNm())
                .userPw(user.getUserPw())
                .userNickNm(user.getUserNickNm())
                .cellPhone(user.getCellPhone())
                .authorities(authorities)
                .build();
    }

    /*
    * UserInfoService는 사용자 인증 시 사용자명을 기반으로 사용자 정보를 데이터 소스에서 조회하고,
    * 이를 Spring Security에서 사용할 수 있는 UserDetails 타입으로 반환하여 인증과 권환 확인 과정에서 활용됨
    * */
}

```