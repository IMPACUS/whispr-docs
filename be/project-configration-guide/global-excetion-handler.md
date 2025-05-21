### Global Excetion Handler 가이드

`GeneralException` 클래스는 애플리케이션 전반에서 발생할 수 있는 예외를 처리하기 위해 설계된 커스텀 예외 클래스입니다. 이 클래스는 HTTP 상태 코드, 오류 코드, 상세 정보를 포함하여 예외를 보다 명확하게 표현할 수 있도록 도와줍니다.

---

#### **클래스 위치**
- 파일 경로: `src/main/java/com/impacus/whispr/global/exception/GeneralException.java`

---

#### **주요 기능**
1. **HTTP 상태 코드 포함**  
   예외 발생 시 관련 HTTP 상태 코드를 포함하여 클라이언트에 적절한 응답을 제공합니다.

2. **오류 코드 관리**  
   `ErrorCode` 인터페이스를 사용하여 예외의 유형을 명확히 구분합니다.

3. **상세 정보 제공**  
   예외와 관련된 추가적인 상세 정보를 포함할 수 있습니다.

---

#### **필드 설명**

- **`HttpStatus status`**: HTTP 상태 코드를 나타냅니다.
- **`ErrorCode errorCode`**: 예외의 유형을 나타내는 오류 코드입니다.
- **`Object detail`**: 예외와 관련된 추가적인 상세 정보입니다.

---

#### **사용 예시**

```java
throw new GeneralException(HttpStatus.NOT_FOUND, CommonErrorCode.RESOURCE_NOT_FOUND);
```

```java
throw new GeneralException(CommonErrorCode.INVALID_INPUT, "입력 값이 유효하지 않습니다.");
```

---

이 가이드는 `GeneralException`을 올바르게 이해하고 사용할 수 있도록 돕기 위해 작성되었습니다. 추가적인 질문이 있다면 팀원들에게 문의하세요.