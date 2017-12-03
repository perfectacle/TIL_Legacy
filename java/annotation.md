---
disqus: false
---

# 어노테이션
프로그램의 소스 코드 안에 다른 프로그램을 위한 정보를 미리 약속된 형식으로 포함시킨 것.  

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

## @SafeVarargs
Varargs, Variable Arguments, 가변인자를 뜻한다.  
메서드에 선언 된 가변인자가 non-reifiable type일 경우,
메소드 선언과 호출부에서 **unchecked** 경고가 발생한다.  
문제가 없는 코드라면 이 어노테이션을 사용해야한다.  
이 어노테이션은 생성자, static, final 키워드가 붙은 곳에서만 사용할 수 있는데,
오버라이딩 될 수 없다는 걸 뜻한다.  
메소드 선언부에 이 어노테이션을 붙여놓으면 호출부에서 붙일 필요가 없다.  
하지만 @SuppressWarnings 어노테이션으로 unchecked 경고를 방지하려면 선언부/호출부 두 곳에 다 붙여줘야한다.  
그리고 @SafeVarargs는 unchecked 경고는 막아주지만 varargs 경고는 막아주지 못하기 때문에  
메소드를 선언할 때 습관적으로 @SafeVarargs와 @SuppressWarnings("varargs")를 동시에 쓰는 게 좋다.  
그냥 컴파일 해보면 @SuppressWarnings("varargs")를 쓰지 않아도 경고가 출력되지 않지만 -Xlint 옵션을 넣었을 때는 경고가 보인다.  

## 메타 어노테이션
어노테이션을 정의하는데 사용되는 **어노테이션의 어노테이션**이다.  
어노테이션의 적용 대상(target)나 유지기간(retention) 등이 있다.  

### @Target
```java
@Target({FIELD, TYPE})
```
target 어노테이션에 들어갈 수 있는 것들은 java.lang.annotation.ElementType에 enum 클래스로 있다.

### @Retention
어노테이션의 유지기간을 지정하는데 사용된다.  
java.lang.annotation.RetentionPolicy enum에 정의돼있다.  
* SOURCE: 소스파일에만 존재, 클래스 파일에는 존재하지 않음.  
컴파일러는 직접 작성할 것이 아니면 쓸 일이 없다고 함.  
* CLASS: 클래스 파일에는 존재하지만 JVM에 로딩될 때 어노테이션 정보가 무시됨.  
따라서 실행시 어노테이션에 대한 정보를 얻을 수 없으므로 잘 사용하지 않음.  
* RUNTIME: 클래스 파일에도 존재하고 reflection을 통해 클래스 파일에 저장된 어노테이션 정보를 얻을 수 있음.  
제일 많이 사용된다고 보면 됨.  

### @Documented
어노테이션에 대한 정보가 javadoc으로 작성한 문서에 포함되도록 함.  

### @Inherited
어노테이션이 자손 클래스에 상속되도록 함.  
조상 클래스가 이 어노테이션이 붙어 있으면 자손 클래스도 이 어노테이션이 붙은 것으로 인식 됨.  

## 어노테이션의 형태
```java
@interface anno {
    type name() default value;
}
```

어노테이션 내에 선언된 메소드(위 예제에서는 name)를 어노테이션의 요소(element)라고 한다.  
어노테이션에는 상수 정의가 가능하지만 디폴트 메서드는 불가능하다.  
어노테이션의 요소에는 반환 타입이 무조건 있어야하며 매개변수가 없는 추상메서드 형태가 된다.  
기본적으로 interface 처럼 구현하지 않아도 되지만, 어노테이션을 적용할 때는 요소들의 값을 전부 지정해줘야한다.  
위처럼 default 값을 넣어주면 굳이 값을 지정하지 않아도 된다.  

또한 위처럼 **어노테이션의 요소가 하나 뿐이고, 요소명이 value일 때** 요소명은 생략이 가능한 채로 사용이 가능하다.  
```java
@anno("asdf")
// @anno(value = "asdf") 둘 다 똑같음.
public class A {}
```

값이 배열이라면 아래와 같이 해야한다.  
```java
@anno({"asdf", "qwer"})
@anno("asdf") // 값이 하나일 때는 괄호 생략 가능
@anno({}) // 값이 없을 때는 괄호만 입력하면 됨.
```

어노테이션 요소를 배열로 선언할 때도 아래와 같다.  
```java
@interface anno {
    int[] count();
    int[] count2() default {1, 2};
    int[] count3() default 1; // 기본값 하나일 때
}
```

## java.lang.annotation.Annotation
모든 어노테이션의 조상이다.  
하지만 어노테이션의 모습은 일반적인 인터페이스로 정의돼있고, 다른 어노테이션들이 명시적으로 extends 키워드를 써서 상속받는 걸 허용하지 않는다.  
Annotation 인터페이스는 equals, hashCode, toString 같은 메서드가 정의돼있어서 다른 어노테이션에서 해당 메소드를 쓸 수 있다.  

## 마커 어노테이션
값을 지정할 필요가 없는 경우에 어노테이션 요소를 하나도 정의하지 않아도 된다.  
이런 어노테이션들을 마커 어노테이션이라고 한다.  

## 어노테이션 요소 규칙
* 상수 OK  
* 타입은 기본형, String, enum, 어노테이션, Class만 허용  
* 매개변수 선언 불가  
* 예외 선언 불가  
* 요소를 타입 매개변수로 정의할 수 없다.  
```java
@interface TestAnno {
    int id = 100; // 상수 OK
    String major(int a); // 매개변수 X
    String minor() throws Exception; // 예외 발생 X
    ArrayList<T> hi; // 타입 매개변수 사용 불가
}
```

## 어노테이션 요소 사용하기
어노테이션 요소를 선언만 해서 어따가 써먹는지 모를 것이다.  
클래스 객체를 사용해서 어노테이션 정보를 불러와서 사용이 가능하다.  
```java
@interface TestAnno {
    int id();
}
@TestAnno(id = 12)
public class ABC {
    public static void main(String[] args){
      Class<ABC> abcClass = ABC.class;
      TestAnno anno =  (TestAnno)abcClass.getAnnotation(TestAnno.class);
      System.out.printf(anno.id()); // 12
    }
}
```