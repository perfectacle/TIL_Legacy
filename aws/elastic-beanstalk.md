# Elastic Beanstalk
기본적으로 EB는 오토스케일링 + CD(Continuous Delivery, 무중단 배포) + 헬스 체크 + ELB를 통으로 묶어놓은 아주 효자 서비스이다.  
하지만 VPC 잘못 설정하고 로드밸런스 타입 잘못 설정하고 하면 Environment를 재생성해야한다는 제약이 존재한다...  
또한 무중단 배포 기법에 따라서 배포 시간이 상당히 길어질 수도 있다.

## NLB 물리기
디폴트 로드밸런서는 클래식 로드밸런서이고, 로드밸런서의 타입은 변경이 안되니  
최초 배포(environment 생성)시에 이미 NLB로 만들어줘야한다.  
콘솔로 만들 때는 .ebextensions 폴더 아래 아래와 같은 옵션을 추가해줘야한다.  
프로젝트 루트 폴더에 .ebextensions 폴더 만들어서 그 아래 *.config 파일 만들어주면 됨.
```bash
option_settings:
  aws:elasticbeanstalk:environment:
    LoadBalancerType: network
  aws:elasticbeanstalk:environment:process:default:
    DeregistrationDelay: '20'
    HealthCheckInterval: '10'
    HealthyThresholdCount: '5'
    UnhealthyThresholdCount: '5'
    Port: '80'
    Protocol: TCP
```
대충 보면 뭐 감이 올라나...  


## 커스텀 로그 추가하기
ELB, EC2 모두 private하면 접근할 방법이 없으니 로그를 보기가 까다롭다.  
로그 다운로드를 지원하지만 eb에서 기본적으로 제공하는 로그만 주기 때문에 커스텀 로그는 같이 안 받아진다.  
프로젝트 루트 폴더에 .ebextensions 폴더 만들어서 그 아래 *.config 파일 만들어주면 됨. 
```bash
files:
  "/opt/elasticbeanstalk/tasks/bundlelogs.d/applogs.conf" :
    mode: "000755"
    owner: root
    group: root
    content: |
      /var/log/**/*.log
```
저 /var 머시기 경로에 톰캣 서버/액세스 로그 찍히게 해놨음.  

## 자바 플랫폼 vs 톰캣
스프링 부트 같은 경우에는 임베디드 톰캣을 써서 jar 파일로 빌드하고 배포해서 자바 플랫폼을 썼는데  
자바 플랫폼은 nginx가 디폴트이다.  
하지만 톰캣 플랫폼은 [apache가 디폴트](http://docs.aws.amazon.com/ko_kr/elasticbeanstalk/latest/dg/java-tomcat-platform.html#java-tomcat-proxy)이고,
nginx로 설정할 수도 있다.  

## 참조 링크
* [.ebextensions/network-load-balancer.config 예제](http://docs.aws.amazon.com/ko_kr/elasticbeanstalk/latest/dg/environments-cfg-nlb.html#network-load-balancer.config)    
* [AWS Elastic Beanstalk Tomcat 플랫폼 사용](http://docs.aws.amazon.com/ko_kr/elasticbeanstalk/latest/dg/java-tomcat-platform.html)  
* [AWS Elastic Beanstalk Java SE 플랫폼 사용](http://docs.aws.amazon.com/ko_kr/elasticbeanstalk/latest/dg/java-se-platform.html)  
* [Elastic Beanstalk 환경의 Amazon EC2 인스턴스의 로그 보기](http://docs.aws.amazon.com/ko_kr/elasticbeanstalk/latest/dg/using-features.logging.html)