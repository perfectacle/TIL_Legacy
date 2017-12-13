---
title: 크롬에서는 시만텍에서 발급한 SSL 인증서를 신뢰하지 않기로 하는 걸까?
---

# 크롬에서는 시만텍에서 발급한 SSL 인증서를 신뢰하지 않기로 하는 걸까?
[내 블로그]()를 들어가서 콘솔탭을 보면 아래와 같은 warnings 로그로 아래와 같은 문구가 뜬다.  
>> The SSL certificate used to load resources from https://d33wubrfki0l68.cloudfront.net will be distrusted in M70.
 Once distrusted, users will be prevented from loading these resources.
  See https://g.co/chrome/symantecpkicerts for more information.  
  
참 거슬려서 대충 알아봤더니 [구글, 시만텍 인증서 보안수준 평가절하](http://www.zdnet.co.kr/news/news_view.asp?artice_id=20170326032010)라는 기사를 볼 수 있었다.  
내 블로그는 netlify를 통해 관리되고 있고, netlify에서는 내부적으로 aws의 cloudfront 서비스를 사용해서 cdn을 구현한 것 같은데...  
뭔가 걱정이 된다.  
그렇다고 해서 모든 cloudfront가 시만텍 인증서를 쓰는 건 아닌 것 같아서 다행인데, aws 측에서 어떻게 인증서에 대해 조치를 취해줬으면 좋겠다 ㅠㅠ
netlify가 해줘야하려나...??