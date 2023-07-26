# NOWNESS
- 국비지원 풀스택 과정 팀 프로젝트
- 기획 의도: 지역 현장 정보 공유를 통한 사회적 비용(인파 집중으로 인한 문제 등) 감소
- 기간 및 인원: 진행중 / 5명(풀스택)

- 기술 스택
  - Backend: Java 17, Spring Boot 3, Thymeleaf, Spring Security 6, MyBatis 3, MySQL 8
  - Frontend: Bootstrap, JavaScript, jQuery
  - 외부 API: Naver Image CAPTCHA API

- 구현 사항
  1) 로그인/회원가입/회원정보 등 회원관련 화면 설계 및 구현
      - ID/Password 및 소셜 로그인(Google, Kakao, Naver) 기능
        - 구현 일정을 맞추기 위해 구현을 하기는 했지만, Spring Security에 대해 이해하지 못하고 구현을 하여 지속적으로 공부하고 블로그에 글을 남기고 있습니다.([블로그 링크](https://limvik.github.io/categories/spring/)) 
      - 인증 이메일 발송/재발송, 이메일을 통한 비밀번호 재설정 등 회원정보 관리 기능
      - ID/Password 기반 회원가입 시 CAPTCHA 적용을 통한 부정행위 방지
  2) 데이터 모델 설계 및 ERD 작성

- 향후 계획
  - 관리자 기능
  - Let's Encrypt를 이용한 HTTPS 적용 및 배포
  - 테스트 코드 작성
  - AOP를 이용한 로그인 여부 확인, 이메일 인증 여부 확인
  - 로그인/회원가입 시 키 입력 감지 및 유효성, 중복 검사 개선(키워드: 디바운싱, 쓰로틀링)
 
- 프로젝트 진행 중 작성한 글
  - [MySQL Error Code 1824. Failed to open the referenced table 'tablename'](https://limvik.github.io/posts/mysql-error-code-1824/)
  - [Spring Boot, MyBatis, MySQL Stored Procedure 사용 예제](https://limvik.github.io/posts/stored-procedure-example-in-spring-boot-mybatis-mysql/)
  - [Spring Security 공부 글](https://limvik.github.io/categories/spring/)

# 구현 사항

## 로그인/회원가입/회원정보 등 회원관련 화면 설계 및 구현

### 로그인/회원가입

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

### 회원정보

![회원정보](https://github.com/kdtkdt/NOWNESS/assets/135004614/c456de35-07c9-4848-b5d1-97dfa7c4582f)

### 사용자 작성 게시글/댓글 목록

사용자 작성 게시글과 댓글 목록 화면은 UI를 공유하므로 게시글 목록 스크린샷만 추가합니다.

![사용자 작성 게시글 목록](https://github.com/kdtkdt/NOWNESS/assets/135004614/44b8c1ee-8e21-487c-af27-882ae0f73484)

## 데이터 모델 설계 및 ERD 작성

![nowness ERD](https://github.com/kdtkdt/NOWNESS/assets/135004614/e95fcdcd-5e3a-4ef7-bc4f-2903403ec189)
