# NOWNESS
- 국비지원 풀스택 과정 팀 프로젝트
- 기획 의도: 지역 현장 정보 공유를 통한 사회적 비용(인파 집중으로 인한 문제 등) 감소
- 기간 및 인원: 약 1개월 / 5명(풀스택)

- 기술 스택
  - Backend: Java 17, Spring Boot 3.1.1, Thymeleaf 3.1.1, Spring Security 6.1.1, MyBatis 3.0.2, MySQL 8.0.32
  - Frontend: Bootstrap, JavaScript, jQuery
  - 외부 API: Naver Image CAPTCHA API

- 구현 사항
  1) 로그인/회원가입/회원정보 등 회원관련 화면 설계 및 구현
      - ID/Password 및 소셜 로그인(Google, Kakao, Naver) 기능
        - 구현 일정을 맞추기 위해 구현을 하기는 했지만, Spring Security에 대해 이해하지 못하고 구현을 하여 지속적으로 공부하고 블로그에 글을 남기고 있습니다.([블로그 링크](https://limvik.github.io/categories/spring/)) 
      - 인증 이메일 발송/재발송, 이메일을 통한 비밀번호 재설정 등 회원정보 관리 기능
      - ID/Password 기반 회원가입 시 CAPTCHA 적용을 통한 부정행위 방지
  2) 데이터 모델 설계 및 ERD 작성
 
- 프로젝트 진행 중 작성한 글
  - [MySQL Error Code 1824. Failed to open the referenced table 'tablename'](https://limvik.github.io/posts/mysql-error-code-1824/)
  - [Spring Boot, MyBatis, MySQL Stored Procedure 사용 예제](https://limvik.github.io/posts/stored-procedure-example-in-spring-boot-mybatis-mysql/)
  - [Spring Security 로그아웃(Logout) 하기](https://limvik.github.io/posts/spring-security-logout-operation/)
  - [Spring Security 공부 글](https://limvik.github.io/categories/spring/)

# 구현 사항: 로그인/회원가입/회원정보 등 회원관련 화면 설계 및 구현

## 로그인/회원가입

- ID/Password 및 소셜 로그인(Google, Kakao, Naver) 기능

![로그인/회원가입](https://github.com/kdtkdt/NOWNESS/assets/135004614/cb92ee49-7765-41ae-9be2-98a1a73739cb)

### 관련 파일

- [login_signup.html](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/templates/login_signup.html)
- [login_signup.js](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/static/js/user/login_signup.js)
- [UserController.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/controller/UserController.java)
- [UserApiController.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/controller/UserApiController.java)
- [SignUpForm.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/controller/SignUpForm.java)
- [UserDetailsService.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/service/UserDetailsService.java)
- [OAuth2UserCustomService.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/service/OAuth2UserCustomService.java)
- [User.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/domain/User.java)
- [UserRepository.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/repository/UserRepository.java)
- [UserDTO.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/dto/UserDTO.java)
- [user-mapper.xml](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/mapper/user-mapper.xml)
- [CaptchaApiController.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/controller/CaptchaApiController.java)
- [NaverImageCaptchaService.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/captcha/NaverImageCaptchaService.java)
- [ApiConfig.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/config/ApiConfig.java) Naver Image Cpatcha API key 로딩

## 회원정보

![회원정보](https://github.com/kdtkdt/NOWNESS/assets/135004614/c456de35-07c9-4848-b5d1-97dfa7c4582f)

### 관련 파일

- [mypage.html](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/templates/mypage.html)
- [mypage.js](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/static/js/user/mypage.js)
- [UserController.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/controller/UserController.java#L104-L121)
- [UserApiController.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/controller/UserApiController.java)
- [UserDetailsService.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/service/UserDetailsService.java)
- [UserRepository.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/repository/UserRepository.java)
- [BoardRepository.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/repository/BoardRepository.java)
- [user-mapper.xml](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/mapper/user-mapper.xml)
- [board-mapper.xml](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/mapper/board-mapper.xml)

## 이메일 인증

![헤더에서 이메일 인증 필요 메시지](https://github.com/kdtkdt/NOWNESS/assets/135004614/62fb12e3-b890-4d33-b2b3-6178959a50dc)

![회원가입 시 발송되는 메일](https://github.com/kdtkdt/NOWNESS/assets/135004614/59e47b54-94b2-4213-9634-072a1acc0e46)

![이메일 인증 완료 시 화면](https://github.com/kdtkdt/NOWNESS/assets/135004614/14e13477-d108-451a-843e-e8f83ce157ed)

### 관련 파일

### 이메일 인증 및 비밀번호 재설정 기능을 개선할 방법

현재는 회원가입 시 혹은 인증 이메일 재발송 요청 시 UUID로 생성한 인증 코드를 데이터베이스에 저장하고, 인증 링크 클릭 시에 삭제하고 있습니다.

비밀번호 재설정 시에도 이메일 인증과 비슷하게 비밀번호 재설정 이메일을 보내면서 UUID로 생성한 인증 코드를 보내고, 데이터베이스에 저장합니다. 재설정이 완료되면 데이터베이스에서도 삭제됩니다.

그리고 보안을 위해 데이터베이스의 EVENT 기능을 이용하여 3일마다 삭제하고 있습니다.

```sql
CREATE EVENT delete_expired_password_reset_data
ON SCHEDULE EVERY 1 DAY
STARTS CURRENT_TIMESTAMP
DO
  DELETE FROM password_reset_lists
  WHERE date < DATE_SUB(NOW(), INTERVAL 3 DAY);
```

JWT(JSON Web Token)를 공부하기 시작하면서, JWT를 email 인증에 사용하는 사례를 보니 굳이 테이블을 새로 만들거나 EVENT로 데이터베이스에 부하를 발생시키지 않을 수 있겠다는 생각이듭니다.

```
관련 예제
https://example.com/confirm-email?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImpvaG5kb2VAZXhhbXBsZS5jb20iLCJpYXQiOjE2MDUxNzU4OTIsImV4cCI6MTYwNTE4MzA5Mn0.A9G_WUqabZn_3hNQPZTgS1K1S9HaoQIGtSowuhcXfL4
```

JWT를 막 공부하기 시작했기 때문에, 상황에 따라 단점이 있는지 파악이 필요하겠습니다.

## 사용자 작성 게시글/댓글 목록

사용자 작성 게시글과 댓글 목록 화면은 UI를 공유하므로 게시글 목록 스크린샷만 추가합니다.

![사용자 작성 게시글 목록](https://github.com/kdtkdt/NOWNESS/assets/135004614/44b8c1ee-8e21-487c-af27-882ae0f73484)

### 관련 파일

- [user_posts_replies.html](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/templates/user_posts_replies.html)
- [UserController.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/controller/UserController.java#L123-L157)
- [UserDetailsService.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/service/UserDetailsService.java#L206-L224)
- [BoardRepository.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/repository/BoardRepository.java)
- [board-mapper.xml](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/mapper/board-mapper.xml#L15-L39)

## 회원탈퇴

![회원탈퇴 화면](https://github.com/kdtkdt/NOWNESS/assets/135004614/e1813ae5-db4f-4041-a33d-fac08689d73f)

### 관련 파일

- [withdrawal.html](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/templates/withdrawal.html)
- [withdrawal.js](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/static/js/user/withdrawal.js)
- [UserController.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/controller/UserController.java#L143)
- [UserDetailsService.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/service/UserDetailsService.java#L227)
- [UserRepository.java](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/java/highfive/nowness/repository/UserRepository.java#L25)
- [user-mapper.xml](https://github.com/kdtkdt/NOWNESS/blob/sg/src/main/resources/mapper/user-mapper.xml#L69)


## 데이터 모델 설계 및 ERD 작성

![nowness ERD](https://github.com/kdtkdt/NOWNESS/assets/135004614/f20c4529-52b3-45ad-a914-010168d0e294)

### 협의 사항

- 사용자 탈퇴 시 게시글 자동 삭제되지 않음
- 관리자가 게시글 삭제 시 댓글, 첨부파일, 좋아요, 태그 등 모두 함께 삭제

## 하려다가 안한 것들

- 관리자 기능: 각 팀원들이 개별 기능을 완성하지 못한 것이 많아 제외하였습니다.
- Let's Encrypt를 이용한 HTTPS 적용 및 배포: 개인 프로젝트에서 적용할 계획입니다.
- 테스트 코드 작성: 다음 프로젝트에서 테스트 코드 먼저 작성하는 방식을 적용하고 있습니다.
- AOP를 이용한 로그인 여부 확인, 이메일 인증 여부 확인: 굳이 AOP로 해야 할 필요성을 못느껴 만들었다가 삭제했습니다.
- 로그인/회원가입 시 키 입력 감지 및 유효성, 중복 검사 개선(키워드: 디바운싱, 쓰로틀링): 개인 프로젝트에서 적용할 계획입니다.

## 기술적으로 어려웠던 점
- jenkins 에서 jar 파일 실행 시 환경변수를 불러오지 못하는 문제를 해결하지 못해, command line 에서 직접 jar 파일을 실행시켰습니다.
- javascript 중복 코드가 발생해도 thymeleaf 와 함께 쓸 때의 best pratice는 찾기가 어려웠습니다.
