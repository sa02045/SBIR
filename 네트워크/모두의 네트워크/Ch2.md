# 네트워크의 기본 규칙

## 1. 프로토콜이란?

- 네트워크에서 통신하기 위해 필요한 `규칙`
- 편지를 보낼 때 집 -> 우체국 -> 집 과정을 거치면서 여러 규칙을 지켜야하는 것 처럼, 네트워크도 컴퓨터 -> 컴퓨터가 연결되기 위해 여러 규칙이 필요하다

## 2. OSI 모델이란?

- 케이블을 연결하는 커넥터의 규격이 다를 수 있다. 이러한 일을 방지하기 위해 `표준모델` `규격`을 정해야한다

- `ISO` 국제표준화기구에서 `OSI 모델`이라는 표준규격을 제정한다

| 데이터의 송수신을 7개의 계층(레이어)으로 표현한 모델

### `응표세전네데물`

1. 응용계층 : 애플리케이션에 대한 서비스를 제공
2. 표현계층 : 문자코드, 압축, 암호화등의 데이터 변환
3. 세션계층 : 세션체결, 통신방식을 결정
4. 전송계층 : 신뢰할 수 있는 통신을 구현
5. 네트워크계층 : 다른 네트워크와 통신하기 위해 논리적인 주소를 결정
6. 데이터링크계층 : 네트워크 기기간의 데이터 전송과 물리적인 주소를 결정
7. 물리계층 : 물리적인 연결과 전기신호를 변환 및 제어

- 송신 측 : 상위 -> 하위 -> 데이터 -> 하위 -> 상위 : 수신 측
- 각 계층은 `독립적`이기 때문에 다른 계층에 영향을 받지 않음

## 3. TCP/IP 모델이란?

| 응용,전송,인터넷,네트워크 4계층으로 이루어짐

1. 응용계층
2. 전송계층
3. 인터넷계층
4. 네트워크 접속계층

- 응용계층이 OSI모델의 응,표,세 계층이 합쳐짐
- 인터넷 계층 = 네트워크 계층
- 네트워크 접속 계층= 데이터링크+물리
- 현재 인터넷은 TCP/IP모델로 이루어짐

## 4. 캡슐화와 역캡슐화란?

- 데이터를 송수신할 때는 캡슐화와 역캡슐화가 이루어진다

- 데이터를 보낼 때 데이터의 앞 부분에 전송하는데 필요한 정보를 붙여서 다음 계층으로 보내야한다.
- 이 정보를 `헤더` 라고한다
- 헤더에는 데이터를 받을 상대방의 정보도 포함된다

- 데이터를 보낼 때 헤더를 하나씩 붙여나가는 것을 `캡슐화` 라고 한다

- 데이터를 받는 쪽에서 헤더를 하나씩 제거하는 것을 `역캡슐화` 라고 한다

### 전체 흐름

1. 응용 계층에서 웹 사이트에 접속하기 위한 요청 데이터가 만들어진다
2. 요청 데이터는 전송계층에 전달 되는데, 신뢰할 수 있는 통신이 이루어지도록 `헤더`를 데이터에 붙인다

3. 네트워크 계층에서도 도 다른 `헤더`를 붙이고, 데이터링크 계층에서도 `헤더`와 `트레일러`를 붙인다

- 트레일러란 데이터를 전달할 때 데이터의 마지막에 추가하는 정보이다

4. 데이터링크 계층에서 만들어진 데이터는 최종적으로 `전기신호`로 변환되어 수신측에 도착한다

- 이렇게 필요한 데이터를 추가해가는 것을 `캡슐화`라고 한다

5. 반대로 받는 측에서 `헤더`를 제거해 나가면서 데이터를 상위계층으로 보내는 것을 `역캡슐화`라고 한다

### VPN

| Virtual Private Network(가상 사설망)
가상 통신 터널을 만들어 연결하여 통신하는 것

1. 인터넷 VPN

- 거점 접속과 원격접속 연결이 있다
- 거점 접속은 `IPsec`이라는 암호 기술 프로토콜을 사용하여 접속한다
- 원격 접속 연결은 외부에서 사용하는 컴퓨터와 사내 네트워크를 연결하기 때문에 암호화된 통신로를 만든다

2. IP-VPN

- MPLS라는 기술을 사용하여 인터넷 망이 아닌 통신 사업자 전용 폐쇄망을 사용한다

- 폐쇄망이기 떄문에 암호화 기능이 필요하지 않다
