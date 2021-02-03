### IP addressing

**네트워크 ID 구하는 표 (중요! )**

![image-20210203174818303](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210203174818303.png)

#### IP address

IP address는 **네트워크** 부분과 **호스트 부분**으로 구성
(IP address = Network ID Host ID)
(예 : 교실이름과 학생번호)

- 하나의 네트워크란?
  - 하나의 Broadcast Domain
  - L3 장비 (router)를 거치지 않고 통신이 가능한 영역
    -> 다른 네트워크와 통신하기 위해서는 라우터를 거쳐야 함

이렇게 IP 주소를 **Network 부분**과 **Host 부분**으로 구분해주는 역할을 하는 것이 **Subnet mask**이다

#### Subnet mask

**(1)**

​	IP 주소를 Network 부분과 Host 부분으로 규정

​	IP = Network ID (고정된 bit) + Host ID (고정되지 않은 bit)

​	총 네트워크 범위에서 Network field에 '1'을 할당하고 Host field에 '0'을 할당한 값

**(2) example **

​	IP address : 210.55.1.7
​	& (and 연산) // 8비트 2진수로 변환 후 연산
​	Subnet mask : 255.255.255.0

​	== Network ID : 210.5.1.0
​	== Broadcast : 210.5.1.255

​	-> Host field를 모두 '0'으로 채우면 **Network ID**
​		Host field를 모두 '1'로 채우면 **Broadcast 주소**

**Network ID와 Broadcast 주소는 IP 주소로 사용할 수 없다**

사용 가능한 IP주소 : 210.5.1.1 ~ 210.5.1.254

#### IP Adress Class

IP 주소 범위에 따라 Subnet msk를 default 값으로 정한 것

클래스 범위가 높을 수록 활동 범위가 적음 (활동범위 : A<B<C )

#### subneting

#### VLSM

subneting 된 네트워크를 다시 subneting 하는 것

----

### Router

라우터는 Layer 3 (네트워크 계층) 장비이다
서로 다른 네트워크를 연결하고 Broadcast  Domain을 나눈다.

##### 라우터의 역할

경로결정 : packet이 목적지로 갈 수 있는 경로를 확인하고 어느 경로가 가장 최적경로인지 결정
스위칭 : 결정된 경로대로 packet을 전송해주는 것

routing protocol에 따라 Routing table을 작성한다.

##### 라우터의 종류

단독형 : 일체형으로 이미 모든 인터페이스가 구성 (확장성X)
모듈형 : 사용자의 필요에 따라 인터페이스 모듈을 직접 꽂아서 사용가능 (확장성O)

(단독과 모듈)

![image-20210203173106586](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210203173106586.png)

##### 라우터 interface 종류

1) LAN 구간 interface -->> Ethernet Interface
2) WAN 구간 interface -->> serial Interface
3) 관리용 인터페이스 -->> console Port

![image-20210203172946604](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210203172946604.png)

##### 라우터에 사용되는 cable

1) V.35 -->> WAN 구간에 사용되는 케이블 중 하나
2) UTP ->> LAN 구간에 사용되는 케이블
3) Console cable 장비 관리용 케이블

##### 라우터는

성능, interface의 숫자, 지원하는 기능, 메이커에 따라 가격이 다르다
모듈형에서 interface는 따로 구입해야 한다. 
라우터에서 사용되는 software를 IOS(Internetworking Operating System)라고 한다.
	-> 즉, Router의 운영체제이다.

##### 접속방법

**1) consolcable**
	라우터의 콘솔 포트에 콘솔케이블을 연결하고 나머지 한쪽을 컴퓨터의 serial포트에 연결,
	연결 후 터미널 프로그램을 사용 해 접속

라우터에 PC를 적접 연결해야 하고 console cable이 필요하다는 불편함이 있음

가장 일반적이고 편리한 벙법이며 **안정적인** 접근이 장점

**2) Talnet**
	대부분 라우터를 관리할 때 가장 많이 사용하는 방법
	라우터의 IP 주소를 알고 네트워크에 접속만 되어 있다면 장소와 상관없이 접속이 가능하다

단점 : 라우터를 처음 구성 할 때에는 IP 주소 설정이 안 되어있어서 Talnet 사용이 불가하고 네트워크 연결이 끊어질 경우 접속이 불가하다

Talnet을 **Virtual Terminal** (가상터미널)이라고 한다.
