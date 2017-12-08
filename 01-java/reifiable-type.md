---
title: reifiable type
---

# reifiable type
re(다시) -ify(~화 하다) able(~할 수 있는)  
다시 ~화 할 수 있는 타입 이라는 엉성한 뜻이니 그냥 영어 느낌 그대로 끌고 가야할 것 같다.  
제네릭에서는 컴파일 후에 제거되는 타입들이 있다. 이러한 타입을 non-reifiable type이라고 한다.  
대표적으로 `List<String>`과 같은 것들일 것이다.  
반대로 제네릭 타입인데 컴파일 이후에 제거되지 않는 타입이 reifiable type이다.  

[The Java™ Tutorials: Non-Reifiable Types](https://docs.oracle.com/javase/tutorial/java/generics/nonReifiableVarargsType.html)
을 보면 아래와 같이 설명하고 있다.  
> A reifiable type is a type whose type information is fully available at runtime.
  This includes primitives, non-generic types, raw types, and invocations of unbound wildcards.
  Non-reifiable types are types where information has been removed at compile-time by type erasure — 
  invocations of generic types that are not defined as unbounded wildcards.
  A non-reifiable type does not have all of its information available at runtime.
  Examples of non-reifiable types are List<String> and List<Number>;
  the JVM cannot tell the difference between these types at runtime.
  As shown in Restrictions on Generics, there are certain situations where non-reifiable types cannot be used:
  in an instanceof expression, for example, or as an element in an array.

primitives는 알겠는데 non-generic types, raw types, and invocations of unbound wildcards는 잘 모르겠다.  
아래 링크를 통해 나중에 참고해서 정리하자.  
[Generic - 원천(raw)타입을 사용하지 맙시다. - O! JAVA](http://ojava.tistory.com/27)

## 참조 링크
* [The Java™ Tutorials: Non-Reifiable Types](https://docs.oracle.com/javase/tutorial/java/generics/nonReifiableVarargsType.html)  
* [Generic - 원천(raw)타입을 사용하지 맙시다. - O! JAVA](http://ojava.tistory.com/27)  
