# 네트워크의 전체흐름 살펴보기

## 랜 카드에서의 데이터 전달과 처리

### 네트워크의 구성

- 응용계층 : 애플리케이션에서 사용하는 데이터 송수신
- 전송계충 : 목적지에 데이터를 정확하게 전송
- 네트워크계층: 다른 네트워크에 데이터를 전달
- 데이터링크계층: 랜에서 데이터를 송수신
- 물리계층: 데이터를 전기신호로 변환

### 컴퓨터의 데이터가 전기신호로 변환되는 과정

1. 웹사이트에 접속(응용계층)에서 시작. URL을 입력하면 캡슐화가 시작됨
2. 브라우저는 웹서버에 HTTP 메시지를 보낸다
3. 데이터가 전송계층에 전달되고 TCP 헤더가 붙음
4. TCP헤더에는 출발지 포트번호, 도착지 포트번호가 있음
5. 네트워크계층에 전달되는데 IP헤더가 붙음
6. IP헤더에는 출발지, 도착지의 IP주소가 붙음
7. 데이터링크계층에 붙어 이더넷 헤더가 붙음
8. 물리계층에서 전기신호로 변환됨 (랜 카드)

### 웹 서버에서의 데이터 전달과 처리

1. 데이터기 전기신호로 웹 서버에 도착하면 데이터링크계층에서 목적지 MAC주소와 자신의 MAC주소가 같은지 비교한다

2. 같으면 이더넷 헤더와 트레일러를 분리하고 네트워크 계층에 전달한다

3. 네트워크 계층에서는 목적지 IP주소와 웹서버의 IP주소가 같은지 확인한다. 같으면 분리하고 전송계층에 전달한다
4. 전송계층에서는 목적지 포트번호를 확인하여 어떤 어플리케이션이 전달해야하는 지 판단하고 TCP헤더를 분리하여 응용계층에 전달한다
