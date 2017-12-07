# VPC 링크에 파라미터 넘기기
API Gateway에서 분명 파라미터를 넘겼는데 vpc 내의 인스턴스에서는 못 받는 사건이 발생...  
알고 보니 API의 Method Request에 추가한 파라미터들을 Integration Request(VPC 링크 단)에도 토스를 해줘야하는 거였다.  
다만 단순하게 파라미터 이름만 넘기는 게 아니라 Mapped from 이란 필드에 값을 추가해줘야한다.  
`ethod.request.{"path" | "querystring" | "header"}.{param_name}` 이런 형태가 기본 포맷인데  
예를 들면 method.request.querystring.myparam이 될 수 있는 거다.  
그러면 리퀘스트의 쿼리스트링에 myparam이란 파라미터가 매핑되는 것이다.  
path는 path variable, header는 리퀘스트 헤더를 뜻하는 것 같다.  
파라미터 조차 유동적으로 다루기 위한 전략(?) 같다.  
 