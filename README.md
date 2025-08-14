# 🚗 Dear Carmate Backend
* Team3 김수민
##### 🔗 배포링크(홈페이지) : https://example.com
####  🔗 [Swagger 문서](https://nb02-dear-carmate-be03.onrender.com/api-docs/) 
####  🔗 [Team wiki](https://github.com/nb02-DearCarmate-team03/Dear_Carmate_be/wiki)
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

## 담당한 작업 및 기술적 성과

1.  인증API 
   * 로그인 / 토큰 갱신 
   * POST /auth/login 
   * POST /auth/refresh

   이번 프로젝트에서는 passport와 쿠키 기반 인증 방식을 사용하여 로그인 기능을 구현하였습니다. 이전 passport를 사용해 본 경험이 있어 구현이 비교적 수월했으며, 추후 소셜 로그인 기능을 추가한다면 확장성 측면에서도 유리하다고 판단하여 선택하였습니다.

  프론트엔드 명세서에 따르면 Authorization 헤더 방식으로 구현되어 있었기 때문에, 백엔드에서는 쿠키 방식과 헤더 방식을 모두 지원할 수 있도록 기능을 구현하였습니다.

  passport-local 전략을 통해 로그인 시 이메일과 비밀번호를 검증하였고, passport-jwt 전략을 통해 쿠키 또는 헤더에서 accessToken을 추출하여 payload.sub로 유저 정보를 조회하도록 구성하였습니다.

  또한 jwt.ts 파일을 별도로 분리하여 다음과 같은 기능을 구현하였습니다:

  * accessToken, refreshToken 생성 함수
  * refreshToken 검증 함수
  * HttpOnly 쿠키로 토큰 저장 처리

  아래는 쿠키 설정 코드입니다. (컨트롤러에서 accessToken을 설정한 부분입니다.)

```ts
res.cookie('accessToken', loginResponse.accessToken, {
  httpOnly: true,
  secure: process.env.NODE_ENV === 'production',
  maxAge: 15 * 60 * 1000, // 15분
});
```
* httpOnly: 클라이언트 측 JavaScript에서 접근하지 못하도록 설정
* secure: 배포 환경에서만 HTTPS를 통해 전송되도록 설정
* maxAge: 토큰의 만료 시간 설정 (15분)


2. 유저 API 
 * 회원가입 /  내 정보 조회 /  내  정보 수정 / 회원 탈퇴 / 유저 삭제
   * POST /users
   * POST /users/me
   * PATCH /users/me
   * DELETE /users/me
   * DELETE /users/me

유저 관련 API는 회원가입부터 시작하여, 로그인한 사용자의 정보 조회, 수정, 탈퇴 기능을 제공하며, 어드민 권한에서는 유저 삭제 기능까지 포함하고 있습니다. 기본적인 CRUD 작업 외에도 인증과 함께 동작하도록 구현하였습니다.

3. 유효성 검사 미들웨어

  유저 도메인뿐 아니라, 팀원들이 담당한 다른 도메인에서도 class-validator 및 class-transformer를 활용하여 유효성 검사를 적용하였습니다. 각 도메인 폴더 내에서 DTO를 정의하고, 모든 도메인에서 공통적으로 유효성 검사를 수행할 수 있도록 유틸리티 미들웨어 함수를 작성하였습니다.

  plainToInstance()를 사용하여 일반 JavaScript 객체를 클래스 인스턴스로 변환하고, 클래스에 정의된 데코레이터를 기준으로 유효성 검사를 수행하였습니다.

  이렇게 구현한 유효성 검사 미들웨어를 통해, 모든 도메인 라우터에서 아래와 같은형태로 사용할 수 있도록 구성하였습니다.

```ts
validateDto(LoginDto)
```

4. 인증 미들웨어 래핑 함수

  기존에 작성되어 있던 인증 미들웨어는 passport 기반이 아니었기 때문에, 인증이 필요한 라우터에서 오류가 발생하는 문제가 있었습니다. 이에 따라, 모든 도메인에서 공통적으로 사용할 수 있도록 passport 기반의 인증 미들웨어를 래핑하는 함수를 작성하였습니다.

  이 미들웨어를 통해 인증이 필요한 모든 라우터에서 일관된 방식으로 인증을 처리할 수 있게 하였으며, 팀원들도 동일한 방식으로 사용할 수 있도록 테스트 후 공유드렸습니다. 


5. 데이터베이스 및 Seed 작업
* 공용 데이터베이스 생성 (Render)
* Seed 파일 작성 및 더미데이터 생성

프로젝트 테스트의 편의성을 높이기 위해, seed.ts 파일을 작성하여 초기 데이터를 자동으로 생성할 수 있도록 하였습니다. 주요 내용은 다음과 같습니다:

 * 플랫폼 관리자 계정 생성
 * 중고차 회사 8개 생성
 * 각 회사별 대표 1명
 * 일반 직원 5~8명 랜덤 생성

또한 mock.ts 파일을 작성하여 각 회사별로 다음과 같은 데이터를 더미 형식으로 생성하였습니다:

 * 차량, 고객, 계약, 미팅 정보
* 대시보드 통계 데이터

random() 함수를 활용하여 수작업 없이 다양한 더미 데이터를 효율적으로 생성할 수 있도록 하였으며, 테스트와 개발 과정에서 데이터 활용이 용이하도록 구성하였습니다.

⚠️ 주의: Seed 실행 시 기존 데이터는 삭제되도록 설정되어 있습니다.

6. 프론트엔드/ 백엔드 배포

7. 최종 발표 PPT 제작


## 문제 해결 경험 (Trouble Shooting)

