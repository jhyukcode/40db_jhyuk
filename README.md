# 📚 스마트 도서 대여 플랫폼 (전자 도서 대출 시스템)

> 40db 팀프로젝트 | 2025.04.10 ~ 2025.04.30  
> 전자 도서를 OAuth 기반으로 대출·반납하고, 마이페이지에서 회원 정보를 관리할 수 있는 웹 서비스입니다.

---

## 🔧 개발 환경

- **Backend**: Spring Boot 2.7, Spring Security 5.0.7, JPA
- **Frontend**: Thymeleaf, JQuery
- **DB**: **MySQL 8.0**
- **API**: Aladin Open API, Naver/Kakao/Google Auth API, Daum 우편번호 API
- **협업 도구**: Git, SourceTree, Notion

---

## 🌟 주요 기능

- OAuth 2.0 기반 소셜 로그인 (Google, Naver, Kakao)
- Aladin API 연동을 통한 도서 조회 및 등록
- 도서 대출/반납 기록 관리
- 사용자 마이페이지 및 정보 수정
- 사용자 주소 검색 (Daum 우편번호 API)

---

## 👤 담당 역할 - *회원 인증 및 마이페이지 설계*

### ✅ 구현 내용

- **OAuth 2.0 소셜 로그인 연동**
  - Google, Naver, Kakao Auth API를 통한 사용자 인증 구현
  - 인증 후 사용자 정보 DB(MySQL)에 저장 및 세션 관리

- **우편번호 인증 연동**
  - 다음 우편번호 API를 활용하여 주소 검색 기능 구현
  - 회원 가입 시 입력한 주소를 마이페이지에 연동

- **회원 정보 관리**
  - 로그인/회원가입 이후 사용자 정보를 수정할 수 있는 마이페이지 설계 및 구현
  - 사용자 정보 조회, 수정, 탈퇴 기능 구현

---

### 🛠 트러블슈팅

1. **소셜 로그인 시 NullPointerException 발생**
   - **원인**: 각 OAuth 제공사(Naver, Kakao, Google)에서 반환하는 JSON 구조가 다름
   - **해결**: 사용자 정보를 파싱할 때 각 플랫폼별로 로직을 분기 처리하여 해결

2. **OAuth 인증 시 사용자 정보 제한**
   - **원인**: `@AuthenticationPrincipal`을 통해 가져올 수 있는 정보가 제한됨
   - **해결**: 커스텀 `UserDetails` 객체를 생성하고, `PrincipalDetails`에 추가 정보를 주입하여 해결

3. **Git Push 거부**
   - **원인**: `application.properties`에 API Key가 포함되어 보안 경고 발생
   - **해결**: 민감 정보는 `oauth.properties`로 분리하고 `.gitignore`에 추가  
     - API Key는 팀 내 메신저를 통해 별도 공유

---

## 🚀 기술적 성장 포인트

- **Spring Security 기반 OAuth 인증 구조 이해**
- **외부 API와 연동 시 로직 분기 및 예외 처리 경험**
- **MySQL 기반 데이터 설계 및 사용자 정보 관리**
- **보안 파일 관리 (gitignore 및 config 분리)에 대한 실전 경험**
- **Git GUI 도구(SourceTree) 숙련도 향상**

---

## 🤝 협업 경험 및 회고

- Notion을 활용한 요구사항 정리 및 역할 분담
- MySQL 기반 ERD 설계 후 팀원들과 지속적으로 스키마 조율
- Git 사용에 미숙했던 부분은 피드백을 바탕으로 SourceTree를 통해 보완
- 향후 연동 기능의 설계를 더 체계적으로 구성하고, UI 구현 역량도 강화하고자 함
