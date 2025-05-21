## APIResponseEntity 공통 응답 포맷 가이드

`APIResponseEntity` 클래스는 API 응답을 표준화하여 클라이언트에 전달하기 위한 DTO(Data Transfer Object)입니다. 이 클래스는 메시지와 데이터를 포함하며, 페이징 또는 슬라이싱된 데이터를 처리하는 정적 메서드를 제공합니다.

---

#### **클래스 위치**
- 파일 경로: `src/main/java/com/impacus/whispr/global/dto/response/APIResponseEntity.java`

---

#### **주요 기능**
1. **일반 응답 처리**  
   메시지와 데이터를 포함하는 API 응답 객체를 생성합니다.

2. **페이징 응답 처리**  
   `Page` 객체를 기반으로 페이징된 응답 데이터를 생성합니다.

3. **슬라이싱 응답 처리**  
   `Slice` 객체를 기반으로 슬라이싱된 응답 데이터를 생성합니다.

---

#### **필드 설명**
- **`String message`**: 응답 메시지를 나타냅니다.
- **`T data`**: 응답 데이터로, 제네릭 타입을 사용하여 다양한 데이터 타입을 지원합니다.

---

#### **정적 메서드 설명**

1. **`toPage(String message, Page<T> page)`**
   - **설명**: 페이징된 데이터를 포함하는 응답 객체를 생성합니다.
   - **입력**: 
     - `String message`: 응답 메시지
     - `Page<T> page`: 페이징된 데이터
   - **출력**: `APIResponseEntity<PageResponse<T>>`
   - **예시**:
     ```java
     Page<User> userPage = userService.getUsers();
     APIResponseEntity<PageResponse<User>> response = APIResponseEntity.toPage("사용자 목록 조회 성공", userPage);
     ```

2. **`toSlice(String message, Slice<T> slice)`**
   - **설명**: 슬라이싱된 데이터를 포함하는 응답 객체를 생성합니다.
   - **입력**: 
     - `String message`: 응답 메시지
     - `Slice<T> slice`: 슬라이싱된 데이터
   - **출력**: `APIResponseEntity<SliceResponse<T>>`
   - **예시**:
     ```java
     Slice<User> userSlice = userService.getUserSlice();
     APIResponseEntity<SliceResponse<User>> response = APIResponseEntity.toSlice("사용자 슬라이스 조회 성공", userSlice);
     ```

---

#### **사용 예시**

1. **일반 응답**
   ```java
   APIResponseEntity<String> response = APIResponseEntity.<String>builder()
       .message("요청 성공")
       .data("Hello, World!")
       .build();
   ```

2. **페이징 응답**
   ```java
   Page<User> userPage = userService.getUsers();
   APIResponseEntity<PageResponse<User>> response = APIResponseEntity.toPage("사용자 목록 조회 성공", userPage);
   ```

3. **슬라이싱 응답**
   ```java
   Slice<User> userSlice = userService.getUserSlice();
   APIResponseEntity<SliceResponse<User>> response = APIResponseEntity.toSlice("사용자 슬라이스 조회 성공", userSlice);
   ```

---

#### **주의사항**
1. `PageResponse`와 `SliceResponse` 클래스는 별도로 정의되어 있어야 하며, 페이징 및 슬라이싱 데이터를 적절히 매핑해야 합니다.
2. 제네릭 타입(`T`)을 사용하여 다양한 데이터 타입을 처리할 수 있도록 설계되었습니다.
3. 응답 메시지는 클라이언트가 이해하기 쉽도록 명확하게 작성해야 합니다.