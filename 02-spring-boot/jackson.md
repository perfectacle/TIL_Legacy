---
title: Jackson의 readValue, writeValueAsString, 그리고 JsonIgnore
---

# Jackson의 readValue, writeValueAsString, 그리고 @JsonIgnore

여태까지 포스트맨 같은 프로그램을 이용해서 API 호출만 해보고 데이터 포맷만 봤는데...
Java Object <-> JSON 등 매핑 관련 라이브러리인 잭슨을 쓰다보니...

```java
String json = "...";
objectMapper.readValue(json, Object.class)
```

위와 같이 json 문자열 -> 자바 객체(deserialize)로 매핑하려고 할 때 @JsonIgnore 어노테이션이 붙은 애들은 무시하고 매핑되었다...
마찬가지로 아래와 같이 자바 객체 -> json 문자열로 바꾸려고 할 때(serialize)도 마찬가지였다...

```java
objectMapper.writeValueAsString(new Object());
``` 

또한 JSON 문자열에는 각종 getter나 boolean 체크를 위한 is 메소드 등등이 그대로 찍혀서 나오게 되는데...
이걸 다시 디시리얼라이즈(자바 객체로 바꾸는...)하면 알 수 없는 필드라고 나온다...

귀찮아서 JSON으로부터 자바 객체로 바로 매핑해서 테스트 하려고 할 때 이런 필드 하나하나 빼다가 오히려 시간을 많이 날리기도 한다.  
그냥 빌더 하나 만들어서 처리하는 게 오히려 더 빠를 수도 있다...

그리고 이 @JsonIgnore가 붙었을 때 restTemplate으로 통신을 할 때도 마찬가지로 안 나온다.  
어떻게 보면 당연한데 매번 브라우저 관점, API 호출 관점에서만 바라봐서 그렇지  
Serialize/Deserialize 관점으로 바라보는 게 필요할 것 같다.  

반성하자...

