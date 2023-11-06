<p>src/main/java/org/flower/commons/UserUtils.java</p>

```java
package org.flower.commons;

import jakarta.servlet.http.HttpSession;
import lombok.RequiredArgsConstructor;
import org.flower.commons.constants.UserRole;
import org.flower.entities.User;
import org.flower.models.user.UserInfo;
import org.modelmapper.ModelMapper;
import org.springframework.stereotype.Component;

@Component
@RequiredArgsConstructor
public class UserUtils {

    private final HttpSession session;

    /**
     * 로그인 여부 체크
     *
     * @return
     * */
    public boolean isLogin(){

        return getUser() != null;
    }

    /**
     *  관리자 여부 체크
     *
     * @return
     * */
    public boolean isAdmin(){
        User user = getEntity();

        if (user != null && user.getRole() == UserRole.ADMIN){
            return true;
        }

        return false;
    }

    /**
     *  회원번호와 로그인한 회원번호가 일치한지 체크
     *
     * @param userEmail
     * @return
     * */
    public boolean isMine(String userEmail){

        return isLogin() && getUser().getUserEmail() == userEmail;
    }

    /**
    *  회원 정보 조회
     *
     * @return
    * */
    public UserInfo getUser() {
        UserInfo userInfo = (UserInfo) session.getAttribute("userInfo");

        return userInfo;
    }

    /**
    *  엔티티로 가져오기
     *
     * @return
    * */
    private User getEntity() {
        UserInfo userInfo = getUser();

        return userInfo != null ? new ModelMapper().map(userInfo, User.class) : null;
    }
}

```
<p>src/main/java/org/flower/models/user/UserEditService.java</p>

```java
package org.flower.models.user;

import lombok.RequiredArgsConstructor;
import org.flower.commons.UserUtils;
import org.flower.controllers.user.user.UserJoin;
import org.flower.entities.User;
import org.flower.repositories.UserRepository;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.stereotype.Service;
import org.springframework.validation.Errors;

/*
* 사용자의 정보를 수정하는 서비스
* */
@Service
@RequiredArgsConstructor    // Lombok 라이브러리의 어노테이션으로, final 또는 @NonNull 필드값만 파라미터로 받는 생성자를 자동으로 생성
public class UserEditService {

    private final UserRepository repository;

    private final PasswordEncoder passwordEncoder;      // 비밀번호 암호화에 대한 변수 의존 주입

    private final UserUtils userUtils;

    // 사용자 정보 수정 부분 (구현해보기)
    public void userEdit(UserJoin join, Errors errors){

    }
}

```
<p>src/main/java/org/flower/models/user/UserSaveService.java</p>

```java
package org.flower.models.user;

import lombok.RequiredArgsConstructor;
import org.flower.controllers.user.user.UserJoin;
import org.flower.entities.User;
import org.flower.repositories.UserRepository;
import org.springframework.security.core.Authentication;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.stereotype.Service;

/*
* 사용자의 정보를 생성하고 저장하는 서비스
* */
@Service
@RequiredArgsConstructor        // Lombok 라이브러리의 어노테이션으로, final 또는 @NotNull 필드값만 파라미터로 받는 생성자를 자동으로 생성
public class UserSaveService {

    private final UserRepository repository;

    private final PasswordEncoder passwordEncoder;      // 비밀번호 암호화 담당 변수 의존 주입

    /* 사용자 정보 저장하거나 업데이트 하는 메서드 */
    public void save(UserJoin userJoin){
        User user;

        // 현재 스레드에 바인딩된 SecurityContext에서 Authentication 객체를 가져옴
        Authentication auth = SecurityContextHolder.getContext().getAuthentication();

        // 현재 인증된 사용자가 UserInfo 타입인지 확인
        if(auth.getPrincipal() instanceof UserInfo){        // 회원 정보 수정
            // UserInfo 타입이 맞다면 사용자 정보수정 실행
            UserInfo userInfo = (UserInfo) auth.getPrincipal();

            // 사용자를 찾아 수정하거나,
            user = repository.findById(userInfo.getUserNo()).orElse(UserJoin.of(userJoin));
            user.setUserNm(userJoin.getUserNm());
            user.setUserEmail(userJoin.getUserEmail());
            user.setUserPw(userJoin.getUserPw());
            user.setUserNickNm(userJoin.getUserNickNm());
            user.setCellPhone(userJoin.getCellPhone());
        }else {                                             // 없다면 새로운 사용자를 생성함
            user = UserJoin.of(userJoin);
        }

        if (userJoin.getUserPw() != null){              // 비밀번호 수정이 있는 경우 변경 처리
            String hash = passwordEncoder.encode(userJoin.getUserPw());
            user.setUserPw(hash);
        }

        // 사용자 정보를 데이터베이스에 저장
        repository.saveAndFlush(user);
    }
}

```