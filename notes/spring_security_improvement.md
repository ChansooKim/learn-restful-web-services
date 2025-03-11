# Spring Security 인증 설정 개선
***
모든 요청에 대해 인증을 하고, 인증이 되지 않은 요청에는 인증을 위한 로그인 페이지를 띄우도록 한다.

``` java
@Configuration  
public class SpringSecurityConfiguration {  
    @Bean  
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {  
    
        // 1) All requests should be authenticated  
        http.authorizeHttpRequests(  
                auth -> auth.anyRequest().authenticated()  
        );  
        // 2) If a request is not authenticated, a web page is shown  
        http.httpBasic(withDefaults());  
        // 3) CSRF -> POST, PUT  
        http.csrf().disable();  
        
        return http.build();  
    }  
}
```