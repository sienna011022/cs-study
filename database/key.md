### 데이터베이스 key

-  #### 후보키란 무엇인가요?

  tuple을 유일하게 식별하기 위해 사용되는 속성들의 부분 집합입니다.


-  #### 기본키란 무엇인가요?

  테이블의 모든 행을 고유하게 식별할 수 있는**유일한 식별자(identifier)**입니다.


- #### 슈퍼키란 무엇인가요?

  각 릴레이션(테이블)에서 튜플(행)을 유일하게 식별할 수 있는 속성(열, attribute) 또는 속성의 집합입니다.


- #### 외래키란 무엇인가요?

  `ForeignKey`는 한 테이블의 `PrimaryKey`를 다른 테이블의 특정 속성(열)과 연결하는 역할을 합니다.


- #### 최소성과 유일성에 대해 설명해주세요

  유일성은 하나의 키값으로 튜플을 유일하게 식별할 수 있는 성질

  최소성은 키를 구성하는 속성들 중 가장 최소로 필요한 속성들로만 키를 구성하는 성질


- #### 기본키는 수정이 가능한가요?

  가능은 하지만, 지양해야한다고 알고 있습니다

  연관관계가 있다면 모든 참조된 곳에서 값을 update 해줘야한다.

  인덱스가 정렬 될때 비용이 증가하기 떄문이다.


- #### 사실 MySQL의 경우, 기본키를 설정하지 않아도 테이블이 만들어집니다. 어떻게 이게 가능한 걸까요?

  MYSQL은 항상 테이블 생성시, 기본키를 만들어줍니다


- #### 외래키 값은 NULL이 들어올 수 있나요?

  네 참조하고 있는 릴레이션 과의 관계가 끊어질 수 있기 떄문입니다.


- #### 어떤 칼럼의 정의에 UNIQUE 키워드가 붙는다고 가정해 봅시다. 이 칼럼을 활용한 쿼리의 성능은 그렇지 않은 것과 비교해서 어떻게 다를까요?

  유니크 인덱스는 무결성을 위해 중복 검사가 필요하여 쓰기 성능을 희생해야 한다. 대신 1건만 읽어도 되므로 읽기 성능은 높아진다.
