## 그라운드 룰
- 개발 IDEA: InteillJ
  - 로컬 개발 환경은 docker/docker-compose로 자동 구축
- 코드 컨벤션: InteillJ Default
- 백앤드 Task 관리: Github issue/칸반보드
- Logging 시스템 및 포맷 : ??
- DB 마이그레이션 툴: liquibase
- 테스트 코드
  - 테스트 코드 필수 여부:
  - 커버리지:
  - pr 조건 추가 여부:
- pr 조건 추가 :
  - 코드 리뷰
  - 테스트 코드 커버리지
  - 정적 분석
- 코드 리뷰 여부:
- API docs: Swagger-ui
- 삭제 정책: soft delete
- API rule: Restful API
  - API rule 에서 구현 중 적용하기에 어려운 예외적인 케이스에 대해서는 상황에 따라 허용
- 코드
  - 의존성 주입 방법: 생성자 주입
  - Service 관리: `@Transactional(readOnly = true)`
  - 권한: `@PreAuthorize`
  - queryDSL 사용 여부: O
  - ResponseEntity 포맷
  - Entity column 암호화 알고리즘: `AES256`

    - `@Convert(converter = AES256ToStringConverter.class)`
  - 예외 처리 관리 포맷

    ```jsx
    {
        "code": "101_INVALID_TOKEN", // 에러 코드
        "msg": "유효하지 않은 토큰입니다.", // 에러 설명
        "detail": ""
    }
    ```
  - Enum 유효성 검사 어노테이션: `@ValidEnum`
  - XSS 필터 설정
- 네이밍룰
  - Class :
    - 약어인 경우, 대문자를 사용 (예시, DTO)
    - CRUD 작업에 따라 DTO 또는 명세 클래스의 이름은 해당 동작을 명확히 드러내도록 작성
      - 형식: `동작 + 도메인명 + 접미어`
        - `Create` : 생성 작업
        - `Read` 또는 `Get` : 조회 작업
        - `Update` : 수정 작업
        - `Delete` : 삭제 작업
      - 예시: `CreateProductDTO`, `UpdateUserRequest`, `DeleteOrderCommand`, `GetUserResponse` 등
  - 패키지: 전부 소문자 사용
- 복잡한 플로우 및 설계가 존재하는 경우, 개인 판단에 따라 Flow chart 혹은 UML 작성 (whispr-docs에서 관리)

### Backend Deploy Spec (dev)

- AWS EC2 + docker
- DB: AWS RDS
  - 서버가 커지면, K8S 고려중
- CICD:
  - dev: git action
  - prod: github action vs jenkins vs Code deploy
- HTTPS: nginx로 SSL 설정하여 라우팅

### 협업 규칙(Github Organization 사용)

#### Git 관리 규칙

**Branch 관리**

- Gitflow 방식 (release 브랜치를 제외하고 사용하는 방식) master/develop/feature/hotfix
  - 예시: feature/{자신 이름 key}/**

**Commit**

```jsx
<Type>: <subject>  (#이슈번호)     -- 헤더
<BLANK LINE>
<body>                           -- 본문 (생략 가능)

Type
- feature : 새로운 기능에 대한 커밋
- fix : 버그 수정에 대한 커밋
- build : 빌드 관련 파일 수정에 대한 커밋
- chore : 그 외 자잘한 수정에 대한 커밋
- ci : CI관련 설정 수정에 대한 커밋
- docs : 문서 수정에 대한 커밋
- style : 코드 스타일 혹은 포맷 등에 관한 커밋
- refactor :  코드 리팩토링에 대한 커밋
- test : 테스트 코드 수정에 대한 커밋
```

### 함수 네이밍 룰

#### API Path

1. 맨 앞에 `api` 사용
2. 다음, 버전을 나타내는 `v1` 와 같은 문자 사용

```jsx
(api/v1/{entity}/**
```

#### Enum 저장 타입

- @Enumerated(EnumType.String)

#### 생성자 생성 규칙

- [정적 팩토리 메서드 패턴](https://velog.io/@saint6839/%EC%A0%95%EC%A0%81-%ED%8C%A9%ED%86%A0%EB%A6%AC-%EB%A9%94%EC%84%9C%EB%93%9C-%EB%84%A4%EC%9D%B4%EB%B0%8D-%EB%B0%A9%EC%8B%9D)

### 패키지 구조:

- DDD
  - 공통으로 사용해야 하는 관리 폴더명: globla
  - 다대다 관계인 경우,
- controller, service, entity, repository, dto
- DTO 명칭 (Request, Response 명칭)
  - App → Controller: Request
  - App ← Controller: Response
