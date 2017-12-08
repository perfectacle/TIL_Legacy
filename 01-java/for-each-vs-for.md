---
title: forEach vs for
---

# forEach vs for
js와 유사한 결과다.  
문법을 잘 몰라서 테스트  

```java
class Test {
    public static void main(String[] args){
        List<Integer> integers = Lists.newArrayList(null, 1);
        integers.forEach(e -> { 
            if(e == null) return;
            System.out.println(e); // 1
        });
        
        for (Integer integer : integers) { 
            if(integer == null) return;
            System.out.println(integer); // 아무것도 안 찍음 
        }
        
        System.out.println(123); // 안 찍음.
    }
}
```

js의 forEach vs for문과 마찬가지로 람다의 forEach는 해당 스코프만 탈출한다.  
하지만 for문은 걍 해당 함수 자체를 종료시켜버림.
아마 별도의 컨텍스트를 가지지 않는 듯...

```java
class Test {
    String txt;
    
    public static void main(String[] args){
        Test test = new Test();
        Test test2 = new Test();
        
        test.txt = "1";
        test.txt = "2";
        
        List<txt> txts = new ArrayList<>();
        txts.add(test);
        txts.add(test2);
        
        txts.stream().filter(e -> e.txt.equals("2").forEach(e -> e.txt = "3");
        txts.forEach(e -> System.out.println(e.txt)); // "1" "3"
    }
}
```

람다 내에서 참조변수를 쓰면 원본 객체의 참조를 건드리는 거니 값이 바뀜!