# SpringBoot Actuator
***
> SpringBoot Actuator는 프로덕션 레벨에서 다양한 기능을 제공해서
> 애플리케이션을 프로덕션 환경에서 모니터링하고 관리할 수 있게 해준다.

의존성
``` xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-actuator</artifactId>  
</dependency>
```

http://localhost:8080/actuator
actuator에서 제공하는 앤드포인트들을 확인할 수 있다.
-> 기본적으로 Actuator는 애플리케이션의 상태 정보만 공개한다.

더 많은 정보를 확인하려면 `applications.properties`에 아래 라인을 추가한다.
``` properties
management.endpoints.web.exposure.include=*
```

주요 앤드포인트
- `beans` - 애플리케이션 내 모든 Spring Bean 목록 확인
- `health` - 애플리케이션 상태(Health) 정보 제공
- `metrics` - 애플리케이션 성능 지표 제공
- `mappings` - 요청 매핑(Request Mappings) 상세 정보 제공
- 그 외 다양한 기능을 지원한다.