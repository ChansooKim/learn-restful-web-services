# Content Negotitaion
***
> 특정한 리소스에는 여러 표현이 가능하다.
>
> JSON 형식이거나 XML 형식이거나
> 동일한 리소스에 여러 표현을 보유하는 것이 가능하다.
>
> 동일한 리소스를 다양한 언어로 노출하고 싶은 경우
> 지원하고자 하는 어떤 언어로도 사용할 수 있다.

Consumer는 자신이 원하는 표현을 알려주고 원하는 형식을 받을 수 있다.
-> 이를 콘텐츠 협상 (`Content Negotiation`) 이라고 한다.

`Accept` 헤더를 통해 `application/xml` 또는 `application/json` 를
`Accept-Language` 헤더를 통해 원하는 언어를 받을 수 있다.

``` xml
<dependency>  
    <groupId>com.fasterxml.jackson.dataformat</groupId>  
    <artifactId>jackson-dataformat-xml</artifactId>  
</dependency>
```
의존성을 추가하고

요청 시 헤더에 `Accept: application/xml`을 요청하면
json 대신 xml로 바로 응답을 받아볼 수 있다.
``` xml
<List>  
    <item>  
        <id>1</id>  
        <name>Adam</name>  
        <birthDate>1995-03-06</birthDate>  
    </item>  
    <item>  
        <id>2</id>  
        <name>Eve</name>  
        <birthDate>2000-03-06</birthDate>  
    </item>  
    <item>  
        <id>3</id>  
        <name>Jim</name>  
        <birthDate>2005-03-06</birthDate>  
    </item>  
</List>
```

