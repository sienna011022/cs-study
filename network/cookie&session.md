### 쿠키와 세션의 차이
- ####  쿠키 동작 방식

  클라이언트가 페이지를 요청하면

  서버는 쿠키를 생성하고 HTTP헤더에 쿠키를 포함시켜 응답합니다

  브라우저가 종료 되어도 쿠키 만료 시간이 있다면 클라이언트는 쿠키를 보관합니다

  이후 요청시 HTTP헤더에 쿠키를 넣어보냅니다

  ex ) 장바구니, 자동로그인시 팝업(일주일간 보지 않기)

- ####  세션 동작 방식

  클라이언트가 서버에 접속시 세션 ID를 발급 받음

  클라이언트느 세션 ID에 대해서 쿠키를 사용해서 저장

  서버에 요청 시, 이 쿠키의 세션 ID를 서버에 전달

  서버는 세션 ID로 세션에 있는 클라이언트의 정보를 가져와서 사용

  클라이언트의 정보를 가지고 요청 처리 후 응답

- ####  왜 HTTP에서 쿠키와 세션이 필요한가요?

  HTTP는 비상태성(Stateless) 프로토콜로 상태 정보를 유지하지 않는다. 연결을 유지하지 않기 때문에 리소스 낭비가 줄어드는 것은 큰 장점이지만 통신할 때마다 매번 연결 설정을 해야 하며, 이전 요청과 현재 요청이 같은 사용자의 요청인지 알 수 없다는 단점이 존재한다

- ####  cookie와 세션의차이(만료시점)

  cookie는 생성시 , expires 속성에 만료 시점을 정의하여 삭제 될 날짜를 지정할 수 있다

  세션은 클라이언트가 로그아웃을 하거나 일정 시간 동안 응답이 없으면 세션이 만료 되기 때문에 정확한 만료 시점을 알기가 어렵다

- #### cookie와 세션의차이(저장위치)

  쿠키는 클라이언트의 브라우저 메모리나 하드디스크에 저장되지만 세션은 서버의 메모리에 저장된다

- #### cookie와 세션의차이(리소스)

  쿠키는 클라이언트 메모리에 저장이 되어 서버의 리소스를 사용하지 않는다.
  세션은 서버에 저장이 되어 세션 생성시 마다 리소스를 차지한다

- #### cookie와 세션의차이(용량제한)

  클라이언트도 모르게 사이트 마다 쿠키가 생성될 수 있기 때문에 도메인당 20개 하나의 쿠키는 4KB로 제한되어있다.
  세션은 서버의 메모리를 사용하기에 제한이 없다

- #### cookie와 세션의차이(보안)

  cookie는 클라이언트 측에 저장되어 보안에 취약, 세션은 서버에 저장되기에 취약 X

- #### 왜 세션말고 쿠키를 사용?

  세션은 서버의 메모리를 사용하기에 메모리를 감당할 수 없음. 적재적소에 맞게 사용 지향

- #### Stateless의 의미를 살펴보면, 세션은 적절하지 않은 인증 방법 아닌가요?

  stateless는 연결이 끊기면, 상태를 유지하지 못한다는 특징인데,세션 또한 연결이 종료되면 서버에 있는 세션정보가 만료 됩니다.

- #### 규모가 커져 서버가 여러 개가 된다면, 세션을 어떻게 관리할 수 있을까요?

  로드밸런서를 이용할 수 있습니다.

  여러대의 서버로 트래픽을 균등하게 분산시켜주는 기술입니다

- #### 로드 밸런서의 세션 관리 방법은 무엇이있나요?

  (1)Sticky Session

  첫 요청을 처리한 서버 즉 세션을 가진 서버에게 매 요청을 보냅니다

  트래픽을 여러대 분산해야하는데, 특정 서버에게만 트래픽을 보내서 세션 관리 서버가 죽으면 세션이 사라짐

  (2) Session Clusteirng

  클러스터링이란?

  여러대의 서버를 하나처럼 운영하는 것을 의미한다.

  새로운 서버를 만들 때마다 데이터를 옮겨서 클러스터링해준다

  (3) Session Server

  서버마다 세션을 따로 두지 않고 세션만 관리하는 별도의 서버를 만듭니다. 세션 서버가 하나라서 단일 장애 지점이 생기긴 하나, Redis 같은 In-memory DB는 메모리에 데이터를 저장하면서 , 다른 서버의 메모리에 실시간으로 복사본이 저장되고 디스크에 저장됩니다.
