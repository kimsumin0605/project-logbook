# 🚗 Dear Carmate Backend
* Team3 김수민
##### 🔗 배포링크(홈페이지) : https://example.com
####  🔗 Swagger 문서 : 
####  🔗 Team wiki : 
## 프로젝트 소개

<p>
 🚗 중고차 계약 관리 서비스 DearCarmate<br/>
     중고차 계약, 간편하고 스마트하게
     복잡한 계약 관리, 이젠 한 곳에서 해결하세요.
</p>


<p>
<strong>🗓️ 프로젝트 기간 : 2025.07.22 ~ 2025.08.13</strong>
</p>

## 기술 스택

<h3 align="center"><b>📚 Languages 📚</b></h3>

<p align="center"> <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" /> 
<img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white" /> </p>

<h3 align="center"><b>⚙️ Frameworks & Libraries</b></h3>

<p align="center"> <img src="https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white" /> <img src="https://img.shields.io/badge/Prisma-2D3748?style=for-the-badge&logo=prisma&logoColor=white" /><br/>  <img src="https://img.shields.io/badge/Passport-34E27A?style=for-the-badge&logo=passport&logoColor=white" /> <img src="https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black" /> <img src="https://img.shields.io/badge/ESLint-4B32C3?style=for-the-badge&logo=eslint&logoColor=white" /> <img src="https://img.shields.io/badge/Prettier-F7B93E?style=for-the-badge&logo=prettier&logoColor=black" /> </p>

<h3 align="center"><b>🗄️ Database & Hosting</b></h3>

<p align="center"> <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" /> <img src="https://img.shields.io/badge/Render-0099E5?style=for-the-badge&logo=render&logoColor=white" /> </p>

<h3 align="center"><b>🔧 Development Tools </b></h3>

<p align="center"> <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" /> <img src="https://img.shields.io/badge/Nodemon-76D04B?style=for-the-badge&logo=nodemon&logoColor=white" /> <img src="https://img.shields.io/badge/TS Node-3178C6?style=for-the-badge&logo=ts-node&logoColor=white" /> <img src="https://img.shields.io/badge/Dotenv-ECD53F?style=for-the-badge&logo=dotenv&logoColor=black" /> </p>


<h3 align="center"><b>🔐 Authentication & Utility Libraries </b></h3>
<p align="center">
  <img src="https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=JSON%20web%20tokens&logoColor=white" alt="JWT" />
  <img src="https://img.shields.io/badge/Nodemailer-009966?style=for-the-badge&logo=gmail&logoColor=white" alt="Nodemailer" />
  <img src="https://img.shields.io/badge/Multer-1E90FF?style=for-the-badge&logo=files&logoColor=white" alt="Multer" />
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase" />
</p>

<h3 align="center"><b> 🤝 Collaboration Tools </b></h3>
<p align="center"> <img src="https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white" alt="Notion" /> <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" /> <img src="https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord" /> </p>

## 담당한 작업

 🔐 인증API 
 * 로그인 / 토큰 갱신 
   * POST /auth/login 
   * POST /auth/refresh

 👤 유저 API 
 * 회원가입 /  내 정보 조회 /  내  정보 수정 / 회원 탈퇴 / 유저 삭제
   * POST /users
   * POST /users/me
   * PATCH /users/me
   * DELETE /users/me
   * DELETE /users/me

🗄️데이터베이스 및 Seed 작업
 - 공용 DB 생성 및 Prisma 연결 (Render)
- Seed 파일 작성
 * seed.ts: 플랫폼 관리자 및 중고차 회사 8개 생성
   * 각 회사별 대표 1명, 일반 직원 5~8명 랜덤 생성
  * mock.ts: 각 회사별 차량, 고객, 계약, 미팅, 대시보드 통계 등 생성
  
   * ⚠️ Seed 실행 시 기존 데이터 삭제


## 기술적 성과 

#### 주요 구현 기능

 인증 구조 (Passport + 쿠키 기반)

📁  passport.ts
- Local 전략: 이메일/비밀번호 로그인 처리
- JWT 전략: 쿠키 또는 헤더에서 accessToken 추출 후 유저 인증

📁 jwt.ts
- accessToken, refreshToken 생성 및 검증 함수 제공
- HttpOnly 쿠키를 통해 토큰 클라이언트에 전달

📁 auth.ts
- 인증이 필요한 API에서 사용
- JWT 전략으로 사용자 검증 → 실패 시 401 반환

## 문제 해결 경험 (Trouble Shooting)

1. 스키마 필드명 불일치로 회원가입 오류 발생

* 문제: API 명세서와 다른 필드명을 사용하여 프론트와 연동 시 에러 발생

