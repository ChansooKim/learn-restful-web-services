# Validation
***
`@Valid` 어노테이션을 사용하면
바인딩이 수행될 때 객체에 정의된 유효성 검증이 자동으로 수행된다.

``` java
@PostMapping("/users")  
public ResponseEntity<User> createUser(@Valid @RequestBody User user) {  
    User savedUser = service.save(user);  
    URI location = ServletUriComponentsBuilder.fromCurrentRequest()  
            .path("/{id}")  
            .buildAndExpand(savedUser.getId())  
            .toUri();  
    return ResponseEntity.created(location).build();  
}
```

``` java
@Override  
protected ResponseEntity<Object> handleMethodArgumentNotValid(  
        MethodArgumentNotValidException ex, HttpHeaders headers, HttpStatusCode status, WebRequest request) {  
    ErrorDetails errorDetails = new ErrorDetails(LocalDateTime.now()  
            , ex.getFieldError().getDefaultMessage(), request.getDescription(false));  
    return new ResponseEntity<>(errorDetails, HttpStatus.BAD_REQUEST);  
}
```
-> `ex.getFieldError().getDefaultMessage()` 첫 번째 메시지만 출력하도록 한다.

``` java
public class User {  
    private Integer id;  
    @Size(min = 2, message = "Name should have atleast 2 characters")  
    private String name;  
    @Past(message = "Birth Date should be in the past")  
    private LocalDate birthDate;  
  
    public User(Integer id, String name, LocalDate birthDate) {  
        super();  
        this.id = id;  
        this.name = name;  
        this.birthDate = birthDate;  
    }
    ...
}
```
size, past 여부 등 validation을 설정하고, 원하는 메시지도 반환할 수 있다.

error message
``` json
{
	"timestamp": "2025-03-06T15:34:33.254952",
	"message": "Name should have atleast 2 characters",
	"details": "uri=/users"
}
```