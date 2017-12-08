---
title: 맵의 참조 관계
---

# 맵의 참조 관계
아직도 자바의 참조를 이해하지 못해서 아래 동작을 직접 테스트 코드로 짜서 이해해봤다.  

```java
@Test
public void test() {
    Deal deal = new Deal();
    deal.setId(1L);

    List<Deal> dealList = Lists.newArrayList(deal);

    Map<Long, List<Deal>> collect = dealList.stream().collect(groupingBy(Deal::getId));

    collect.get(1L).get(0).setId(2L);
}
```

맵으로 바꾼다 해도 딥카피가 되는 게 아니라 기존 dealList에도 영향을 미친다.  
주말에 좀 자세하게 파봐야겠다.