# 어노테이션
프로그램의 소스 코드 안에 다른 프로그램을 위한 정보를 미리 약속된 형식으로 포함시킨 것.  

## 메타 어노테이션
어노테이션을 정의하는데 사용되는 **어노테이션의 어노테이션**이다.

## @SuppressWarnings
Suppress: 막다  
경고를 막는 어노테이션이다.  
```java
@SuppressWarnings("unchecked")
public void test() {}

@SuppressWarnings({"unchecked", "deprecation"})
public void test2() {}
```
컴파일 할 때 -Xlint 옵션을 붙였을 때도 오류가 안 뜨게 하는 어노테이션.  
오류가 떠야 정상인데 묵인해야하는 경우가 있을 수 있는데(물론 컴파일/런타임 시에 에러가 없다는 가정 하에...)  
이 어노테이션을 붙이면 됨. 어쩔 수 없을 때만 써야지 오류 보기 싫다고 마구잡이로 쓰면 안 됨.  

## @SafeVargs