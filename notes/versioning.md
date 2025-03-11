# 버전 관리 (Versioning)
***
> REST API를 많은 클라이언트가 사용중인 경우, API 변경 사항이 발생했을 때
버전 관리를 통해 클라이언트가 유연하게 사용하도록 할 수 있다.

#### 버전 관리의 종류
- URL 기반 버전 관리
- 요청 매개변수(Request Parameter) 활용
- 헤더(Header) 기반 버전 관리
- 미디어 타입(Media Type) 기반 버전 관리

##### URL 기반 버전 관리 - Twitter
``` java
@GetMapping("/v1/person")  
public PersonV1 getFirstVersionOfPerson() {  
    return new PersonV1("Bob Charlie");  
}  
  
@GetMapping("/v2/person")  
public PersonV2 getSecondVersionOfPerson() {  
    return new PersonV2(new Name("Bob", "Charlie"));  
}
```
##### Request Parameter 활용 버전 관리 - Amazon
``` java
@GetMapping(path = "/person", params = "version=1")  
public PersonV1 getFirstVersionOfPersonRequestParameter() {  
    return new PersonV1("Bob Charlie");  
}  

@GetMapping(path = "/person", params = "version=2")  
public PersonV2 getSecondVersionOfPersonRequestParameter() {  
    return new PersonV2(new Name("Bob", "Charlie"));  
}
```
##### (Custom) Header 기반 버전 관리 - Microsoft
``` java
@GetMapping(path = "/person", headers = "X-API-VERSION=1")  
public PersonV1 getFirstVersionOfPersonRequestHeader() {  
    return new PersonV1("Bob Charlie");  
}  
  
@GetMapping(path = "/person", headers = "X-API-VERSION=2")  
public PersonV2 getSecondVersionOfPersonRequestHeader() {  
    return new PersonV2(new Name("Bob", "Charlie"));  
}
```
별도의 헤더 `X-API-VERSION` 추가
##### 미디어 타입 기반 버전 관리 - GitHub
``` java
@GetMapping(path = "/person/accept", produces = "application/vnd.company.app-v1+json")  
public PersonV1 getFirstVersionOfPersonAcceptHeader() {  
    return new PersonV1("Bob Charlie");  
}  
  
@GetMapping(path = "/person/accept", produces = "application/vnd.company.app-v2+json")  
public PersonV2 getSecondVersionOfPersonAcceptHeader() {  
    return new PersonV2(new Name("Bob", "Charlie"));  
}
```
`accept` 헤더에 produces에 지정된 값을 사용


##### 고려사항
- URI 오염 (URI Pollution)
- HTTP 헤더의 오용 (Misuse of HTTP Headers)
- 캐싱 (Caching)
- 브라우저에서 요청을 실행할 수 있는가?
- API 문서화 (API Documentation)

##### Summary
***
완벽한 해결책은 없음 (No Perfect Solution)
- 필요하기 전에 미리 버전 관리에 대해 고민해야 한다
- 하나의 Enterprise에서는 하나의 버전 관리 방식`One Versioning Approach`을 유지하는 것이 좋음