# HAL Explorer
***
의존성
``` xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-actuator</artifactId>  
</dependency>
```
http://localhost:8080/explorer/index.html# 로 접근한다.

`HAL`(JSON Hypertext Application Language):
API의 리소스 간 하이퍼링크를 제공하는 일관되고 쉬운 형식

`HAL Explorer`
- HAL을 사용하는 RESTful 하이퍼미디어 API를 위한 탐색 도구
- 비개발자 팀도 API를 쉽게 사용할 수 있도록 지원

`Spring Boot HAL Explorer`
- Spring Boot 프로젝트에서 HAL Explorer를 자동 설정
- `spring-data-rest-hal-explorer` 의존성 사용