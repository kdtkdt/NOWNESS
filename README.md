# NOWNESS

- 기획 의도: 지역 현장 정보 공유를 통한 사회적 비용(인파 집중으로 인한 문제 등) 감소
- 기간 및 인원: 진행중 / 5명

- 기술 스택
  - Backend: Java 17, Spring Boot 3, Thymeleaf, Spring Security 6, MyBatis 3, MySQL 8
  - Frontend: Bootstrap, JavaScript, jQuery
  - 외부 API: Naver Image CAPTCHA

- 구현 사항
  1) 로그인/회원가입/회원정보 등 회원관련 화면 설계 및 구현
  2) ID/Password 및 소셜 로그인(Google, Kakao, Naver) 기능
  3) 인증 이메일 발송/재발송, 이메일을 통한 비밀번호 재설정 등 회원정보 관리 기능
  4) ID/Password 기반 회원가입 시 CAPTCHA 적용을 통한 부정행위 방지
  5) 데이터 모델 설계 및 ERD 작성

- 향후 계획
  - 관리자 기능
  - Let's Encrypt를 이용한 HTTPS 적용 및 배포
  - 테스트 코드 작성
  - AOP를 이용한 로그인 여부 확인
  - 로그인/회원가입 시 키 입력 감지 및 유효성, 중복 검사 개선(키워드: 디바운싱, 쓰로틀링)

# 구현 사항

## 1. 로그인/회원가입/회원정보 등 회원관련 화면 설계 및 구현

### 로그인/회원가입 화면

![로그인/회원가입](https://github.com/kdtkdt/NOWNESS/assets/135004614/cb92ee49-7765-41ae-9be2-98a1a73739cb)

### 회원정보 화면

![회원정보 화면](https://github.com/kdtkdt/NOWNESS/assets/135004614/83e70d8e-55cb-4691-acb2-19bf1ddb52ed)
