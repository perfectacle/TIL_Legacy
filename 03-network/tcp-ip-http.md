---
title: TCP/IP, UDP와 HTTP
---

# TCP/IP와 HTTP
TCP, UDP는 OSI 7 계층에서 4계층인 전송 계층이다.  
HTTP, FTP는 OSI 7 계층에서 7계층인 어플리케이션 계층이다.  

TCP는 연결 지향형이기 때문에 신뢰도가 높다.  
연결을 위해서 3 Way Handshake를 해야하기 때문에 비용이 많이 든다.  

UDP는 비연결 지향형이기 때문에 신뢰도가 낮고, TCP에 비해 비용이 저렴하다. (맞나??)  

HTTP는 필수는 아니지만 대부분 TCP 프로토콜 위에서 돌기 때문에 신뢰도가 높다.  
또한 HTTP는 웹 문서들을 보여주기 위한 프로토콜, 정보 공유를 위해 나온 프로토콜이기 때문에 다수에게 열려있어야한다.  
다수에게 열려있어야 하기 때문에 커넥션 풀을 그만큼 다 들고 있는 것은 매우 큰 비용이다.  
따라서 기본적으로 HTTP 1.0 스펙에서는 응답이 끝나면 커넥션을 종료시켜버린다.  
이 말 뜻은 10개의 요청이 있으면  
1. 10번의 3 Way handshake
2. 10번의 요청
3. 10번의 응답

매우 비효율적으로 작동하는 걸 볼 수 있다.  
따라서 HTTP 1.1 스펙에서는 Keep-alive 라는 것이 등장했다.  
Keep-alive에 정의된 시간 만큼 커넥션 풀을 유지하는 것이다.  
만약 Keep-alive 사이에 10개의 요청이 있으면  
1. 1번의 3 Way handshake  
2. 10번의 요청
3. 10번의 응답

2번과 3번이 좀 걸리긴 하지만(이건 HTTP 2 스펙에서 개선됐다고 알고 있음.)  
적어도 1번의 경우는 어느 정도 해소했다고 볼 수 있다.  
물론 그만큼의 시간동안 서버에서 커넥션을 유지시켜야하므로 서버 쪽의 비용이 좀 더 증가했다고 봐야 할 거 같다.  

그리고 커넥션에 대한 정보?를 세션(어플리케이션 계층의 세션이 아닌 전송 계층(TCP)의 세션?)이라고 부르는 것 같다.  

반면 FTP는 다수에게 열려있는 게 아니라 인증된 유저에게만 열면 되기 때문에 커넥션을 계속해서 물고 있다.  
애초에 커넥션 자체가 HTTP 프로토콜에 비하면 새발의 피 수준이기 때문일 것이다.  
