# 정적/동적 필터링
***
REST API와 관계없이 항상 필드를 차단하거나 필터링해야 하는 경우
-> 정적 필터링

응답의 일부로 필드를 전송할지 동적으로 결정하는 경우
-> 동적 필터링

### 정적 필터링 (Static Filtering)
``` java
public class SomeBean {  
    private String field1;  
    @JsonIgnore  
    private String field2;  
    private String field3;
    public SomeBean(String field1, String field2, String field3) {  
        super();  
        this.field1 = field1;  
        this.field2 = field2;  
        this.field3 = field3;  
    }
    ...
}
```
`@JsonIgnore`어노테이션을 사용해서 해당 필드가 응답에 포함되지 않도록 할 수 있다.

``` java
@JsonIgnoreProperties("field1")  
public class User {  
    private Integer id;  
    @Size(min = 2, message = "Name should have atleast 2 characters")  
    @JsonProperty("user_name")  
    private String name;  
    @Past(message = "Birth Date should be in the past")  
    @JsonProperty("birth_date")  
    private LocalDate birthDate;
    ...
}
```
@JsonIgnoreProperties({"field1", "field2"})
`@JsonIgnoreProperties`를 사용해서 특정 필드를 지정하는 방법도 가능하다.


### 동적 필터링 (Dynamic Filtering)
``` java
@GetMapping("/filtering")  
public MappingJacksonValue filtering() {  
    SomeBean someBean = new SomeBean("value1", "value2", "value3");  
  
    MappingJacksonValue mappingJacksonValue = new MappingJacksonValue(someBean);  
    SimpleBeanPropertyFilter filter = SimpleBeanPropertyFilter.filterOutAllExcept("field1", "field2");  
    FilterProvider filters = new SimpleFilterProvider().addFilter("SomeBeanFilter", filter);  
    mappingJacksonValue.setFilters(filters);  
  
    return mappingJacksonValue;  
}
```

``` java
@JsonFilter("SomeBeanFilter")  
public class SomeBean {  
    private String field1;  
    private String field2;  
    private String field3;
    ...
}
```
`@JsonFilter()`를 통해 Filter명을 지정해준다.