* 해결: 명세서 기준으로 스키마, DTO, 서비스의 필드명을 일관되게 수정

* 느낀점: API 개발 시 프론트와 명세서를 초기에 철저히 확인해야 함
----
2. DTO의 @IsOptional 누락으로 전체 필수 입력 오류
* 문제: TypeScript 옵셔널 속성만 선언하고, 유효성 검증 데코레이터 누락

* 해결: @IsOptional() 명시적으로 추가

* 느낀점: 타입과 런타임 검증은 별개이며, class-validator 사용법에 대한 명확한 이해 필요
---
3.  의존성 주입 리팩토링 중 라우터 오류 발생
* 문제: 컨트롤러 내부에서 서비스 객체 누락 → 콜백 함수 undefined 에러

라우터 연결 시 아래와 같은 오류 발생
```ts
[STATUS] 500
[MESSAGE] Route.post() requires a callback function but got a [object Undefined]
```
 * 콜백 함수가 정의되지 않아 라우팅이 실패한 상황

* 해결: Repository → Service → Controller 순으로 인스턴스 생성 및 주입 구조 재설계

```ts
const authRepository = new AuthRepository(prisma);
const authService = new AuthService(authRepository);
const authController = new AuthController(authService);
```
컨트롤러 메서드가 정상적으로 동작하도록 해결함.

느낀점:
코드 작성 시 타입 오류나 컴파일 에러가 없어 문제가 없는 줄 알았지만, 실제 서버를 실행하고 요청을 보내는 과정에서 500 에러가 발생함.
이번 경험을 통해, 런타임에 필요한 의존성이 제대로 주입되지 않으면 예기치 못한 에러가 발생할 수 있다는 점과, 의존성 구조를 명확하게 설계하는 것이 중요하다는 걸 깨달음.
단순히 폴더나 파일 구조만 만드는 데 그치지 않고, 각 레이어를 실제로 연결해 객체들이 서로 올바르게 참조하도록 해야 한다는 것도 배움.

## 어려웠던 점 및 아쉬운 점
1. 타 도메인 구조 이해 부족 → PR 리뷰 시 시간 소요

2. 계층별 책임 혼동 (Controller, Service, DTO 간 경계 불명확) 

3. TypeScript 설정 적용은 했지만 디버깅에는 시간이 많이 소요됨

4. 인증/인가 로직은 구현했지만 보안 취약점 존재 (서버 로그아웃 미구현)

5. 응답 속도 및 DB 효율성 고려 미흡

## 협업 및 피드백
1. 팀 위키
- 팀 위키를 적극 활용하여 문서화 → 빠른 정보 공유 가능

2. 코드리뷰를 하면서 새로운 것을 많이 알게됨. 또한 다른 팀원들의 코드를 보면서 새로운 접근 방식과 흐름을 배움.

## 코드 품질 및 최적화
- tsconfig, ESLint, Prettier 설정 → 코드 안정성과 일관성 확보
- 도메인 기반 레이어 아키텍처 도입
  * 관심사 분리
  * 의존성 명확화
  * 유지보수

 ## 향후 개선 사항 및 제안

- 프론트엔드에 회원 탈퇴 기능 미구현

-> 백엔드에는 해당 API가 구현되어 있으므로, 프론트엔드에 회원 탈퇴 UI 및 연동 기능을 추가하고 싶습니다.

- 로그아웃 기능 서버 측 처리로 개선 필요 백엔드에서 진행하도록 하고 싶음.

-> 현재는 프론트엔드에서 토큰을 삭제하는 방식으로 로그아웃을 처리하고 있지만, 백엔드에서 로그아웃 로직을 직접 다루는 구조로 개선해보면 좋을 거 같음.
이번 프로젝트에서는 Redis 등을 활용한 토큰 블랙리스트 방식을 도입하고 싶었으나, 프론트에서 로그아웃을 담당하면서 적용하지 못한 점이 아쉬웠다. 추후에는 Redis를 통한 보안성 강화도 함께 고려하고 싶다.

### 코드리뷰 진행 
---
시간이 오래 걸렸지만, 계약서 업로드 기능에 대한 PR 리뷰를 통해 새로운 기술 및 설계 방식을 학습할 수 있었다. 리뷰 과정에서 다른 팀원의 코드 스타일, 로직 구성 방식을 접하면서 더 나은 구현 방식에 대해 고민하게 되었다.

🔗 [계약서 PR 코드리뷰](https://github.com/nb02-DearCarmate-team03/Dear_Carmate_be/pull/73)

🔗 [로그인 및 토큰 재발급 PR](https://github.com/nb02-DearCarmate-team03/Dear_Carmate_be/pull/32)