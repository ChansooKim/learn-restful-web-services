# 일대다 관계 매핑
***
``` java
@Entity  
public class Post {  
    @Id  
    @GeneratedValue
    private Integer id;  
    private String description;  
    
    @ManyToOne  
    private User user;
```

``` java
@Entity(name = "user_details")  
public class User {  
    @Id  
    @GeneratedValue
    private Integer id;  
    private String name;
    private LocalDate birthDate;  
  
    @OneToMany(mappedBy = "user")  
    private List<Post> posts;
```

`@ManyToOne`의 fetch 속성은 관계가 지연 로딩되는지 또는 즉시 로딩되는지를 결정한다.
-> 동일한 쿼리에서 Post와 User의 세부 정보를 검색하려고 한다면, EAGER Fetch를 요청한다. Post의 세부 정보와 함께 가져오도록 요청하면 User 세부 정보도 같이 가져오게 된다. 다대일 관계에서 `기본값`이다.
Lazy Fetch
`@ManyToOne(fetch = FetchType.LAZY)`