## IP addressing

**네트워크 ID 구하는 표 (중요! )**

![Crocus](https://t1.daumcdn.net/cfile/tistory/9926943C5BB8ED8F2F)

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

