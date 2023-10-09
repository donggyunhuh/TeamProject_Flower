<p>src/main/java/org/flower/commons/validators/ServiceValidator.java</p>

```java
package org.flower.commons.validators;

import org.springframework.validation.Errors;
/**
* 서비스 유효성 검사 공통 Validator
 *
 * @param <T>
 * */
public interface ServiceValidator<T> {

    void check(T t);

    /**
     * 커맨드 객체가 포함된 경우
     *
     * @param t
     * @param errors
     * */
    default void check(T t, Errors errors){
        if(errors != null && errors.hasErrors()){
            return;
        }

        this.check(t);
    }
}

```
<p>src/main/java/org/flower/commons/validators/RequiredCheckValidator.java</p>

```java
package org.flower.commons.validators;

/* null 값과 문자열의 유효성 검사를 위한 메서드 제공하는 인터페이스 */
public interface RequiredCheckValidator {
    /**
     * null 값 체크
     *
     * @param o
     * @param e
    * */
    default void nullcheck(Object o, CommonException e){
        if(o == null){
            throw e;
        }
    }

    /**
    * 문자열 필수 항목 체크
     *
     * @param str
     * @param e
    * */
    default  void requiredCheck(String str, CommonException e){
        if(str == null || str.isBlank()){
            throw e;
        }
    }
}

```