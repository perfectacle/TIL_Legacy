---
title: 스태틱 메서드 모킹 및 메소드 호출할 때 NullPointerException이 발생하는 상황 해걸하기
---

# 스태틱 메서드 모킹 및 메소드 호출할 때 NullPointerException이 발생하는 상황 해걸하기  
Mockito는 static method나 생성자를 모킹하지 못한다.  
따라서 PowerMockito를 써야한다.  
```groovy
dependencies {
    testCompile group: 'org.powermock', name: 'powermock-module-junit4', version: '1.7.3'
    testCompile group: 'org.powermock', name: 'powermock-api-mockito', version: '1.7.3'
}
```

Mockito와는 조금 사용방법이 다르다.  
아래와 같이 하면 된다.  
```java
@RunWith(PowerMockRunner.class)
@PrepareForTest({PropertyUtils.class}) // 모킹할 클래스 배열로 쭉쭉 넘기면 됨.
public class Test1 {
    @Before
    public void setup() {
        mockStatic(PropertyUtils.class);
        PowerMockito.when(PropertyUtils.getProperty(any())).thenReturn(any());
    }
}
```

하지만 아래와 같이 파워모키토로 모킹하고 나서 모킹을 하게 되면 오류가 난다.

```java
@RunWith(PowerMockRunner.class)
@PrepareForTest({PropertyUtils.class}) // 모킹할 클래스 배열로 쭉쭉 넘기면 됨.
public class Test1 {
    @Before
    public void setup() {
        DealRepository dealRepository = mock(DealRepository.class);
        mockStatic(PropertyUtils.class);
        when(dealRepository.findOne(any())).thenReturn(new Deal());
        PowerMockito.when(PropertyUtils.getProperty(any())).thenReturn(any());
        // 이 위치에 있게 되면 org.mockito.exceptions.misusing.InvalidUseOfMatchersException 오류 발생함.
        // when(dealRepository.findOne(any())).thenReturn(new Deal());
    }
}
```

또한 primitive(ex) int) 타입에 any()를 쓰면 nullPointerException이 발생하니 이럴 때는 anyInt()를 써야한다...