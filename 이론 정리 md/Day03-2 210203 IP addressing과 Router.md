## IP addressing

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

## Router

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

**3) 기타 접속 방식**
	AUX포트, NMS(네트워크 관리 시스템) Router에 접속해서 설정할 수도 있다
	TDTP서버를 통해 다른 Router에서 만들어놓은 라우터 설정 파일을 라우터로 다운로드 하는 방식이있다.



##### 라우터의 내부 구성

![image-20210204142252016](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20210204142252016.png)

​	**1) RAM**
​		휘발성 메모리
​		IOS가 올라와서 실행되고, 라우팅 테이블과 구성파일(설정 내용)이 올라와서 동작하는 장소
​		그 외에도 ARP cache나 fast switching에 대한 cache 등을 가지고 있다.

​	**2) NVRAM (Non Volatile RAM)**
​			비휘발성 메모리
​			설정파일(설정내용)을 저장한다 (라우팅 테이블은 저장하지 않음)

​	**3) Flash 메모리**
​			비휘발성 메모리
​			주로 ISO 이미지 파일 저장용으로 사용되고 NVRAM보다 메모리용량이 크다(NVRAM은 설정파일만 저장)
​			Router에 새로운 기능이 추가되면 Router 자체를 교환하는 것이 아닌 IOS를 업그레이드를 하면 된다

​	**4) ROM**
​		Router의 가장 기본적인 내용이 저장
​		전원이 들어올 경우 어떤 순서로 Router 자신의 상태를 점검하고 IOS를 어디서 RAM으로 올리는지 등의 내용이 저장 됨 (Bootstrap)
​		복구용 Mini IOS가 저장 되어 있다.

​	**5) 부가 설명**
​		전체적으로 PC와 비슷한 구성을 가진다
​		Router에서 작업은 모두 RAM위에서 동작
​		ROM에는 Router의 기본정보와 mini IOS, NVRAM에는 설정파일, Flash에는 IOS이미지가 저장 된다
​		RAM 과 Flash는 필요에 따라 업그레이드를 할 수 있지만 적정한 메모리를 유지하는 것이 좋다
​		ROM은 특별한 경우가 아닌 이상 교체하는 상황이 거의 없다

##### 라우터의 부팅 과정

1) Power On self test (POST)
	자신이 물리적으로 이상이 있는지 없는지 체크를 하는 과정

2) Load and run bootstrap code
	bootstrap code를 불러오는 과정

3)Find the IOS software
	어디서 IOS 이미지를 가져올건지 정하는 과정

4)Load the IOS software
	찾은 IOS를 불러오는 과정(RAM위에 올려서 동작을 시킨다)

5)Find the configuration
	NVRAM에 있던 설정파일들을 찾는다

6)Load the configuration
	NVRAM에 있던 설정파일을 RAM으로 불러온다

7) RUN
	Router가 작동

##### Router의 Mode

1.ROMMON Mode
	평소에는 사용하지 않음
	라우터 패스워드를 모를 경우와 IOS 이미지 파일에 이상이 생긴 경우 복구를 하기 위한 모드

2.Setup Mode
	NVRAM에 저장된 Router 설정 파일이 없는 경우 자동으로 실행되는 모드

3.User Mode
	사용중인 라우터에 콘솔 혹은 talnet으로 접속하면 처음 보이는 화면

4.Privileged Mode
	라우터의 운영자 모드

5.Global Configuration Mode
	라우터의 설정을 변경하거나 새로 설정할 경우 사용하는 모드

##### 정적 라우팅 프로토콜

​	관리자가 직접 목적지 네트워크의 정보를 입력하는 프로토콜
​	라우터에 광리자가 수동으로 경로를 입력

장점
	cpu가 best path를 찾기 위한 계산을 하지 않기 때문에 라우팅 속도도 빨라지고 메모리도 적게 사용한다
		-> 라우터 성능이 좋아진다

단점
	관리자가 직접 네트워크 경로를 일일이 설정해야 하는 불편함
	입력한 경로에 이상이 생겨도 Packet을 계쏙해거 그 경로로 전송한다
	대규모 네트워크에서는 사용하기 힘듦