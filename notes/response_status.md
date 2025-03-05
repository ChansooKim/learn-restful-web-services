# Response Status
***
`200` Success
`201` Created
`204` No Content
`401` Unauthorized (인증실패 시)
`400` Bad Request (validation error 같은)
`404` Resource Not Found
`500` Server Error


응답 상태를 잘 활용하여 응답해줘야 한다.

``` java
@PostMapping("/users")  
public ResponseEntity<User> createUser(@RequestBody User user) {  
    service.save(user);
    return ResponseEntity.created(null).build();  
}
```
-> ResponseEntity를 통해 201(created) 상태코드를 반환할 수 있다.

** 여기에, 추가로 어떤 사용자가 생성됐는지 알려줄 수 있다.
`/users/4` 를 반환하면 사용자는 해당 location에 요청을 보낼 수 있게 된다.

=> 이를 `location 헤더`라고 한다.

`ResponseEntity.created()` 메서드는 URI location을 인자로 받는다.

``` java
@PostMapping("/users")  
public ResponseEntity<User> createUser(@RequestBody User user) {  
    User savedUser = service.save(user);  
    URI location = ServletUriComponentsBuilder.fromCurrentRequest()  
            .path("/{id}")  
            .buildAndExpand(savedUser.getId())  
            .toUri();  
    return ResponseEntity.created(location).build();  
}
```
location을 생성해서 인자로 함께 반환할 수 있다.

응답헤더로 { Location: http://localhost:8080/users/4 } 값이 추가된 것을 확인할 수 있다.

> API의 소비자는 해당 URL을 이용해 조회할 수 있다.
>
> REST API를 만들 땐 꼭 소비자의 입장에서 생각해야 한다.