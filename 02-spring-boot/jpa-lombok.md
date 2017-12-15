---
title: JPA와 Lombok이 마냥 좋은 것 만은 아닌 것 같다.
---
# JPA와 Lombok이 마냥 좋은 것 만은 아닌 것 같다.
맨 처음에 JPA의 findBy와 페이징과 Lombok의 @Data, @Setter, @Getter의 첫 모습을 보고 홀딱 반했었다.  
하지만 JPA를 써보고 나니 @Transactional의 무서움에 도달했다. (내가 save 때리지 않았는데 알아서 save 때리는 걸 보고...)  
또한 @OneToOne, @OneToMany, @ManyToOne, @ManyToMany 등의 어노테이션에서 내가 원하지 않게 추가로 쿼리가 날아가는 모습이 보이거나  
그 조인한 테이블이 또 @OneToOne 등등을 물고 있으면 계속해서 쿼리를 호출하고 슬로우 쿼리를 유발하는 것 같다.  

Lombok의 경우에는 getter, setter를 어노테이션으로 달다보니 제대로 코드를 추적하지 못하는 사례가 있었던 것 같다.  
아니면 인텔리제이 같은 IDE에서 소스 코드 리팩토링 같은 게 제대로 지원 안 한다거나...  
그냥 @Slf4j 쓰는 용도로만 써야겠다... 