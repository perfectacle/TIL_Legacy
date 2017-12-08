---
title: VPC Link
---

# VPC Link
API Gateway에서 쓰는 기술인 듯...  
VPC(private) 자원에 접근하기 위한 링크같다.  
API Gateway(문지기)는 public이고 그 문지기가 private 자원에 접근하고자 하는데  
vpc 자원과 같은 vpc 내에 속하지 못하니 그걸 링크 해주는 애를 통해서 연결해야하는데 그걸 vpc link가 지원해준다.  
어떤 이윤지는 잘 모르겠으나 NLB에서만 연결이 가능하다.  
아마 네트워크 계층과 뭔가 관련이 있을 듯...