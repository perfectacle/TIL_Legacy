# Today I Learned
야근에 찌들어 공부 안 하는 내 자신을 바라보며 위기감을 느끼고, 작년 스터디 할 때의 열정을 불살라 보고자 하루에 뭐라도 끄적여 보자는 강한 의지를 보여주고자 하는 프로젝트

## 각오
1. 천재지변이 있거나 가정사, 개인사가 있지 않는 이상은 무조건 1일 n커밋을 원칙으로 한다.  
n은 1 이상의 수를 뜻한다.  
2. 별 시덥잖은 거라도 뭐든지 그 날 하루 배웠던 거는 무조건 올리자, 굳이 거창한 내용일 필요가 없다.  
괜히 거창하게 정리하려고 했다가 시간만 더 들고, 나만 보고 이해한다는 용도로 정리해서 효율성을 극대화 시키자.  
3. IT 관련 된 거면 뭐든지 정리한다, 별 시덥잖은 거라도 무조건...  
혹시 나중에 참고할지 모르니 그냥 한 줄 추가하는 정도로라도 추가하자.  
4. 생각 나면 그 때 그 때 업데이트...

## 커밋 로그
1. 2017년  
    1. 12월  
        1. 1일  
            * 리드미 작성  
        2. 2일 - 작심 1일도 못감, 나태함의 정석을 보여줌.  
        3. 3일  
            * [java - reifiable type](/01-java/reifiable-type.md)  
            * [java - 어노테이션](/01-java/annotation.md)  
            * [java - 클래스 객체](/01-java/class-object.md)  
            * [etc. - gitbook 설정](/06-etc/gitbook-config.md)  
            * [etc. - 맥 OS에서 백틱(`)입력하기](/06-etc/mac-os-typing-backtick.md)  
            * [IDE - 인텔리제이에서 빈 패키지 보이기](/05_-ide/intellij-show-empty-package/README.md)  
        4. 4일 - 야근을 하느라 실질상 5일에 커밋
            * [Spring Boot - @Transactional 어노테이션 고찰](/02-spring-boot/transactional-commit.md)
            * [java - forEach vs for](/01-java/for-each-vs-for.md)
        5. 5일 - 야근 하느라 뭐 정리할 시간도 없고 기억 했던 거도 까먹...  
            * [AWS - API 게이트웨이](/04-aws/api-gateway.md)  
            * [network - IP 주소](/03-network/ip-address.md)  
        6. 6일 - 집에 일찍 가고 싶었으나... api 게이트웨이 + 빈스톡 + route 53 + certificate manager 등등 설정할 게 넘나 많아서 야근을... 흑흑...  
            * [AWS - Route53](/04-aws/route-53.md)  
            * [AWS - Elastic Load Balancer](/04-aws/elastic-load-balancer.md)
            * [AWS - VPC Link](/04-aws/vpc-link.md)
            * [AWS - Elastic Beanstalk](/04-aws/elastic-beanstalk.md)  
        7. 7일 - 남의 말을 새겨듣자... 테스트 포인트나 벨리데이션 포인트를 놓치는 경우가 많다 ㅠㅠㅠ...  
        또한 나는 미션 중심(How to)만 찾고, 원리를 찾아서 이해할 생각을 크게 하지 못한다...  
        그리고 레거시를 두려워하고, 이슈 포인트를 잘 캐치해내서 이슈 제기 및 문제 해결을 위해 공유해야하는 자세를 가져야겠다!  
            * [AWS - VPC 링크에 파라미터 넘기기](/04-aws/vpc-link-parameter.md)  
            * [etc - Character Separated Value](/06-etc/character-separated-value.md)  
            * [이것 저것 짜치는 것들...](/06-etc/20171207.md)  
        8. 8일 - 한 주가 끝났다, TIL을 해보니 내가 모르는 게 너무 많다... 주말동안 정리가 가능할까 ㅠㅠ  
            * [java - 상속은 구리다?](/01-java/is-extend-bad.md)  
            * [java - 맵의 참조 관계](/01-java/map-reference.md)  
            * [java - 상속 패턴](/01-java/extend-pattern.md)  
            * [Programming - 함수형 패러다임의 예](/00-programming/functional-paradigm-example.md)
        9. 9일 - 역시 사람은 변하지 않는다. 하루종일 퍼자기만 함 ㅠㅠ  
        10. 10일 - 정체성에 혼란을 느끼고 프론트 공부만 한 것 같다 ㅠㅠ
            * [Typescript + TSLint + Mocha + Chai + ts-node + nyc로 모던한 프론트 엔드 테스트 환경 구축하기](https://blog.perfectacle.com/2017/12/10/ts-node-mocha-chai/)  
            * [rollup.js를 통해 모듈 번들링하기](https://blog.perfectacle.com/2017/12/10/bundle-with-rollup)  
            * [travis-ci와 coveralls를 이용하여 좀 더 안전하게 협업하기](https://blog.perfectacle.com/2017/12/10/travis-ci-coveralls)  
        11. 11일 - 결제 데스 밸리에 도달했다... 트랜잭셔널을 항상 확인하자... 지금 당장 시급한 건 JPA 공부려나? ㅠㅠ
            * [JPA - FetchType](/02a-jpa/fetch-type.md)
        12. 12일 - 즐거운 회식이었다... 덕분에 다음날 커밋...  
            * [Spring Boot - @JsonProperty](/02-spring-boot/json-property.md)  
            * [Git - reset 취소, stash drop 취소하기](/05a-git/revert.md)  
        13. 13일 - 회식의 여파로 넘나 피곤...  
            * [ES Module을 각각의 모듈 번들러는 어떻게 번들링할까?](https://github.com/perfectacle/es-module-webpack-rollup-parcel)  
            * [크롬에서는 시만텍에서 발급한 SSL 인증서를 신뢰하지 않기로 하는 걸까?](/06-etc/chrome-symantec.md)  
        14. 14일 - 피곤... @.@  
            * [스태틱 메서드 모킹 및 메소드 호출할 때 NullPointerException이 발생하는 상황 해걸하기](/01-java/power-mocking.md)
        15. 15일 - 드디어 한 주가 끝났다... 넘나 바쁜 한 주였다.  
            * [JPA와 Lombok이 마냥 좋은 것 만은 아닌 것 같다.](/02-spring-boot/jpa-lombok.md)
2. 2018년
    1. 2월
        1. 9일 - 근 두 달 만에 커밋... 귀찮아서 커밋 로그를 정리하는 건 포기... 최대한 심플하게 가자... 그래야 습관이라도 들 것 같다.
