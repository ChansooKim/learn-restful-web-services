# HATEOAS
***
`HATEOAS` Hypermedia as the Engine of Application State

> REST API를 향상해서 소비자에게 후속 작업을 수행하는 방법을 알려주는 것
>
> HATEOAS가 던지는 질문은 REST API를 향상하여 데이터를 반환할 뿐만 아니라
> 리소스에 관한 작업을 수행하는 방법의 정보를 제공하는 것이다.
>
> 데이터를 한 단계 더 업그레이드 시켜준다.

의존성 추가
``` xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-hateoas</artifactId>  
</dependency>
```

``` java
@GetMapping("/users/{id}")  
public EntityModel<User> retrieveUser(@PathVariable int id) {  
    User user = service.findOne(id);  
    if(user == null) {  
        throw new UserNotFoundException("id:"+id);  
    }  
    EntityModel<User> entityModel = EntityModel.of(user);  
    WebMvcLinkBuilder link = linkTo(methodOn(this.getClass()).retrieveAllUsers());  
    entityModel.add(link.withRel("all-users"));  
    return entityModel;  
}
```

``` json
{  
    "id": 1,  
        "name": "Adam",  
        "birthDate": "1995-03-11",  
        "_links": {  
		    "all-users": {  
		        "href": "http://localhost:8080/users"  
		    }  
		}  
}
```