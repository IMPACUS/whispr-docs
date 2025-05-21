### DB 암호화 복호화 컨버터 (AES256ToStringConverter)

`AES256ToStringConverter`는 JPA 엔티티의 속성을 AES-256 알고리즘을 사용하여 암호화/복호화하는 데 사용되는 클래스입니다. 이 클래스는 데이터베이스에 민감한 정보를 안전하게 저장하기 위해 설계되었습니다.

---

#### **클래스 위치**

- 파일 경로: `src/main/java/com/impacus/whispr/global/converter/AES256ToStringConverter.java`

---

#### **주요 기능**

1. **데이터베이스 저장 시 암호화**
   엔티티의 속성을 데이터베이스에 저장하기 전에 AES-256 알고리즘을 사용하여 암호화합니다.
2. **데이터베이스 조회 시 복호화**
   데이터베이스에서 조회된 암호화된 데이터를 AES-256 알고리즘을 사용하여 복호화합니다.

#### **의존성**

- **`AES256Util`**: AES-256 암호화/복호화 로직을 처리하는 유틸리티 클래스입니다.

---

#### **사용 예시**

```java
@Entity
public class User {

    @Convert(converter = AES256ToStringConverter.class)
    private String sensitiveData;

    // Getter, Setter, etc.
}
```

- `@Convert` 애너테이션을 사용하여 엔티티의 특정 필드에 `AES256ToStringConverter`를 적용합니다.
- `sensitiveData` 필드는 데이터베이스에 암호화된 상태로 저장되며, 조회 시 자동으로 복호화됩니다.

---

#### **주의사항**

1. `AES256Util` 클래스의 `secretKeyAES` 값이 올바르게 설정되어 있어야 합니다.
