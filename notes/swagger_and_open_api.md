# Swagger & Open API
***
#### 개요
`2011년` Swagger Specification과 Swagger 도구(Tools) 출시
`2016년` Swagger 명세를 기반으로 Open API 명세(Specification) 생성
- Swagger 도구(예: Swagger UI)는 여전히 존재함
  `OpenAPI Specification` 표준화된 언어 독립적인 인터페이스
- REST API를 발견하고 이해하는 데 도움을 줌
- 이전에는 Swagger 명세로 불림
  `Swagger UI` REST API를 시각적으로 확인하고 상호작용 가능
- OpenAPI 명세로부터 자동 생성 가능

#### springdoc-openapi
https://github.com/springdoc/springdoc-openapi

의존성 추가 (SpringBoot 3.4.3 기준)
``` xml
<dependency>  
    <groupId>org.springdoc</groupId>  
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>  
    <version>2.8.5</version>  
</dependency>
```

swagger 접속 url
http://localhost:8080/swagger-ui/index.html

http://localhost:8080/v3/api-docs
-> 노출된 모든 리소스에 관한 세부 정보를 확인할 수 있다.
Bean의 Validation 설정까지 확인할 수 있다.
    