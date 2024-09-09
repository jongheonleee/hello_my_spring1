# Hello My Spring 🙋🏻‍♂️ 

### 01. 오브젝트와 의존관계

### 02. 테스트


#### 🧑🏻‍🏫 주요 내용 작성
<img src="" width="800" height="500"/>


#### 👉 테스트를 작성하는 것의 의미

<br>

> - 내가 작성한 코드에 대한 확신을 갖게해줌
> - 추후에 테스트 코드를 믿고 리팩토링을 진행할 수 있음
> - 테스트 대상에 대한 학습, 분석용으로 활용할 수 있음

<br>

#### 👉 단위 테스트와 통합 테스트

<br>

> - 단위 테스트 : 테스트 대상이 명확하며 해당 대상에 대해서만 테스트를 진행하는 방식
> - 통합 테스트 : 단위 테스트를 통과한 객체들이 서로 잘 연동되는지 확인하는 방식
> - 단위는 작을수록 좋음, 그 이유는 빠른 피드백이 가능함.
> - 통제할 수 없는 외부 리소스나 객체를 사용하는 것은 단위 테스트가 아님

<br>

#### 👉 테스트의 중요 요인

<br>

> - 테스트에서 중요한 것은? "넓은 범위를 자동으로 테스트를 진행하여 내가 작성한 코드의 대한 확신을 갖고 추후에 리팩토링을 편리하게 하는 것"
> - 넓은 범위 : 꼼꼼하게 테스트를 작성하는 것을 의미함
> - 자동화 : 일일이 수동으로 테스트를 진행하는 것이 아닌 편리하게 실행할 수 있어서 반복적으로 실행하는 것을 의미함
> - 효율성 : 가능한 적은 시간과 노력을 쏟아서 위의 조건을 충족하는 테스트 코드를 작성해야함(훈련이 필요함)

<br>

#### 👉 테스트를 작성할 때 요령

<br>

> - 네거티브 테스트에 대해 먼저 작성
> - 테스트 코드를 작성할 때는 크게 2가지로 나눌 수 있음, '성공'과 '실패'
> - 하지만, 각 요인에 대해서 꼼꼼하게 따져야함
> - 성공 : 수량, 데이터를 많이 늘리기/ 다양한 테스트 시나리오를 작성
> - 실패 : 논리적인 오류/ 예외 상황 세분화
> - given - when - then 방식으로 테스트 코드의 시나리오를 작성한다고 생각하는 것이 좋음

<br>

#### 👉 테스트 코드는 일관성을 보장해야함

<br>

> - 테스트 환경은 독립적으로 구성하는 것이 좋음, 이를 통해서 테스트 결과의 일관성을 보장할 수 있음
> - 테스트 코드의 변경 사항이 없는 한 항상 동일한 결과를 보장해야함

<br>

#### 👉 TDD, 테스트 주도 개발 

<br>

> - TDD는 테스트 주도 개발로 '목적 지향적 프로그래밍'을 도모하는 하나의 개발 방법
> - 이를 통해 좀 더 시간과 자원을 효율적으로 쓰게하려는 의도
> - TDD는 크게 5가지 단계로 나뉘어짐. 각 단계마다 집중해야하는 부분이 다름, 1~4번는 '빠르게 구현'하는 부분에 초점을 두고, 5번은 '깔끔한 코드, OOP 코드'를 만드는데에 초점을 둠 
> - (1) 기능 목록 분석 및 정리, 이를 하나의 기능 목록 리스트로 정리
> - (2) 테스트 코드 작성
> - (3) 테스트 코드 실행 및 실패 테스트 파악, 이를 통과하게 만듦(구현, 수정)
> - (4) (1) ~ (3)을 반복하며 구현
> - (5) 리팩토링

<br>

#### 👉 학습 테스트

<br>

> - 자신이 사용할 API나 프레임워크, 아니면 객체 등등을 직접 테스트해 보면서 익히는 과정
> - 머리로 이해하는 것에는 한계가 있기에 직접 학습 테스트 코드를 작성함으로써 이해도를 높일 수 있음

