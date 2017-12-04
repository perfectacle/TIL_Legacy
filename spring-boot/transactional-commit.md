# @Transactional 어노테이션 고찰
아주 간단한 고찰  
JPA에서 save 메소드를 호출하지도 않았는데 지가 알아서 업데이트를 침.  
알고 봤더니 @Transactional 어노테이션을 타서 그랬음...  
알아서 커밋하는 듯...
`@Transactional(readOnly = true)`을 태워야 자동 커밋을 하지 않는다...  
readOnly를 걸어놓으면 write가 없으니까 오히려 더 빠를 거 같은데 그건 또 아닌 거 같다.  
오늘은 자야하니 이만 하고 아래 링크를 나중에 정독하자.  

## 참조 링크
* [Why do spring/hibernate read-only database transactions run slower than read-write?](https://stackoverflow.com/questions/34797480/why-do-spring-hibernate-read-only-database-transactions-run-slower-than-read-wri)  
* [Transactional saves without calling update method](https://stackoverflow.com/questions/8190926/transactional-saves-without-calling-update-method)