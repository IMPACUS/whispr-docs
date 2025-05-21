# 개발 환경 구성하는 방법

## intellij 설정

1. git repository clone
2. intellij로 Project 열기
3. Settings
4. Editor > Code Style > Java 선택
5. Scheme 에  [Default] 선택
6. (선택 사항)
   1. Tools > Actives On Save 선택
   2. 아래와 같이 설정하면, 저장할 떄마다 코드 스타일에 맞게 적용됩니다.
   ![alt text](<assets/20250519_184941__2025-05-19 오후 6.48.01.png>)

## docker 설정

만약 개발 환경에서 사용한 DB 등 컨테이너 정보를 확인하고 싶은 경우, compose.yml를 참고하세요.
기본 설정으로는 spring 서버가 띄워져 있는 경우에만 container를 실행합니다. 설정을 변경하고 싶은 경우 하단을 확인하세요.

```
spring.docker.compose.lifecycle-management 설정에 아래 옵션 사용
- none : 말 그대로 아무것도 하지 않음 (Docker Compose 시작도 종료도 하지 않음).
- start-only: 애플리케이션이 시작될 때 Docker Compose를 시작하고 실행 상태로 유지함.
- start-and-stop: 애플리케이션이 시작되면 Docker Compose를 시작하고 JVM이 종료되면 중지함.
```

1. docker-compose 설치 (2.2.0 이상 버전 설치)
2. (Window, Mac)인 경우 docker desktop 설치
