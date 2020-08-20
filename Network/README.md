# 네트워크

* [OSI 7계층](#OSI-7계층)
* [TCP/IP의 개념](#TCP/IP의-개념)
* [TCP와 UDP](#TCP와-UDP)
* [TCP와 UDP의 헤더 분석](#TCP와-UDP의-헤더-분석)
* [TCP의 3-way-handshake와 4-way-handshake](#TCP의-3-way-handshake와-4-way-handshake)
---

### OSI 7계층
* OSI(Open System Interconnection) 참조 모델이란
    * 다른 시스템 간의 원활한 통신을 위해 ISO에서 제안한 통신 규약
    * 개방형 시스템 간의 데이터 통신 시 필요한 장비 및 처리 방법 등을 7단계로 표준화함

* 물리 계층(Physical Layer)
    * 전송에 필요한 두 장치 간의 실제 접속과 절단 등의 규칙 정의
    * 물리적 전송 매체와 전송 신호 방식 정의
    * 프로토콜 데이터 단위 : Bit
* 데이터 링크 계층(Data Link Layer)
    * **Point to Point** 간 신뢰성 있고 효율적인 정보 전송을 위한 계층
    * **흐름 제어, 프레임의 동기화, 오류 제어, 순서 제어** 기능
    * 프로토콜 데이터 단위 : Frame
* 네트워크 계층(Network Layer)
    * 네트워크 연결을 관리하는 기능과 데이터의 교환 및 중계 기능
    * 노드를 거칠 때마다 경로를 찾아주는 **라우팅**, 트래픽 제어 등을 수행한다.
    * 프로토콜 데이터 단위 : Packet
* 전송 계층(Transport Layer)
    * **End to End**의 사용자들이 신뢰성 있는 데이터를 주고 받을 수 있도록 해, 상위 계층들이 데이터 전달의 유효성이나 효율성을 생각하지 않도록 해준다.
    * 시퀀스 넘버 기반의 오류 제어 방식을 사용한다.
    * 예) TCP, UDP
    * 프로토콜 데이터 단위 : Segment
* 세션 계층(Session Layer)
    * 양 끝단의 응용 프로세스가 통신을 관리하기 위한 방법 제공
    * 송/수신 측 간의 대화 동기를 위해 정보의 수신 상태를 체크
    * TCP/IP 세션을 만들고 없애는 책임을 진다.
    * 프로토콜 데이터 단위 : Message
* 표현 계층(Presentation Layer)
    * 통신에 적당한 형태로 변환
    * 코드 변환, 데이터 암호화/압축, 구문 검색 등
    * 프로토콜 데이터 단위 : Message
* 응용 계층(Application Layer)
    * 사용자가 OSI 환경에 접근할 수 있도록 서비스 제공
    * 응용 프로세스와 직접 관계해 일반적인 응용 서비스를 수행
    * 프로토콜 데이터 단위 : Message


### TCP/IP의 개념
* TCP/IP란
    * 인터넷에 연결된 서로 다른 기종의 컴퓨터들이 데이터를 주고받을 수 있도록 하는 표준 프로토콜
    * 응용계층, 전송 계층, 인터넷 계층, 네트워크 액세스 계층으로 이루어져 있다.
* TCP 프로토콜
    * OSI 7계층의 전송 계층에 해당
    * 신뢰성 있는 연결형 서비스 제공
    * 스트림 전송 기능 제공
* IP 프로토콜
    * OSI 7계층의 네트워크 계층에 해당
    * 데이터그램을 기반으로 하는 비연결형 서비스 제공
    * 주소 지정, 경로 선택 기능 제공


### TCP와 UDP
* 전송 계층에서 사용하는 프로토콜
* TCP(Transmission Control Protocol)
    * 데이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜
    * 수신한 세그먼트에 에러가 발생하면 재전송을 요구해 에러를 복구한다.
    * **양방향(Full Duplex) 연결형와 가상 회선 방식**을 제공한다.
        * 3-way handshaking으로 연결을 설정하고, 4-way handshaking으로 연결을 해제한다.
    * **신뢰성**있는 경로를 확립하고 메세지 전송을 감독한다.
    * **스트림** 단위로 전달
    * 순서 제어, 오류 제어, 흐름 제어, 혼잡 제어를 제공한다.
* UDP(User Datagram Protocol)
    * **데이터그램** 단위로 전달
    * 에러가 발생한 세그먼트는 폐기한다.
    * **비연결형 서비스** 제공
    * **실시간** 전송에 유리하며, 신뢰성보다는 **연속성/속도**가 중요할 때 사용
    * 헤더의 Checksum 필드를 통해 최소한의 오류만 검출한다.


### TCP와 UDP의 헤더 분석
* TCP의 헤더
    * Source Port, Destination Port
    * Sequence Number, Acknowledgment Number
    * Offset, Reserved, Flags, Window size
    * Checksum, Urgent Pointer, Option
* UDP의 헤더
    * Source Port, Destination Port
    * Length, Checksum
    * 에러복구를 위한 필드가 불필요하므로 TCP 헤더보다 간단하다.
### TCP의 3-way-handshake와 4-way-handshake
* 3-way handshake란
    * TCP 통신을 이용해 데이터를 전송하기 위해 네트워크 **연결을 설정**하는 과정
    * TCP/IP 프로토콜을 이용해서 통신을 하는 응용 프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방과 사전에 세션을 수립하는 과정
    * 과정
        * Client가 Server에게 연결 요청 메세지(SYN)을 전송한다.
        * Server가 요청을 수락했으며, Client도 포트를 열어 달라는 메세지를 전송한다.(SYN + ACK)
        * Client가 수락 확인을 보내 연결을 맺는다.(ACK)
* 4-way handshake란
    * TCP **연결을 해제**하는 과정
    * 과정
        * Client가 Server에게 연결을 종료하겠다는 FIN 플래그를 전송한다.
        * Server는 일단 확인 메세지를 보내고 자신의 통신이 끝날 때까지 기다린다.
        * 전송할 데이터가 남아있지 않고, 통신이 끝났으면 연결 종료 요청에 응한다는 의미로 Client에게 FIN 플래그를 전송한다.
        * Client는 확인했다는 메세지(ACK)를 전송한다.

* Reference : [https://asfirstalways.tistory.com/356](#https://asfirstalways.tistory.com/356)