1. 스키마 필드명 불일치로 회원가입 오류 발생
* 문제: API 명세서와 다른 필드명을 사용하여 프론트와 연동 시 에러 발생하였습니다.
* 해결: 명세서 기준으로 스키마, DTO, 서비스의 필드명을 일관되게 수정해 문제를 해결했습니다.
* 느낀점: API 개발 초기 단계에서 프론트엔드 코드와 명세서를 정확하게 확인하고, 구조를 일치시키는 것이 매우 중요하다는 점을 다시 한 번 느꼈습니다. 
----
2. DTO의 @IsOptional 누락으로 전체 필수 입력 오류
* 문제: TypeScript 옵셔널 속성만 선언했지만, class-validator의 @IsOptional() 데코레이터를 누락하여 전체 필드가 필수로 처리되는 문제가 발생했습니다.
* 해결: @IsOptional() 명시적으로 추가하여 선택 입력 필드로 정상 동작하도록 수정하였습니다.
* 느낀점: TypeScript의 타입 시스템과 런타임 유효성 검증은 별개로 작동하기 때문에, class-validator의 사용법을 정확히 이해하고 사용하는 것이 중요하다고 느꼈습니다. 

---
3.  의존성 주입 리팩토링 중 라우터 오류 발생
* 문제: 컨트롤러 내부에서 서비스 객체 누락되어 콜백 함수 undefined로 처리되어 라우터 등록 시 오류가 발생했습니다.

라우터 연결 시 아래와 같은 오류 발생
```ts
[STATUS] 500
[MESSAGE] Route.post() requires a callback function but got a [object Undefined]
```
 * 콜백 함수가 정의되지 않아 라우팅이 실패한 상황

* 해결: Repository → Service → Controller 순으로 인스턴스 생성하고, 의존성을 명확하게 주입해 문제를 해결했습니다.

```ts
const authRepository = new AuthRepository(prisma);
const authService = new AuthService(authRepository);
const authController = new AuthController(authService);
```
컨트롤러 메서드가 정상적으로 동작하도록 해결함.

느낀점:
코드 작성 중 타입 오류나 컴파일 에러가 없더라도, 런타임 단계에서 필요한 의존성이 누락되면 예기치 못한 에러가 발생할 수 있다는 점을 경험했습니다. 의존성 주입 구조를 명확히 설계하는 것의 중요성을 깨달았고, 단순한 폴더 구조 설계에서 나아가 각 계층이 실제로 잘 연결되도록 구성해야 한다는 점도 배웠습니다.

## 어려웠던 점 및 아쉬운 점
1. 타 도메인 구조에 대한 이해 부족으로 인해 PR 리뷰 시 시간이 오래 소요되었습니다.
2. 컨트롤러, 서비스, DTO 간의 계층별 책임에 대한 이해가 부족하여 코드의 경계가 모호한 부분이 있었습니다.
3. TypeScript 설정은 적용했지만, 디버깅과 오류 추적에 시간이 많이 소요되었습니다.
4. 인증 및 인가 로직은 구현했지만, 서버 로그아웃 기능이 누락되어 보안 측면에서 아쉬움이 남았습니다.
5. 응답 속도나 데이터베이스 효율성에 대한 고려가 부족했습니다.

## 협업 및 피드백
1. 팀 위키
- 팀 위키를 적극 활용하여 문서화를 진행하였고, 이를 통해 빠르게 정보를 공유하고 참고할 수 있었습니다.

2. 코드 리뷰 경험
- 코드 리뷰를 통해 여러 관점을 배우고, 다른 팀원들의 코드를 보며 새로운 접근 방식과 흐름을 이해할 수 있었습니다. 피드백을 주고받는 과정에서 개발 역량 향상에 큰 도움이 되었습니다.

## 코드 품질 및 최적화
- tsconfig, ESLint, Prettier 등을 설정하여 코드의 일관성과 안정성을 확보하였습니다.
- 도메인 기반 레이어 아키텍처를 도입하여 다음과 같은 장점을 경험할 수 있었습니다:
  * 관심사 분리
  * 의존성 명확화
  * 유지보수성과 테스트 용이성 향상

 ## 향후 개선 사항 및 제안

- 프론트엔드에 회원 탈퇴 기능 미구현

  백엔드에서는 회원 탈퇴 API가 구현되어 있으므로, 프론트엔드에 해당 기능의 UI 및 연동 기능을 추가할 필요가 있습니다.

- 로그아웃 기능의 서버 측 처리 필요

  현재는 프론트엔드에서 토큰을 삭제하는 방식으로 로그아웃을 처리하고 있습니다.   그러나 보안 강화를 위해 백엔드에서 로그아웃을 직접 처리하는 구조로 개선할 필요가 있습니다.

  이번 프로젝트에서는 Redis를 활용한 토큰 블랙리스트 기능을 도입하고 싶었으나, 프론트엔드에 로그아웃 처리가 되어 있어 적용하지 못한 점이 아쉬웠습니다. 추후에는 Redis를 통한 세션 관리 및 보안 강화 방안도 함께 고려하고 싶습니다.

### 코드리뷰 진행 
---
시간이 다소 소요되었지만, 계약서 업로드 기능 PR 리뷰 과정을 통해 새로운 기술을 학습할 수 있었습니다. 리뷰 중에는 다른 팀원의 코드 스타일과 로직 구성 방식을 직접 확인할 수 있었고, 이를 통해 기존에 사용하던 방식보다 더 효율적이고 확장성 있는 구현 방법에 대해 고민하게 되었습니다.

🔗 [계약서 PR 코드리뷰](https://github.com/nb02-DearCarmate-team03/Dear_Carmate_be/pull/73)

🔗 [로그인 및 토큰 재발급 PR](https://github.com/nb02-DearCarmate-team03/Dear_Carmate_be/pull/32)