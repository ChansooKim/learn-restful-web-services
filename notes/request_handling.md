# 요청이 핸들링되는 원리
***
Request -> Dispatcher Sevlet -> Controller
** Spring MVC에서 모든 요청은 Dispatcher Servlet 이 처리한다.
-> Front Controller Pattern
`Dispatcher Servlet`: 요청이 가장 먼저 도달하는 곳
(사용자의 URL에 관계없이 -> 디스패처 서블릿은 루트 URL [/]에 매핑되기 때문)

1. Request(요청)을 보낸다.
2. Dispatcher Servlet이 요청을 받는다.
3. Dispatcher Servlet이 URL을 확인하고 알맞은 컨트롤러 메서드에 매핑한다.

** Dispatcher Servlet은 `Auto Configuration`에 의해 설정된다.

- JSON 형식으로 데이터가 반환되는 이유
  @ResponseBody + JacksonHttpMessageConverters
* @RestController = @Controller + @ResponseBody
  -> Auto Configuration(`JacksonHttpMessageConvertersConfiguration.class`)
  SpringBoot에 의해 자동으로 설정된다.

- 오류 매핑(/error)
  -> Auto Configuration(`ErrorMvcAutoConfiguration.class`)

> 위에서 사용하는 모든 의존성이 Spring-Boot-Starter-Web에 들어있다.

