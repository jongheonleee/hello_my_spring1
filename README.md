# Hello My Spring 🙋🏻‍♂️ 

<br>

## 📌 01. 오브젝트와 의존관계

#### 🧑🏻‍🏫 주요 내용 작성 - 오브젝트

<img src="/images/스프링오브젝트.jpeg" width="800" height="500"/>


#### 🧑🏻‍🏫 주요 내용 작성 - 스프링 컨테이너

<img src="/images/스프링컨테이너.jpeg" width="800" height="500"/>



#### 👉 OOP와 오브젝트 

> - 오브젝트(객체)는 모든 애플리케이션의 기본 구성요소를 의미함
> - 현재는 OOP 프로그래밍과 설계과 각광받고 있음. 이는 현실 세계의 급속도로 변환하는 사용자, 서비스 요구사항에 효율적으로 대처하기 위함입.
> - OOP로 구현된 애플리케이션은 '각 오브젝트 간의 특정 역할이 있고 여러 오브젝트와 관계를 맺음으로써 협력하여 하나의 애플리케이션을 운영'
> - 이렇게 애플리케이션을 구현하는 목적은 '변경에 유리하도록 유연하면서 견고하게 설계하기 위함임, 결국에는 하나의 코드를 각 관심사 별로 분류하여 오브젝트로 정의하고 애플리케이션 운영시점에 여러 오브젝트들 간의 관계를 맺고 하나의 관심에 여러 오브젝트를 바꿔가면서 여러 종류의 코드를 만들어 나가는 것'
> - 스프링에서 주요 관심 사항 중 하나는 애플리케이션의 기본 구성요소인 “오브젝트”입니다. 즉, 오브젝트를 어떻게 생성하고 관리하며 어떻게 의존관계를 설정해야 하는지가 중요한 사항

<br>

#### 👉 디자인 패턴, SOLID 원칙

> - 위의 패턴과 원칙 모두 'OOP를 충족시키기 위해 등장한 기법이나 원칙임'
> - 디자인 패턴의 경우, 애플리케이션의 오브젝트들을 어떻게 합성하며 구성해나가는지에 대한 구체적인 방법을 의미함 
> - SOLID 원칙의 경우, '변경에 유리하도록 설계하기 위한 원칙을 의미함'
> - (1) SRP : 단일 책임 원칙, 하나의 액터에 대해 책임져야함. 즉, 변경 포인트를 한가지로 선정
> - (2) OCP : 개방-폐쇄 원칙, 확장에는 열려있고 변경에는 닫혀있음 
> - (3) LSP : 리스코프 치환 원칙, 상위 클래스 객체 대신 하위 클래스 객체를 사용해도 프로그램의 동작에 문제가 없어야함(다형성) 
> - (4) ISP : 인터페이스 분리 원칙, 하나의 큰 인터페이스봐 여러 개의 작은 인터페이스를 사용하는 것이 좋음.(사용자마다 해당 오브젝트를 어떤 관점으로 바라볼지를 정하는 것)
> - (5) DIP : 의존 역전 원칙, 상위 모듈은 하위 모듈에 의존하지 않아야함

<br>

#### 👉 초난감 DAO에 OOP 프로그래밍 적용해보기

> - 초난감 DAO란? 관심사에 따라 코드가 분류된 것이 아닌 모든 관심사를 가지고 있는 코드를 말함. 쉽게 말해서 서로 다른 종류의 코드가 모여 있는 것을 말합니다.(전혀 분리되지 않은 코드)
> - 처음에 적용한 방식은 Template Method 패턴, 상위 클래스에서 전체 맥락을 구성하고 하위 클래스에서 세부적인 내용을 결정하여 변경에 유리하게 만들었습니다. 이를 통해 변경되지 않는 부분으로부터 변경되는 부분을 분리했고 변경되는 부분은 하위 클래스가 결정하도록 하여 여러개의 하위 클래스를 만들어가면서 기능을 확장할 수 있음.
> - 하지만, 상속의 경우 한계점이 존재합니다. 그것은 상위 클래스와 하위 클래스 간의 긴밀한 관계가 형성된다는 것. 그렇기에 상위에서 변경이 일어나면 모든 하위 클래스에 영향이 미칩니다. 이것은 변경에 유리한 설계라고 보기엔 무언가 부족함 
> - 코드를 하나로 합치는 방법은 크게 두가지가 있습니다. 상속과 합성(포함 관계)입니다. 이제는 상속 대신에 합성을 사용하는 과정을 보여줌. 디자인 패턴에서는 코드를 합치는 대표적인 패턴이 두 가지가 있습니다. 첫 째는 Template Method이고 두 번째는 Strategy임. Template Method 패턴은 상속을 통해 코드를 하나로 합치는 것이고 Strategy 패턴은 합성(포함)을 통해 코드를 하나로 합침
> - 이제 Strategy 패턴을 적용해 나갑니다. Dao는 내부적으로 인터페이스를 활용하여 다형성이 적용된 코드를 작성했습니다. 또한, 인터페이스의 구현체를 여러개 정의하여 기능을 쉽게 확장할 수 있는 구조를 만듦. 이 부분은 SOLID원칙에 OCP와 직결됩니다. 확장에는 열려있고 변경에는 닫혀있다를 의미하는 원칙인데, 맥락이 되는 클래스는 변경되지 않으면서도 그 내부의 특정 기능이 되는 부분에 대해서는 여러개의 클래스를 구성할 수 있습니다. 즉, 맥락이 되는 클래스는 변경이 되지 않고 특정 기능에 대한 클래스를 여러개 정의하여 기능을 쉽게 확장할 수 있음
> - 여기서 추가적으로 해야할 부분이 있습니다. 현재 Dao가 자신이 사용할 오브젝트를 스스로 생성합니다. 즉, 인터페이스를 의존하여 다형성을 활용한 코드를 작성했지만, 정작 생성자에서 자신이 사용할 오브젝트를 생성하고 있습니다. 이를 외부로 분리 해야합니다. 즉, 외부에서 오브젝트를 생성하고 주입해주어야 합니다. 이것이 제어의 역전입니다. 따라서, Application에서 Dao가 사용해야할 오브젝트를 생성하고 주입해주었음 
> - 하지만, Application의 경우 두 가지 관심사가 있습니다. 바로 오브젝트를 생성하고 사용합니다. 즉, 두 개의 서로 다른 관심사를 분리해야합니다. 이 부분은 SOLID 원칙의 SRP와 연결됩니다. SRP는 단일 책임 원칙으로 하나의 클래스에선 하나의 관심사에 집중하도록 만들어야 한다는 것입니다. 이는 변경 포인트가 다른 코드를 클래스로 분리하여 변경을 최소화하고 변경되는 범위를 줄이기 위함
> - 생성하는 관심사는 Factory가 담당하고 Application은 사용하는 관심사에 집중하도록 만들면 됩니다. 이를 통해 생성과 사용이라는 관심을 분리했습니다. 이 부분과 연결되는 디자인 패턴은 Factory 패턴이 있습니다
> - 이를 통해 우리는 하나의 거대한 오브젝트에서 OOP 설계와 프로그램을 적용해 보았습니다. 스프링을 통해 우리는 위의 과정들을 직접 작업하지 않고 할 수 있습니다.  우리가 스프링을 쓰는 이유 중 하나임

<br>


#### 👉 스프링 컨테이너의 중요성(IoC, DI)

> - 스프링 컨테이너에는 여러개의 기능이 있지만. 그 중에 핵심 기능은 IoC/DI입니다. IoC란 제어의 역전으로서, 제어권을 외부에 넘겨주는 것이다. 예를들어서, 우리가 빈에서 의존하는(사용하는) 오브젝트를 생성하고 전달해 주는 것이 아닌 스프링 컨테이너가 특정 빈에 어떤 빈을 주입할 것인지를 결정합니다. 그 과정에서 쓰이는 패턴이 DI입니다. 의존성 주입이라는 의미입니다. 쉽게 말해서, 외부에서 오브젝트를 전달하는 것입니다.
> - 또, 스프링 컨테이너는 서버 운영 측면에서 오브젝트를 효율적으로 사용하도록 도와줍니다. 스프링 컨테이너는 Flyweight 패턴과 매우 유사합니다. 즉, 여러개의 싱글턴을 맵에 저장해 놓고 요청할 때 마다 해당 오브젝트를 반환해주는 형식입니다. 서버 운영 측면에서 클라이언크가 매번 요청할 때 마다 필요한 오브젝트를 생성해서 사용하는 방식은 매우 비효율적입니다. 따라서, 애플리케이션에서 사용되는 오브젝트를 싱글톤으로 등록하여 공유해서 사용하여 메모리 자원을 아낄 수 있습니다.
> - 스프링 컨테이너를 싱글톤 레지스트리라고도 합니다. 기본적으로 오브젝트를 싱글톤으로 관리하는 저장소이기 때문에 붙혀진 이름입니다. 물론, 멀티 쓰레드 환경에서는 싱글톤이 안티패턴입니다. 그래서 스프링에서는 오브젝트를 컨테이너에 등록할 때 스코프를 통해 프로토 타입으로도 등록할 수 있습니다.(기본적으로는 싱글톤으로 등록됨)


<br>


#### 👉 멀티 쓰레드 환경에서 싱글톤 패턴의 문제점

> - 가장 큰 이유는 바로 싱글톤 오브젝트의 인스턴스 변수가 멀티 쓰레드 환경에서 예기치 못하게 변경될 수 있기 때문입니다. 또한, 싱글톤 오브젝트는 테스트 하기 매우 어렵습니다.
> - 그래서, 싱글톤으로 등록될 오브젝트는 주의해서 사용해야합니다. 가장 좋은 방법은 인스턴스 변수 없이 로직으로만 구성된 오브젝트를 만드는 것입니다. 물론 해당 오브젝트로부터 특정 값을 계산하거나 사용해야 하는 경우는 메서드를 통해서 계산된 값을 저장하지 않고 반환하는 형태로 만드는 것이 좋습니다. 만약 해당 오브젝트에 인스턴스 변수가 꼭 필요한 경우에는 동기화 처리가 된 오브젝트를 사용하는 것이 좋습니다.


<br>
<br>

## 📌 02. 테스트

#### 🧑🏻‍🏫 주요 내용 작성

<img src="/images/스프링테스트.jpeg" width="800" height="500"/>


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

<br>
<br>

## 📌 03. OCP 충족을 위해 스프링에서 애용하는 '템플릿' 기법

#### 🧑🏻‍🏫 주요 내용 작성

<img src="/images/템플릿학습정리.jpeg" width="800" height="500"/>

#### 👉 템플릿이란?

> - 전체 맥락을 템플릿이라고 말함. 즉, 전체 맥락이 되는 템플릿을 구성하고 그 하위 클래스나 콜백 ... 으로 세부 내용을 결정하는 방식
> - 위와 같은 기법을 사용하는 이유는 OCP를 충족하기 위함
> - 변경되지 않고 반복되는 부분은 '템플릿'으로 구성하여 최대한 재활용하고 변경되는 부분은 분리해내서 확장하기 좋게 만든 구조

<br>

#### 👉 템플릿이 적용되는 대표적인 사례 - JDBC(try - catch - finally)

```java
public class UserDao {

    private static final String URL = "jdbc:mysql://localhost:3306/yourdb";
    private static final String USER = "root";
    private static final String PASSWORD = "password";

    public User findById(Long id) {
        Connection conn = null;
        PreparedStatement pstmt = null;
        ResultSet rs = null;

        try {
            // 1. 데이터베이스 연결
            conn = DriverManager.getConnection(URL, USER, PASSWORD);

            // 2. SQL 준비
            String sql = "SELECT * FROM users WHERE id = ?";
            pstmt = conn.prepareStatement(sql);
            pstmt.setLong(1, id);

            // 3. SQL 실행 및 결과 처리
            rs = pstmt.executeQuery();
            if (rs.next()) {
                User user = new User();
                user.setId(rs.getLong("id"));
                user.setName(rs.getString("name"));
                user.setEmail(rs.getString("email"));
                return user;
            }
        } catch (SQLException e) {
            e.printStackTrace(); // 예외 처리 (간단히 출력)
        } finally {
            // 4. 리소스 해제 (항상 실행됨)
            try {
                if (rs != null) rs.close();
                if (pstmt != null) pstmt.close();
                if (conn != null) conn.close();
            } catch (SQLException e) {
                e.printStackTrace(); // 리소스 해제 중 예외 발생 시 처리
            }
        }
        return null;
    }
}

```

> - 전통적인 JDBC 코드를 나타냄. 해당 코드의 문제점 아래와 같음
> - (1) 복잡한 try-catch-finally 구조가 중첩됨
> - (2) 모든 메서드마다 반복됨
> - 즉, 위의 문제점이 발생하는 이유는 OCP를 충족하지 못한 코드이기 때문임
> - 문제의 핵심은 변하지 않고 중복되는 코드와 로직에 따라 자주 확장하려고 변하는 코드를 잘 분리해야함 

<br>

#### 👉 OCP를 충족시키는 대표적인 디자인 패턴 - Template Method, Strategy

> #### Template Method 패턴은 상속을 통해 기능을 확장해 나감
> - 즉, 상위에서 맥락을 정해두고 하위에서 세부 내용을 결정하여 OCP를 충족시키는 디자인 패턴
> - <img src="/images/템플릿메서드.jpeg" width="400" height="400"/>
> - Template Method 패턴의 한계점
> - (1) Dao 로직마다 상속을 통해 새로운 클래스를 만들어야함
> - (2) 상위 클래스와 하위 클래스 간의 긴밀한 관계 형성
> - (3) 클래스 레벨에서 컴파일 시점에 이미 그 관계가 결정되어버리기 때문에 유연하지 못함 

<br>

> #### Strategy 패턴은 합성을 통해 기능을 확장해 나감. 즉, 변경되는 부분을 외부로 분리해 놓은 것 
> - 변경되는 부분을 클래스 레벨에서 분리해서 인터페이스를 통해서만 의존하도록 만듦
> - 확장에 해당하는 부분을 별도의 클래스로 만들어 추상화된 인터페이스를 통해 위임하는 방식
> - <img src="/images/전략.jpeg" width="400" height="400"/>
> - Strategy 패턴의 한계점
> - (1) Dao 메서드마다 새로운 Strategy 클래스를 만들어야함
> - (2) 부가적인 정보가 필요한 경우, 인스턴스 변수(iv)로 저장해야함(번거로움)

<br>

> #### Strategy & DI 활용
> - <img src="/images/전략&DI.jpeg" width="400" height="400"/>
> - DI는 Strategy 패턴의 장점을 일반적으로 활용할 수 있도록 만든 구조

<br>

#### 👉 Strategy 패턴의 한계

> - Strategy 패턴의 한계
> - (1) DAO 메서드마다 새로운 전략 클래스를 정의하고 관리해야함
> - (2) 부가적인 정보가 필요한 경우, 인스턴스 변수로 저장해서 사용해야함

<br>

#### 👉 Strategy 패턴 한계점 극복 과정

> - 이를 극복하기 위해선, Strategy를 모듈화해서 관리하지 않고 클라이언트가 가지고 있게 만들어야함. 즉, 클라이언트와 Strategy는 서로 관련도가 높기 때문에 다시 합침
> - 코드 발전 하는 과정을 요약하면 다음과 같음. '로컬 내부 클래스 사용' -> '익명 내부 클래스 변환' -> '파라미터에 익명 내부 클래스 적용' -> 'UserDao에서 JdbcContext 정의(템플릿 정의)해서 분리 -> '결과적으로 UserDao, JdbcContext, DataSource가 서로 협력'
> - DI에 대해서 다시 짚고 가자. 
>   - 인터페이스를 사이에 둬서 클래스 레벨에서는 의존관계가 고정되지 않고 런타임 시에 의존할 오브젝트와 관계를 동적으로 주입해줌
>   - 스프링의 경우 DI가 IoC 개념도 포괄함. 객체 생성, 관계 설정에 대한 제어권한을 오브젝트에서 제거하고 외부로 위임함
> - DI를 고려하면 JdbcContext가 구체 클래스이기 때문에 DI를 제대로 적용하지 못한 것이라고 생각할 수 있음. 
> - 하지만, UserDao와 JdbcContext는 강한 응집도(관련도가 높음)이기 때문에 인터페이스 없이 구체 클래스로 DI 처리해도 무방함 


<br>

#### 👉 템플릿/콜백 패턴이란?

> - 단일 전략 메서드를 갖는 전략 패턴이면서 익명 내부 클래스를 활용하여 매번 새로 콜백을 만들어 사용하고, 컨텍스트를 호출과 동시에 전략 DI를 수행하는 방식
> - 좀 더 쉽게 말하자면, 전략 패턴의 기본 구조에 익명 내부 클래스를 활용한 구조 
> - '템플릿'은 고정된 작업 흐름을 가진 코드를 재사용하기 위한 방법이고, '콜백'은 템플릿에 의해 호출되는 것을 목적으로 만들어진 오브젝트 
> - 콜백이란? 실행되는 것을 목적으로 다른 오브젝트의 메서드에 전달되는 오브젝트를 지칭함. 특정 로직을 담은 메서드를 실행 시키기 위해 사용


<br>

#### 👉 템플릿/콜백 동작 방식

> - <img src="/images/템플릿콜백작동원리.png" width="400" height="400"/>
> - 단순하게 DI 방식의 전략 패턴 구조라고 생각하면됨. 전략 패턴과 DI의 장점을 익명 내부 클래스 사용 전략과 결합한 독특한 구조
> - 템플릿/콜백 패턴의 특징은 크게 3가지가 있음
> - (1) 매번 메서드 단위로 사용할 오브젝트를 새롭게 전달해야함
> - (2) 콜백이 내부 클래스로서 자신을 생성한 클라이언트 메서드 내의 정보를 직접 참조함
> - (3) 클라이언트와 콜백이 강하게 결합됨(관련도가 높음) 

<br>

#### 👉 JdbcContext에 적용된 템플릿/콜백 패턴 

> - <img src="/images/JdbcContext템플릿콜백적용.png" width="400" height="400"/>
> - 콜백의 분리와 재활용. 콜백에서 재활용할 수 있는 부분과 변경되는 부분을 찾아서 다시 분리함. 이 과정을 통해서 SQL 문장만 파라미터로 바꿀 수 있게 하고 메서드 내용 전체를 분리하여 별도의 메서드로 만듦

```java
/**
 * 클래스 관계 : UserDao -> JdbcContext -> DataSource
 * 런타임 의존관계 : UserDao : userDao -> JdbcContext : jdbcContext -> DataSource : simpleDriverDataSource
 */

// JdbcContext.java
public class JdbcContext {
    DataSource dataSource;

    // 의존 오브젝트(DataSource) 주입 받음
    public void setDataSource(DataSource dataSource) {
        this.dataSource = dataSource;
    }

    // Jdbc 작업 맥락 구성 
    public void workWithStatementStrategy(StatementStrategy stmt) throws SQLException {
        // 참조 정보 취득
        Connection c = null;
        PreparedStatement ps = null;

        try {
            // 커넥션 취득 (맥락)
            c = dataSource.getConnection();

            // 자주 변경되는 부분(외부에서 파라미터로 주입받음, 콜백)
            ps = stmt.makePreparedStatement(c);

            // SQL 실행(맥락)
            ps.executeUpdate();
        } catch (SQLException e) { // 예외 처리(맥락)
            throw e;
        } finally { // 자원 반납(맥락)
            if (ps != null) { try { ps.close(); } catch (SQLException e) {} }
            if (c != null) { try {c.close(); } catch (SQLException e) {} }
        }
    }

    // 템플릿/콜백 패턴의 클라이언트
    public void executeSql(final String query) throws SQLException {
        workWithStatementStrategy(
                // 템플릿/콜백 패턴의 콜백 
                new StatementStrategy() {
                    public PreparedStatement makePreparedStatement(Connection c)
                            throws SQLException {
                        // 실질적으로 변경되는 부분은 'query' 부분
                        // 따라서, 응집력이 강한 클라이언트, 콜백, 템플릿을 한군데로 모아둠 
                        return c.prepareStatement(query);
                    }
                }
        );
    }
}


// UserDao.java
public class UserDao {
    private DataSource dataSource;

    public void setDataSource(DataSource dataSource) {
        this.jdbcContext = new JdbcContext();
        this.jdbcContext.setDataSource(dataSource);
        this.dataSource = dataSource;
    }

    private JdbcContext jdbcContext; // 템플릿 

    public void add(final User user) throws SQLException { // 클라이언트 
        this.jdbcContext.workWithStatementStrategy(
                // 콜백(단일 메서드 인터페이스를 구현한 익명 내부 클래스)
                new StatementStrategy() {
                    public PreparedStatement makePreparedStatement(Connection c)
                            throws SQLException {
                        PreparedStatement ps =
                                c.prepareStatement("insert into users(id, name, password) values(?,?,?)");
                        ps.setString(1, user.getId());
                        ps.setString(2, user.getName());
                        ps.setString(3, user.getPassword());

                        return ps;
                    }
                }
        );
    }


    public User get(String id) throws SQLException {
        Connection c = this.dataSource.getConnection();
        PreparedStatement ps = c
                .prepareStatement("select * from users where id = ?");
        ps.setString(1, id);

        ResultSet rs = ps.executeQuery();

        User user = null;
        if (rs.next()) {
            user = new User();
            user.setId(rs.getString("id"));
            user.setName(rs.getString("name"));
            user.setPassword(rs.getString("password"));
        }

        rs.close();
        ps.close();
        c.close();

        if (user == null) throw new EmptyResultDataAccessException(1);

        return user;
    }

    public void deleteAll() throws SQLException {
        // 최종 코드. 변경되는 부분인 SQL 문만 전달하고 그 외에는 템플릿이 처리함
        this.jdbcContext.executeSql("delete from users");
    }

    public int getCount() throws SQLException  {
        Connection c = dataSource.getConnection();

        PreparedStatement ps = c.prepareStatement("select count(*) from users");

        ResultSet rs = ps.executeQuery();
        rs.next();
        int count = rs.getInt(1);

        rs.close();
        ps.close();
        c.close();

        return count;
    }
}





```

> - JdbcContext 안에 클라이언트와 템플릿 콜백이 모두 함께 공존하면서 동작하는 구조가 됨 
> - 위와 같이 하나의 목적을 위해 서로 긴밀하게 연관되어 동작하는 응집력이 강한 코드들은 다시 합치는게 유리함 

<br>

#### 👉 스프링이 제공하는 대표적인 템플릿/콜백 기술 -> JdbcTemplate

```java

public class UserDao {
    public void setDataSource(DataSource dataSource) {
        this.jdbcTemplate = new JdbcTemplate(dataSource);
    }

    private JdbcTemplate jdbcTemplate;

    private RowMapper<User> userMapper =
            new RowMapper<User>() {
                public User mapRow(ResultSet rs, int rowNum) throws SQLException {
                    User user = new User();
                    user.setId(rs.getString("id"));
                    user.setName(rs.getString("name"));
                    user.setPassword(rs.getString("password"));
                    return user;
                }
            };


    public void add(final User user) {
        this.jdbcTemplate.update("insert into users(id, name, password) values(?,?,?)",
                user.getId(), user.getName(), user.getPassword());
    }

    public User get(String id) {
        return this.jdbcTemplate.queryForObject("select * from users where id = ?",
                new Object[] {id}, this.userMapper);
    }

    public void deleteAll() {
        this.jdbcTemplate.update("delete from users");
    }

    public int getCount() {
        return this.jdbcTemplate.queryForInt("select count(*) from users");
    }

    public List<User> getAll() {
        return this.jdbcTemplate.query("select * from users order by id",this.userMapper);
    }

}
```

<br>


## 📌 04. 스프링에서의 예외 처리

#### 👉 예외처리에서 하지 말아야할 행동

```java
// (1) 예외 은폐하기

try {
    // 예외 발생 가능 로직 
} catch (SqlException e) {
    // 마땅한 예외 처리 로직 없음
}


try {
    // 예외 발생 가능 로직 
} catch (SqlException e) {
    e.printStackTrace();
}


// (2) 무의미하고 무책임한 throws 

public void method() throws Exception {
    // 예외 발생 가능 로직 
    method1();
}

public void method1() throws Exception {
    // 예외 발생 가능 로직 
    method2();
}

public void method2() throws Exception {
    // 예외 발생 가능 로직
}

```
> - (1) 예외 은폐하기
>   - 예외를 잡고 마땅한 처리를 하지 않음
>   - 예외 처리시 명심해야 하는 부분은 '모든 예외는 적절하게 복구되든지 아니면 작업을 중단시키고 운영자나 개발자에게 분명하고 빠르게 통보해야함'
> - (2) 무의미하고 무책임한 throws 
>   - throws Exception을 별 생각 없이 남발하면 안됨
>   - 예외 발생 부분을 명확히 파악하기 어려움 


<br>

#### 👉 예외의 종류와 특징

> - Error : 시스템에 뭔가 비정상적인 상황이 발생한 경우, catch 블록으로 잡아 봤자 아무런 대응 방법이 없음. 예를들어, OutOfMemoryError, StackOverflowError 등
> - <img src="/images/예외상속계층도.png" width="400" height="400"/>
> - RuntimeException : 개발자의 부주의로 발생하는 예외. 예를들어, NullPointerException, IllegalArgumentException, IndexOutOfBoundsException 등
>   - 예외처리를 강제하지 않음
>   - 주로 프로그램의 오류가 있을 때 예외가 발생하도록 의도된 것
>   - 개발자의 부주의로 인해 발생하는 경우 
> - Checked Exception : 컴파일러가 강제로 예외 처리를 요구하는 예외. 예를들어, IOException, SQLException 등
>   - 예외처리를 강제함. 즉, try-catch로 예외를 처리하든가 호출한 쪽에서 전달해서 처리하게끔 만들어야함 
>   - 사용자의 부주의로 인해 발생할 수 있는 예외

<br>

#### 👉 예외처리 방법 -> 예외 복구/ 예외처리 회피/ 예외 전환

```java
// (1) 재시도 : 일정 시간 동안 대기했다가 최대 횟수 만큼 시도를 해보는 것

import java.sql.SQLException;

int maxretry = MAX_RETRY;

while(maxretry-->0){
    try{
        // 예외 발생 가능 로직  
        return; // 작업 성공 
    }catch(SomeException e){
        // 로그 출력, 정해진 시간만큼 대기
    }finally{
        // 리소스 반납, 정리 작업 
    }
}

// (2) 예외처리 회피 : 예외를 처리하지 않고 자신을 호출한 쪽으로 예외를 전달함 

public void add() throws SQLException {
    try {
        // JDBC API
    } catch (SQLException e) {
        // 로그 출력
        throw e;
    }
}


// (3) 예외 전환 : 예외를 다른 예외로 전환하는 방법
public void add(User user) throws DuplicateUserIdException, SQLException {
    try {
        // 예외 발생 가능한 로직 
    } catch (SQLException e) {
        if (e.getErrorCode() == MysqlErrorNumbers.ER_DUP_ENTRY) {
            throw new DuplicateUserIdException(e); // 예외 전환 
        } else {
            throw e;
        }
    }
}

```

> - (1) 예외 복구 : 예외가 발생했을 때 복구해서 정상적인 상태로 만듦
>   - 예외 상황을 파악하고 문제를 해결하며 정상 상태로 되돌림
>   - 대표적인 예시는 네트워크가 불안하여 서버 접속이 원할치 않은 경우 재시도(재접속)을 통해 복구함
>   - 재시도 : 일정 시간 동안 대기했다가 최대 횟수 만큼 시도를 해보는 것 
>     - 일정 시간 대기했다가 다시 접속을 시도해보는 방법
>     - 예외 상황으로부터 복구를 시도함
>     - 실패했다면 예외 복구 포기
>
> - (2) 예외처리 회피 : 예외를 처리하지 않고 자신을 호출한 쪽으로 예외를 전달함 
>   - 의도가 분명할 때 사용해야함. 즉, 자신을 사용하는 쪽에서 예외를 다루는게 최선의 방법이라는 판단이 있어야함
> 
> - (3) 예외 전환 : 예외를 다른 예외로 전환하는 방법
>   - 발생한 예외를 그대로 전달하는 것이 아닌, 적절한 예외로 전환해서 전달해야함. 예외를 전환하는 이유에는 크게 두가지가 있음
>   - (1) 의미를 명확하게 하기 위해 사용 - Dao에서 SQLException은 예외 전환해서 던지는 게 좋음(의미가 불분명하기 때문)
>   - (2) 특정 기술의 정보를 해석하는 코드를 비즈니스 로직에 담는 것은 어색함. 즉, 특정 계층에 종속되지 않게 하기위해 예외를 전환함
>   - 예외 전환 방법 크게 두가지가 있음 
>   - (1) 중첩 예외 : 전환하는 예외에 원래 예외를 담음
>   - (2) 포장 : 의미를 명확하게 하기보다는 체크 예외를 언체크(런타임) 예외로 바꾸기 위함 
>     - 클라이언트에서 일일이 예외를 잡아도 마땅한 대처 방법이 없음
>     - 런타임 예외로 포장해서 전달하고 예외 처리 서비스 등을 이용하여 로그를 남기고, 관리자에게 메일 ... 을 통보하고 사용자에게 친절한 안내 메시지를 보여주는 식으로 처리하는게 좋음


<br>

#### 👉 예외처리 전략


```java
// (2) 정상적인 흐름을 따르는 코드는 그대로 두고 잔고 부족과 같은 예외 상황에서는 비즈니스적 의미를 띤 예외를 발생시킴 - InsufficientBalanceException

try {
    BigDecimal balance = account.withdraw(amount);
    // 정상적인 흐름을 따르는 코드
} catch (InsufficientBalanceException e) {
    // 예외 처리 로직
    BigDecimal availFunds = e.getAvailFunds();
    
    // 잔고 부족 안내 메시지 준비. 이를 출력하도록 진행 
} 


```

> #### 런타임 예외의 일반화
> - 체크 예외가 일반적인 예외를 다루고 런타임 예외(언체크 예외)는 시스템 장애나 프로그램상의 오류에 사용
> - 어차피 런타임 예외이므로 시스템 레벨에서 알아서 처리해줄 것이고 꼭 필요한 경우는 런타임 예외라도 잡아서 복구하거나 대응할 수 있음
> 
> #### 애플리케이션 예외
> - 애플리케이션 자체의 로직에 의해 의도적으로 발생시키고 반드시 catch로 대처하도록 요구하는 예외
> - 예를들어서, 사용자가 요청한 금액을 은행 계좌에서 출금하는 기능을 가진 메서드가 있음. 현재 잔고를 확인하고 허용 범위를 넘어서는 출금을 요청하면 작업을 중단시키고 적절한 경고를 사용자에게 보내야함
> - (1) 리턴 값을 일종의 결과 상태를 나타내는 정보로 활용함 - 0, -1, -999
> - (2) 정상적인 흐름을 따르는 코드는 그대로 두고 잔고 부족과 같은 예외 상황에서는 비즈니스적 의미를 띤 예외를 발생시킴 - InsufficientBalanceException
>   - 해당 방식이 좋음
>   - 해당 예외를 '체크 예외'로 만듦. 잔고 부족처럼 자주 발생 가능한 예외상황에 대한 로직을 구현하도록 강제함 


<br>

#### 👉 스프링에서의 SQLException 처리 

> - SQLException의 경우 99%가 코드 레벨에서 복구 불가능함
> - 가장 효율적인 대처 방안은 '관리자나 개발자에게 빠르게 예외가 발생했다는 사실을 통보하는 것'
> - SQLException는 복구 불가능하기에 무분별한 throws 선언이 등장하도록 방치하지 않고 가능한 빨리 언체크(런타임) 예외로 전환해줌
> - 위와 같이 예외 전환의 의의는 크게 2가지가 있음
> - (1) 불필요한 catch/throws 선언을 줄임
> - (2) 예외를 좀 더 의미있고 추상화된 예외로 전환


<br>

#### 👉 JDBC의 한계

> - DB 기술을 자유롭게 바꾸어 사용하기에는 어려움. 크게 2가지 이유가 있음
> - (1) 비표준 SQL 
>   - 대부분의 DB는 표준을 따르지 않고 비표준 문법과 기능을 제공함. 예를들어서, 페이징 처리할 때 MySQL은 limit, offset을 사용하고 Oracle은 rownum을 사용함
>   - 비표준 SQL은 결국 DAO 코드에 명시되고 DAO는 특정 DB에 종속되어 버림
>   - DAO를 DB 별로 만들어 사용하거나 SQL을 외부에서 독립시켜 바꿔 쓸수있게 만듦
> - (2) 호환성 없는 SQLException의 DB 에러 정보
>   - DB마다 SQL만 다른 것이 아니라 예외의 종류와 원인들도 제각각임
>   - JDBC는 다양한 예외를 SQLException 하나에 담음. 그로인해, SQLException의 getErrorCode()로 조회되는 DB에러 코드는 DB별로 상이함
>   - 결국, 호환성 없는 에러코드와 표준을 잘 따르지 않는 상태 코드를 가진 SQLException만으로 DB에 독립적인 유욘한 코드를 작성하는 것은 불가능함 

<br>

#### 👉 DB에러 코드 매핑을 통한 전환

> - 문제는 SQLException의 비표준 에러 코드와 SQL 상태 정보를 어떻게 다루느냐임
> - DB별 에러 코드를 참고해서 발생한 예외의 원인이 무엇인지 해석해주는 기능을 만드는 것
> - 스프링은 DB별 에러 코드를 분류해서 스프링이 정의한 예외 클래스와 매핑해놓은 에러 코드 매핑정보 테이블을 만들어두고 활용함 
>   - <img src="/images/오라클에러코드매핑.png" width="400" height="400"/>
> - 스프링에서는 DataAccessException 이라는 SQLException을 대체할 수 있는 런타임 예외 정의
>   - 이 하위 클래스에는 세분화된 예외 클래스들이 정의됨 - DuplicateKeyException, DataIntegrityViolationException, BadSqlGrammarException 등


<br>

#### 👉 스프링이 DataAccessException 계층 구조를 이용해 기술에 독립적인 예외를 정의하고 사용하게 하는 이유 -> 서비스 계층이 기술에 종속되는 것을 막기 위함

```java

// JDBC API
public void add(User user) throws SQLException;

// JPA API
public void add(User user) throws PersistenceException;

// Hibernate API
public void add(User user) throws HibernateException;

// JDO API
public void add(User user) throws JDOException;

```

> - DAO에서 사용되는 데이터 액세스 기술의 API 특정 예외에 종속시키지 않기 위함
> - DAO를 인터페이스로 분리하여 메서드 구현을 추상화 했지만, 구현 기술마다 발생하는 예외가 다르기에 메서드의 선언이 달라짐 
> - 문제는 DAO를 사용하는 클라이언트 입장에서는 DAO의 사용 기술에 따라 예외 처리가 달라져야함. 즉, 클라이언트가 DAO의 기술에 의존적이게 되어버림


<br>

#### 👉 데이터 액세스 예외 추상화와 DataAccessExcetion 계층 구조

> - <img src="/images/DataAccessException상속계층도.png" width="400" height="400"/>
> - 스프링에서는 위의 문제를 해결하고자 데이터 액세스 기술을 사용할 때 발생하는 예외들을 모두 추상화해서 DataAccessException 계층 구조 안에 정의함
> - <img src="/images/UserDao인터페이스와구현의분리.png" width="400" height="400"/>
> - 이를 통해, DAO를 사용하는 클라이언트는 특정 기술에 종속되지 않도록 만듦

<br>

#### 👉 DataAccessException 활용시 주의사항

> - 스프링의 DataAccessException이 기술에 상관없이 어느정도 추상화된 공통 예외를 변환해주긴 하지만 한계가 있음
> - 예를들어서, 키 값이 중복되는 상황에서는 JDBC의 경우 DuplocatedKeyException이 발생하지만, Hibernate에서는 DataIntegrityViolationException이 발생함
> - DataAccessException을 잡아서 처리하는 코드를 만들려면 학습 테스트로 충분히 파악하고 진행하는 것이 좋음


<br>

#### 👉 커스텀 예외 변환기, 전역 예외 처리기 

```java
// (1) 커스텀 예외 변환기 사용
// 커스텀 예외 변환기 정의 
public class CustomSQLExceptionTranslator extends SQLErrorCodeSQLExceptionTranslator {

    public CustomSQLExceptionTranslator(DataSource dataSource) {
        super(dataSource);
    }

    @Override
    protected DataAccessException customTranslate(String task, String sql, SQLException ex) {
        // SQL 상태 코드나 SQL 예외 메시지를 기준으로 커스텀 예외 처리를 구현
        if (ex.getErrorCode() == SOME_DUPLICATE_KEY_ERROR_CODE) {
            return new DuplicateKeyException("중복된 키 에러 발생", ex);
        }
        if (ex.getErrorCode() == SOME_INTEGRITY_VIOLATION_ERROR_CODE) {
            return new DataIntegrityViolationException("데이터 무결성 위반", ex);
        }
        // 기본 Spring 예외 변환으로 처리하지 못한 예외는 부모 클래스로 위임
        return super.customTranslate(task, sql, ex);
    }
}


// 커스텀 예외 변환기 빈 등록, 추후에 사용할 오브젝트에 주입해줘야함 
@Bean
public CustomSQLExceptionTranslator exceptionTranslator(DataSource dataSource) {
    return new CustomSQLExceptionTranslator(dataSource);
}


// (2) 전역 예외 처리기 사용 
@ControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(DuplicateKeyException.class)
    public ResponseEntity<String> handleDuplicateKeyException(DuplicateKeyException ex) {
        return new ResponseEntity<>("중복된 키 에러: " + ex.getMessage(), HttpStatus.CONFLICT);
    }

    @ExceptionHandler(DataIntegrityViolationException.class)
    public ResponseEntity<String> handleDataIntegrityViolationException(DataIntegrityViolationException ex) {
        return new ResponseEntity<>("데이터 무결성 위반: " + ex.getMessage(), HttpStatus.BAD_REQUEST);
    }
    
    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleGeneralException(Exception ex) {
        return new ResponseEntity<>("예기치 못한 오류: " + ex.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
    }
}


// (3) AOP 기능 활용 - 커스텀 예외 변환기와 AOP를 동시에 적용함 
@Aspect
@Component
public class ExceptionTranslationAspect {

    private final CustomSQLExceptionTranslator exceptionTranslator;

    @Autowired
    public ExceptionTranslationAspect(CustomSQLExceptionTranslator exceptionTranslator) {
        this.exceptionTranslator = exceptionTranslator;
    }

    @Around("execution(* com.example.repository.*.*(..))")
    public Object translateException(ProceedingJoinPoint pjp) throws Throwable {
        try {
            return pjp.proceed();
        } catch (SQLException ex) {
            throw exceptionTranslator.translate(pjp.getSignature().getName(), null, ex);
        }
    }
}

```


> - 위의 문제를 다시 살펴보면, 중복 키가 발생한 상황에서 각 기술마다 발생되는 DataAccessException이 다름
> - JDBC는 DuplicatedKeyException이고 Hibernate는 DataIntegrityViolationException임
>   - 이런 부분을 꼼꼼하게 잘 파악하기 위해선 학습 테스트가 반드시 선행되야함 
> - 이를 효율적으로 대처하는 방식은 크게 2가지가 있음
> - (1) 커스텀 예외 변환기 사용
>   - 각 기술의 예외를 표준화된 방식으로 처리할 수 있는 예외 변환기
> - (2) 전역 예외 처리기 사용
>   - AOP나 스프링의 @ControllerAdvice 같은 예외처리 메커니즘을 사용하여 일관된 방식으로 처리 


<br>
<br>

## 📌 05. 스프링의 서비스 추상화 

#### 👉 서비스 추상화란?

> - 성격이 비슷하지만 구체적인 사용법이 상이한 기술을 추상화하고 이를 일관된 방법으로 사용하게끔 만듦
> - 위와 같이 하는 이유는 OCP, DI 원칙을 지키기 위함
> - 예를들어서, 특정 서비스 로직이 특정 데이터 액세스 기술에 종속되어 버리면 이는 확장에 매우 불리한 구조임
> - 이를 해결하고자 스프링에서는 서비스 추상화 기술을 제공함
>   - PlatformTransactionManager, ...

<br>

#### 👉 사용자 파트 요구사항 추가 및 개발 흐름 설명 

```java
// (*1) 변경되야 하는 사용자의 이외의 정보는 변경되지 않았음을 직접 확인
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations="/test-applicationContext.xml")
public class UserDaoTest {
    
	@Test
	public void update() {
		dao.deleteAll();
		
		dao.add(user1);		// 수정할 사용자
		dao.add(user2);		// 수정하지 않을 사용자
		
		user1.setName("오민규");
		user1.setPassword("springno6");
		user1.setLevel(Level.GOLD);
		user1.setLogin(1000);
		user1.setRecommend(999);
		
		dao.update(user1);
		
		User user1update = dao.get(user1.getId());
		checkSameUser(user1, user1update);
		User user2same = dao.get(user2.getId());
		checkSameUser(user2, user2same);
	}

}


@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations="/test-applicationContext.xml")
public class UserServiceTest {
    @Autowired UserService userService;
    @Autowired UserDao userDao;
    @Autowired DataSource dataSource;

    List<User> users;	// test fixture

    @Before
    public void setUp() {
        users = Arrays.asList(
                new User("bumjin", "박범진", "p1", Level.BASIC, MIN_LOGCOUNT_FOR_SILVER-1, 0),
                new User("joytouch", "강명성", "p2", Level.BASIC, MIN_LOGCOUNT_FOR_SILVER, 0),
                new User("erwins", "신승한", "p3", Level.SILVER, 60, MIN_RECCOMEND_FOR_GOLD-1),
                new User("madnite1", "이상호", "p4", Level.SILVER, 60, MIN_RECCOMEND_FOR_GOLD),
                new User("green", "오민규", "p5", Level.GOLD, 100, Integer.MAX_VALUE)
        );
    }

    @Test
    public void upgradeLevels() throws Exception {
        userDao.deleteAll();
        for(User user : users) userDao.add(user);

        userService.upgradeLevels();

        checkLevelUpgraded(users.get(0), false);
        checkLevelUpgraded(users.get(1), true);
        checkLevelUpgraded(users.get(2), false);
        checkLevelUpgraded(users.get(3), true);
        checkLevelUpgraded(users.get(4), false);
    }

    private void checkLevelUpgraded(User user, boolean upgraded) {
        User userUpdate = userDao.get(user.getId());
        if (upgraded) {
            assertThat(userUpdate.getLevel(), is(user.getLevel().nextLevel()));
        }
        else {
            assertThat(userUpdate.getLevel(), is(user.getLevel()));
        }
    }

    // (*2) service 테스트 실행. 여기서 눈여겨 봐야할 것은 '한명은 Level에 null 적용하고 나머지 한명은 GOLD를 적용함'
    @Test
    public void add() {
        userDao.deleteAll();

        User userWithLevel = users.get(4);	  // GOLD 레벨  
        User userWithoutLevel = users.get(0);
        userWithoutLevel.setLevel(null);

        userService.add(userWithLevel);
        userService.add(userWithoutLevel);

        User userWithLevelRead = userDao.get(userWithLevel.getId());
        User userWithoutLevelRead = userDao.get(userWithoutLevel.getId());

        assertThat(userWithLevelRead.getLevel(), is(userWithLevel.getLevel()));
        assertThat(userWithoutLevelRead.getLevel(), is(Level.BASIC));
    }

    @Test
    public void upgradeAllOrNothing() throws Exception {
        UserService testUserService = new TestUserService(users.get(3).getId());
        testUserService.setUserDao(this.userDao);
        testUserService.setDataSource(this.dataSource);

        userDao.deleteAll();
        for(User user : users) userDao.add(user);

        try {
            testUserService.upgradeLevels();
            fail("TestUserServiceException expected");
        }
        catch(TestUserServiceException e) {
        }

        checkLevelUpgraded(users.get(1), false);
    }


    static class TestUserService extends UserService {
        private String id;

        private TestUserService(String id) {
            this.id = id;
        }

        protected void upgradeLevel(User user) {
            if (user.getId().equals(this.id)) throw new TestUserServiceException();
            super.upgradeLevel(user);
        }
    }

    static class TestUserServiceException extends RuntimeException {
    }



}

```

> #### 사용자 파트 요구사항이 추가됨 - 사용자 레벨 요구사항
>   - 사용자 레벨은 BASIC, SILVER, GOLD로 나뉨
>   - 로그인 횟수, 추천수를 기반으로 레벨을 업그레이드함
> 
> #### update와 같은 쿼리 테스트할 때 주의할 부분 - where 절 없이도 문제 없이 동작함 
>   - 이런 부분들도 테스트를 통해서 확인해야함
>   - 즉, update() 태스트는 수정할 로우의 내용이 바뀐 것만 확인하는 경우만 확인하는 것이 아니라 수정되지 말아야 할 로우의 내용이 그대로 남아 있는지 확인해야함
>   - 위의 문제를 해결하기 위한 2가지 방법 
>   - (1) update 반환타입이 int이기 때문에 적용된 로우수가 몇 인지 확인하기
>   - (2) 변경되야 하는 사용자의 이외의 정보는 변경되지 않았음을 직접 확인
>     - 사용자 2명 등록, 한명은 업데이트 적용 나머지 한명은 업데이트 적용하지 않음 

```java
@Test
public void update() {
    dao.deleteAll();
		
    dao.add(user1);		// 수정할 사용자
    dao.add(user2);		// 수정하지 않을 사용자
		
    user1.setName("오민규");
    user1.setPassword("springno6");
    user1.setLevel(Level.GOLD);
    user1.setLogin(1000);
    user1.setRecommend(999);
		
    dao.update(user1);
		
    User user1update = dao.get(user1.getId());
    checkSameUser(user1, user1update);
    User user2same = dao.get(user2.getId());
    checkSameUser(user2, user2same);
}
```


> #### 처음 가입하는 사용자는 기본적으로 Basic 부여
> - DAO의 add()는 해당 로직'처음 가입하는 사용자는 기본적으로 Basic 부여'을 처리하기엔 적합하지않음
> - service가 알맞음. 사용자가 등록할때 해당 로직 적용
> - service 테스트 실행. 여기서 눈여겨 봐야할 것은 '한명은 Level에 null 적용하고 나머지 한명은 GOLD를 적용함'(*2)
>   - null -> Basic
>   - GOLD -> GOLD

```java
@Test
public void add() {
    userDao.deleteAll();

    User userWithLevel = users.get(4);	  // GOLD 레벨  
    User userWithoutLevel = users.get(0);
    userWithoutLevel.setLevel(null);

    userService.add(userWithLevel);
    userService.add(userWithoutLevel);

    User userWithLevelRead = userDao.get(userWithLevel.getId());
    User userWithoutLevelRead = userDao.get(userWithoutLevel.getId());

    assertThat(userWithLevelRead.getLevel(), is(userWithLevel.getLevel()));
    assertThat(userWithoutLevelRead.getLevel(), is(Level.BASIC));
}

```


> #### 코드 개선 자가 체크리스트
> - (1) 중복코드가 존재하는지
> - (2) 코드의 가독성, 명확성은 적당한지 - 이해하기 쉬운 코드인지
> - (3) 코드의 배치가 알맞은지(적절한 위치에 로직이 놓여있는지)
> - (4) 변경이 일어난다고 가정했을때, 효율적으로 대처할 수 있는지
> 
> #### 해당 코드의 문제점 
> - if 문이 덕칠되어 있음 - 성격이 다른 여러가지 로직이 한군데에 혼재되어 있음
>   - 레벨/업그레이드 조건 파악
>   - 필드 수정
>   - 수정 플래그 체크 표시
>   - 변경 수행
> - upgradeLevel(User user)의 문제점 
> - 다음 단계가 무엇인가 확인하는 로직과 그때 사용자 오브젝트 level 필드를 변경하는 로직이 혼재되어 있음. 노골적으로 드러나 있고 예외상황 처리가 적절히 되어있지않음 
> 
> #### 객체지향 코드 작성하기
> - 객체지향 코드는 '다른 오브젝트의 데이터를 가져와서 직접 작업을 하는 것이 아닌, 데이터를 갖고 있는 오브젝트에게 작업을 요청하는 것. 즉, 객체 간의 소통과 협력이 중요한 구조임'
> - 오브젝트에게 데이터를 요구하지 않고 작업을 해달라고 요청하는 것이 가장 기본적인 객체지향 코드
> - 프로젝트 예시를 들어보면, 의류 카테고리 정보를 담고 있는 오브젝트가 있다고 가정할때 해당 오브젝트에게 적절한 역할이 있어야함(서비스 오브젝트가 임의로 카테고리 오브젝트의 데이터를 조회하고 조작하는 작업을 하면안됨) 
> - 이런 관점에서 '레벨 순서와 다음 레벨이 무엇인지 결정하는 일은 Level 스스로가 결정하기'
 
```java
public enum Level {
	GOLD(3, null), SILVER(2, GOLD), BASIC(1, SILVER);  
	
	private final int value;
	private final Level next; 
	
	Level(int value, Level next) {  
		this.value = value;
		this.next = next; 
	}
	
	public int intValue() {
		return value;
	}
	
	public Level nextLevel() { 
		return this.next;
	}
	
	public static Level valueOf(int value) {
		switch(value) {
		case 1: return BASIC;
		case 2: return SILVER;
		case 3: return GOLD;
		default: throw new AssertionError("Unknown value: " + value);
		}
	}
}
```
> - User 내부 정보가 변경되는 것은 UserService 보다는 User 오브젝트 스스로가 다루는 게 적절함
>   - User는 사용자 정보를 담고 있는 단순한 오브젝트이지만 특정 역할을 수행할 수 있음
>     - UserService가 일일이 User 정보를 업그레이드 시키는 것 보다 User에게 레벨 업그레이드를 해달라고 요청
>     - User 오브젝트는 여러 오브젝트와 협력하므로 스스로 예외 상황에 대해 검증 기능을 갖고 있는 것이 적합함 

```java

public class User {
    String id;
    String name;
    String password;
    Level level;
    int login;
    int recommend;

    public User() {
    }

    public User(String id, String name, String password, Level level,
            int login, int recommend) {
        this.id = id;
        this.name = name;
        this.password = password;
        this.level = level;
        this.login = login;
        this.recommend = recommend;
    }


    public String getId() {
        return id;
    }
    public void setId(String id) {
        this.id = id;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public String getPassword() {
        return password;
    }
    public void setPassword(String password) {
        this.password = password;
    }

    public Level getLevel() {
        return level;
    }

    public void setLevel(Level level) {
        this.level = level;
    }

    public int getLogin() {
        return login;
    }

    public void setLogin(int login) {
        this.login = login;
    }

    public int getRecommend() {
        return recommend;
    }

    public void setRecommend(int recommend) {
        this.recommend = recommend;
    }

    public void upgradeLevel() {
        Level nextLevel = this.level.nextLevel();
        if (nextLevel == null) {
            throw new IllegalStateException(this.level + "은  업그레이드가 불가능합니다");
        }
        else {
            this.level = nextLevel;
        }
    }
}

```

> #### 특정 정책을 처리하는 오브젝트를 인터페이스로 정의
> - 현재 회원 업그레이드 정책을 인터페이스로 정의함
> - 마찬가지로, 쿠폰 발행 정책, ... 여러 도메인에서 발생되는 정책을 인터페이스로 정의해서 관리하는 것은 매우 좋은 생각

```java
public interface UserLevelUpgradePolicy {
    boolean canUpgradeLevel(User user);
    void upgradeLevel(User user);
}
```

> #### 정기 사용자 레벨 관리 작업을 수행하는 도중에 네트워크 연결 문제로 해당 작업을 완료하지 못함 - 모든 회원을 초기 상태 레벨로 복구함
> - 이런 상황을 대처하기 위해 '트랜잭션'을 적용함
> - 예외적인 상황을 작업 중간에 강제로 발생시키는 테스트 코드를 작성해야함
>   - 테스트 대역(UserService) 사용해서 해당 테스트 코드 작성
>   - 테스트의 목적에 맞게 동작하도록 클래스를 만듦
>     - 테스트 대역은 테스트 클래스 내부에 스태틱 클래스로 만드는 것이 좋음
> - 위의 내용 토대로 테스트를 작성하고 시도하면 실패함 -> 트랜잭션 적용이 제대로 적용안됨

```java
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations="/test-applicationContext.xml")
public class UserServiceTest {
	@Autowired UserService userService;	
	@Autowired UserDao userDao;
	@Autowired DataSource dataSource;
	
	List<User> users;	// test fixture
	
	@Before
	public void setUp() {
		users = Arrays.asList(
				new User("bumjin", "박범진", "p1", Level.BASIC, MIN_LOGCOUNT_FOR_SILVER-1, 0),
				new User("joytouch", "강명성", "p2", Level.BASIC, MIN_LOGCOUNT_FOR_SILVER, 0),
				new User("erwins", "신승한", "p3", Level.SILVER, 60, MIN_RECCOMEND_FOR_GOLD-1),
				new User("madnite1", "이상호", "p4", Level.SILVER, 60, MIN_RECCOMEND_FOR_GOLD),
				new User("green", "오민규", "p5", Level.GOLD, 100, Integer.MAX_VALUE)
				);
	}

	@Test
	public void upgradeLevels() throws Exception {
		userDao.deleteAll();
		for(User user : users) userDao.add(user);
		
		userService.upgradeLevels();
		
		checkLevelUpgraded(users.get(0), false);
		checkLevelUpgraded(users.get(1), true);
		checkLevelUpgraded(users.get(2), false);
		checkLevelUpgraded(users.get(3), true);
		checkLevelUpgraded(users.get(4), false);
	}

	private void checkLevelUpgraded(User user, boolean upgraded) {
		User userUpdate = userDao.get(user.getId());
		if (upgraded) {
			assertThat(userUpdate.getLevel(), is(user.getLevel().nextLevel()));
		}
		else {
			assertThat(userUpdate.getLevel(), is(user.getLevel()));
		}
	}

	@Test 
	public void add() {
		userDao.deleteAll();
		
		User userWithLevel = users.get(4);	  // GOLD 레벨  
		User userWithoutLevel = users.get(0);  
		userWithoutLevel.setLevel(null);
		
		userService.add(userWithLevel);	  
		userService.add(userWithoutLevel);
		
		User userWithLevelRead = userDao.get(userWithLevel.getId());
		User userWithoutLevelRead = userDao.get(userWithoutLevel.getId());
		
		assertThat(userWithLevelRead.getLevel(), is(userWithLevel.getLevel())); 
		assertThat(userWithoutLevelRead.getLevel(), is(Level.BASIC));
	}
 
	@Test
	public void upgradeAllOrNothing() throws Exception {
		UserService testUserService = new TestUserService(users.get(3).getId());  
		testUserService.setUserDao(this.userDao); 
		testUserService.setDataSource(this.dataSource);
		 
		userDao.deleteAll();			  
		for(User user : users) userDao.add(user);
		
		try {
			testUserService.upgradeLevels();   
			fail("TestUserServiceException expected"); 
		}
		catch(TestUserServiceException e) { 
		}
		
		checkLevelUpgraded(users.get(1), false);
	}

	
    // 테스트 대역 - 강제로 예외를 발생시키는 UserService
	static class TestUserService extends UserService {
		private String id;
		
		private TestUserService(String id) {  
			this.id = id;
		}

		protected void upgradeLevel(User user) {
			if (user.getId().equals(this.id)) throw new TestUserServiceException();  
			super.upgradeLevel(user);  
		}
	}
	
    // 테스트용 예외 정의 
	static class TestUserServiceException extends RuntimeException {
	}



}

```

> #### 트랜잭션
> - upgradeLevels()가 하나의 트랜잭션 안에서 동작하지 않았기 때문에 위의 테스트는 실패함
>   - 트랜잭션 : 여러 작업을 하나로 묶음, 더 이상 나눌 수 없는 논리적인 작업 단위
>   - 작업 중간에 예외가 발생하여 작업을 완료하지 못할경우 해당 데이터를 작업 시행 이전으로 되돌림(롤백)
> 
> #### 트랜잭션 경계설정
> - DB는 그 자체로 완벽한 트랜잭션을 지원함
>   - 트랜잭션에는 커밋/롤백이 있음
>   - 커밋 : 트랜잭션의 작업을 확정하고 DB에 반영
>   - 롤백 : 트랜잭션의 작업을 취소하고 DB를 이전 상태로 되돌림
> - 트랜잭션은 시작지점과 끝지점이 있음. 애플리케이션 내에서 트랜잭셔이 시작되고 끝나는 지점까지를 트랜잭션 경계라고함
> - 트랜잭션 경계는 하나의 Connection이 만들어지고 닫히는 범위 안에 존재함
>   - 하나의 DB 커넥션 내에 만들어지는 트랜잭션을 로컬 트랜잭션이라고함 
> - upgradeLevels() 와 같이 DB에 여러번 업데이트를 하는 작업은 하나의 트랜잭션으로 구성해야함. 하나의 트랜잭션으로 묶기 위해선 DB 커넥션을 하나만 사용해야함
> - <img src="/images/트랜잭션처리.jpeg" width="400" height="400"/>
> 
> #### 비즈니스 로직 내의 트랜잭션 경계 설정
> - 트랜잭션 경계 설정은 서비스에서 처리함
> - 하지만, 직접 트랜잭션 경계 설정을 할 경우 밑에와 같은 문제들이 발생함
> - (1) 비즈니스 로직과 커넥션 리소스 처리 로직이 혼재됨
> - (2) DAO 메소드와 비즈니스 로직을 담아두는 UserService의 메서드에 일일이 Connection 파라미터를 추가해야함 
> - (3) Connection 파라미터가 UserDao 인터페이스의 메서드에 추가되면, 더 이상 해당 인터페이스는 데이타 액세스 기술로부터 자유롭지 못함
> - (4) 위의 변경사항으로 테스트 코드에도 영향을 미침

```java

// 트랜잭션 경계설정 구조 적용 
public void upgradeLevels() throws Exception {
    // (1) DB Connection 생성
    // (2) Transaction 시작
    
    try {
        // (3) DAO 메서드 호출 
        // (4) Transaction 커밋
    } catch (Exception e) {
        // (5) Transaction 롤백
        throw e;
    } finally {
        // (6) DB Connection 종료
    }
}

// 인터페이스에 Connection 파라미터 추가
public interface UserDao {
   public void add(Cennection c, User user);
   public User get(Connection c, String id);
   public void update(Connection c, User user);
}


// Connection을 공유하도록 수정한 UserService
class UserService {
    public void upgradeLevels() throws Exception {
        Connection c = ...;
        
        try {
            ...
            upgradeLevel(c, user); // Connection 전달함 
        } 
        ... 
    }
    
    // Connection 파라미터 추가됨 
    protected void upgradeLevel(Connection c, User user) {
        user.upgradeLevel();
        userDao.update(c, user);
    }
}
```

> #### 스프링의 트랜잭션 동기화 처리 지원 - TransactionSynchronizationManager
> - 트랜잭션 동기화
> - 트랜잭션 동기화는 트랜잭션을 시작하기 위해 만든 Connection 오브젝트를 특별한 저장소에 보관해두고 이후에 호출되면 Dao의 메서드에 저장된 Connection을 가져다가 사용하게함
> - 트랜잭션 동기화 저장소는 작업 스레드마다 독립적으로 Connection 오브젝트를 지정하고 관리하기 때문에 멀티 쓰레드 환경에서도 안점함
> - <img src="/images/트랜잭션동기화처리.jpeg" width="400" height="400"/>
> - 스프링에서 해당 작업을 지원하기 위해 TransactionSynchronizationManager 인터페이스 지원
> - 트랜잭션 동기화 작업을 초기화하도록 요청함
> - DataSourceUtils에서 제공하는 getConnection()을 통해서 DB Connection을 생성함
> - 해당 메서드는 Connection 오브젝트를 생성해주며 트랜잭션 동기화에 사용하도록 저장소에 바인딩함 


<br>

#### 👉 트랜잭션 서비스 추상화 
> - 글로벌 트랜잭션은 별도의 트랜잭션 관리자를 통해 트랜잭션을 관리하는 방식
> - 글로벌 트랜잭션을 적용해야 트랜잭션 매니저를 통해 여러 개의 DB가 참여하는 작업을 하나의 트랜잭션으로 만들 수 있음(JTA를 통해 글로벌 트랜잭션 관리)
> - <img src="/images/JTA작동원리.png" width="400" height="400">
> - 하지만, 하이버네이트로 이용한 트랜잭션 관리 코드는 JDBC나 JTA의 코드와 다름
>   - 트랜잭션의 경계설정을 해야할 필요가 생기면 다시 특정 데이타 액세스 기술에 종속되어버림 
>   - 여러 기술 사용법의 공통점이 있다면 이를 '추상화' 하는 것은 좋은 접근 방법
>   - 추상화란 하위 시스템의 공통적인 부분을 뽑아내서 분리하여 일관되게 사용하도록 만드는 것 
> - 스프링은 트랜잭션 기술의 공통점을 담은 트랜잭션 추상화 기술을 제공함 
> - <img src="/images/트랜잭션추상화계층.png" width="400" height="400"/>


<br>

#### 👉 트랜잭션 기술 설정의 분리

> - 각 기술마다 PlatformTransactionManager 구현체가 다름
>   - JDBC -> DataSourceTxManager
>   - JTA -> JtaxManager
>   - Hibernate -> HibernateTxManager
> - 어떤 트랜잭션 매니저 구현체를 사용할지는 스프링 DI 방식으로 처리되야함
>   - UserService가 자신이 사용하는 구현체를 알고있는 것은 DI 원칙 위배


```java

public class UserService {
	public static final int MIN_LOGCOUNT_FOR_SILVER = 50;
	public static final int MIN_RECCOMEND_FOR_GOLD = 30;

	private UserDao userDao;
	private PlatformTransactionManager transactionManager;

	public void setUserDao(UserDao userDao) {
		this.userDao = userDao;
	}
    
	public void setTransactionManager(PlatformTransactionManager transactionManager) {
		this.transactionManager = transactionManager;
	}

	public void upgradeLevels() {
		TransactionStatus status = 
			this.transactionManager.getTransaction(new DefaultTransactionDefinition());
		try {
			List<User> users = userDao.getAll();
			for (User user : users) {
				if (canUpgradeLevel(user)) {
					upgradeLevel(user);
				}
			}
			this.transactionManager.commit(status);
		} catch (RuntimeException e) {
			this.transactionManager.rollback(status);
			throw e;
		}
	}
	
	private boolean canUpgradeLevel(User user) {
		Level currentLevel = user.getLevel(); 
		switch(currentLevel) {                                   
		case BASIC: return (user.getLogin() >= MIN_LOGCOUNT_FOR_SILVER); 
		case SILVER: return (user.getRecommend() >= MIN_RECCOMEND_FOR_GOLD);
		case GOLD: return false;
		default: throw new IllegalArgumentException("Unknown Level: " + currentLevel); 
		}
	}

	protected void upgradeLevel(User user) {
		user.upgradeLevel();
		userDao.update(user);
		sendUpgradeEMail(user);
	}
    
	
	public void add(User user) {
		if (user.getLevel() == null) user.setLevel(Level.BASIC);
		userDao.add(user);
	}
}

```

<br>

#### 👉 서비스 추상화와 단일 책임 원칙(SRP)

> - <img src="/images/계층과책임의분리.png" width="400" height="400"/>
> - UserDao와 UserService는 인터페이스와 DI를 통해 연결됨으로써 결합도가 낮아짐. 결합도가 낮다는 것은 데이터 액세스 로직이 바뀌거나, 심지어 데이터 액세스 기술이 바뀐다고 할지라도 UserService의 코드에는 영향을 미치지 않음. 즉, 서로 독립적으로 확장될 수 있음
> - 애플리케이션 로직의 종류에 따른 수평적인 구분이든, 로직과 기술이라는 수직적인 구분이든 모두 결합도가 낮으며, 서로 영향을 주지 않고 자유롭게 확장될 수 있는 구조를 만들 수 있는데는 스프링의 DI가 중요한 역할을 하고 있음
> - DI의 가치는 이렇게 관심, 책임, 성격이 다른 코드를 깔끔하게 분리하는 데 있음

<br>

#### 👉 단일 책임 원칙(SRP)

> - 단일 책임 원칙(SRP) : 하나의 모듈은 한 가지 책임을 가져야함. 하나의 모듈이 바뀌는 이유는 한 가지여야함을 보장
>   - 변경이 발생했을 때 변경 대상이 명확해짐
>   - 기술적인 수정사항에도 마찬가지로 적용되는 효과 
> - 책임과 관심이 다른 코드를 분리하고 서로 영향을 주지 않도록 다양한 추상화 기법을 도입하고, 애플리케이션 로직과 기술/환경을 분리하는 등의 작업은 갈수록 복잡해지는 엔터프라이즈 애플리케이션에서는 반드시 필요함. 이를 스프링에서는 DI를 통해 지원함
> - 단일 책임 원칙을 잘 지키는 코드를 만들려면 인터페이스를 도입하고 이를 DI로 연결해야함. 그 결과로 단일 책임 뿐만아니라 개방 폐쇄 원칙도 충족함
> - 또한, 모듈 간에 결합도가 낮아서 서로의 변경이 영향을 주지 않고 같은 이유로 변경이 단일 책임에 집중되는 응집도 높은 코드를 작성할 수 있음 


<br>

#### 👉 메일 서비스 추상화 

> - 추가 요구 사항 정의 : '레벨이 업그레이드되는 사용자에게는 안내 메일을 발송함'
> - 자바에서는 메일 발송할 때 JavaMail을 사용함. 밑에는 전형적인 자바로 메일 보내는 코드 

```java

private void sendUpgradeEMail(User user) {
    Prorperties props = new Properties();
    props.put("mail.smtp.host", "mail.ksug.org");
    Session s = Session.getInstance(props, null);
    
    MimeMessage message = new MimeMessage(s);
    try {
        message.setFrom(new InternetAddress("useradmin@ksug.org"));
        message.addRecipient(Message.RecipientType.TO, new InternetAddress(user.getEmail()));
        message.setSubject("Upgrade 안내");
        message.setText("사용자님의 등급이 " + user.getLevel().name() + "로 업그레이드되었습니다");
        
        Transport.send(message);
    } catch (AddressException e) {
        throw new RuntimeException(e);
    } catch (MessagingException e) {
        throw new RuntimeException(e);
    } catch (UnsupportedEncodingException e) {
        throw new RuntimeException(e);
    }
}
```

<br>

#### 👉 JavaMail이 포함된 코드의 테스트

> - JavaMail을 사용한 코드는 테스트하기 어려움
> - 테스트를 실행했는데 만약 메일 서버가 준비되어 있지 않았다면 예외가 발생하면서 테스트가 실패함
> - 그렇다고해서 테스트를 하면서 매번 메일 서버를 연결하여 메일이 발송되는 것은 바람직한 방법이아님
> - 그래서, 실제 DB 대신에 테스트 DB를 사용하듯이 테스트 때는 메일 서버 설정을 다르게 해서 테스트용 메일 서버를 이용하는 것이 좋음


<br>

#### 👉 JavaMail은 테스트 하기 어려운 대표젹인 API

> - JavaMail은 테스트하기 어려운 대표적인 API임. JavaMail의 핵심 API에는 DataSource 처럼 인터페이스로 만들어져서 구현을 바꿀 수 없기 때문임
> - 그렇기에 인터페이스를 통해 테스트 대역을 만들어서 테스트를 진행하는 방식을 적용할 수 없음

<br>

#### 👉 스프링의 메일 서비스 추상화 -> MailSender

> - 스프링은 위와 같은 문제를 해결하고자 MailSender라는 인터페이스를 제공함
> - 이를 통해 테스트 대역인 DummyMailSender를 만들어서 테스트를 진행할 수 있음
> - <img src="/images/유저메일기능테스트구성.jpeg" width="400" height="400"/>


<br>

#### 👉 테스트 대역의 종류와 특징

> - 테스트 대역
>   - 테스트 환경을 만들어 구성하기 위해, 테스트 대상이되는 오브젝트의 기능에만 충실하게 수행하면서 빠르고 여러번 테스트를 실행할 수 있도록 사용하는 오브젝트
> - 테스트 스텁
>   - 테스트 대상의 의존 오브젝트로서 존재하면서 테스트 수행 중에 코드가 정상 수행할 수 있도록 돕는 것 
> - 목 오브젝트
>   - 테스트 대상 오브젝트와 의존 오브젝트 사이에 일어나는 일을 검증할 수 있도록 특별히 설계된 오브젝트
>   - 목 오브젝트는 스텁처럼 테스트 오브젝트가 정상적으로 실행되도록 도와주면서 테스트 오브젝트와 자신의 사이에서 일어나는 커뮤니케이션 내용을 저장해뒀다가 테스트 결과를 검증하는데 활용할 수 있게 해줌
> - <img src="/images/목오브젝트작동원리.jpeg" width="400" height="400"/>

```java
// 테스트 대역 정의 
public class DummyMailSender implements MailSender {
    public void send(SimpleMailMessage mailMessage) throws MailException {
    }

    public void send(SimpleMailMessage[] mailMessage) throws MailException {
    }
}




@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations="/test-applicationContext.xml")
public class UserServiceTest {
	@Autowired UserService userService;	
	@Autowired UserDao userDao;
	@Autowired MailSender mailSender; 
	@Autowired PlatformTransactionManager transactionManager;
	
	List<User> users;	// 테스트 픽스쳐 
	
	@Before
	public void setUp() {
		users = Arrays.asList(
				new User("bumjin", "박범진", "p1", "user1@ksug.org", Level.BASIC, MIN_LOGCOUNT_FOR_SILVER-1, 0),
				new User("joytouch", "강명성", "p2", "user2@ksug.org", Level.BASIC, MIN_LOGCOUNT_FOR_SILVER, 0),
				new User("erwins", "신승한", "p3", "user3@ksug.org", Level.SILVER, 60, MIN_RECCOMEND_FOR_GOLD-1),
				new User("madnite1", "이상호", "p4", "user4@ksug.org", Level.SILVER, 60, MIN_RECCOMEND_FOR_GOLD),
				new User("green", "오민규", "p5", "user5@ksug.org", Level.GOLD, 100, Integer.MAX_VALUE)
				);
	}

	@Test 
    @DirtiesContext // 테스트 컨텍스트가 변경되는 것을 알림
	public void upgradeLevels() {
		userDao.deleteAll();
		for(User user : users) userDao.add(user);
		
		MockMailSender mockMailSender = new MockMailSender();  
		userService.setMailSender(mockMailSender);  
		
		userService.upgradeLevels();
		
		checkLevelUpgraded(users.get(0), false);
		checkLevelUpgraded(users.get(1), true);
		checkLevelUpgraded(users.get(2), false);
		checkLevelUpgraded(users.get(3), true);
		checkLevelUpgraded(users.get(4), false);
		
		List<String> request = mockMailSender.getRequests();  
		assertThat(request.size(), is(2));  
		assertThat(request.get(0), is(users.get(1).getEmail()));  
		assertThat(request.get(1), is(users.get(3).getEmail()));  
	}
	
    // 목 오브젝트 정의 
	static class MockMailSender implements MailSender {
        // 커뮤니케이션 내용을 저장해둠 
		private List<String> requests = new ArrayList<String>();	
		
		public List<String> getRequests() {
			return requests;
		}

		public void send(SimpleMailMessage mailMessage) throws MailException {
			requests.add(mailMessage.getTo()[0]);  
		}

		public void send(SimpleMailMessage[] mailMessage) throws MailException {
		}
	}


	private void checkLevelUpgraded(User user, boolean upgraded) {
		User userUpdate = userDao.get(user.getId());
		if (upgraded) {
			assertThat(userUpdate.getLevel(), is(user.getLevel().nextLevel()));
		}
		else {
			assertThat(userUpdate.getLevel(), is(user.getLevel()));
		}
	}

	@Test 
	public void add() {
		userDao.deleteAll();
		
		User userWithLevel = users.get(4);	  // GOLD 레벨  
		User userWithoutLevel = users.get(0);  
		userWithoutLevel.setLevel(null);
		
		userService.add(userWithLevel);	  
		userService.add(userWithoutLevel);
		
		User userWithLevelRead = userDao.get(userWithLevel.getId());
		User userWithoutLevelRead = userDao.get(userWithoutLevel.getId());
		
		assertThat(userWithLevelRead.getLevel(), is(userWithLevel.getLevel())); 
		assertThat(userWithoutLevelRead.getLevel(), is(Level.BASIC));
	}
 
	@Test
	public void upgradeAllOrNothing() {
		UserService testUserService = new TestUserService(users.get(3).getId());  
		testUserService.setUserDao(this.userDao);
		testUserService.setTransactionManager(this.transactionManager);
		testUserService.setMailSender(this.mailSender);
		 
		userDao.deleteAll();			  
		for(User user : users) userDao.add(user);
		
		try {
			testUserService.upgradeLevels();   
			fail("TestUserServiceException expected"); 
		}
		catch(TestUserServiceException e) { 
		}
		
		checkLevelUpgraded(users.get(1), false);
	}

	
	static class TestUserService extends UserService {
		private String id;
		
		private TestUserService(String id) {  
			this.id = id;
		}

		protected void upgradeLevel(User user) {
			if (user.getId().equals(this.id)) throw new TestUserServiceException();  
			super.upgradeLevel(user);  
		}
	}
	
	static class TestUserServiceException extends RuntimeException {
	}



}
```

## 📌 06. AOP

#### 🧑🏻‍🏫 주요 내용 작성

<img src="" width="800" height="500"/>

#### 👉 AOP에 대한 간단한 소개
> - 스프링의 3대 기반 기술은 IoC/DI, 서비스 추상화, AOP임
> - AOP는 Aspect Oriented Programming의 약자로, 관점 지향 프로그래밍이라고 함
> - AOP는 OOP의 한계를 극복하기 위해 나온 개념으로, OOP는 객체의 기능을 중심으로 모듈화를 하지만, AOP는 횡단 관심사를 중심으로 모듈화함


<br>

#### 👉 AOP로 트랜잭션 코드 분리
> - 트랜잭션 경계설정 기능을 AOP를 통해 해결하고자함
> - 앞서 서비스 추상화를 통해 트랜잭션, 메일 발송 기술 등에 종속적인지 않은 비즈니스 로직을 만듦
> - 하지만, 트랜잭션 경계설정을 위해 비즈니스 로직에는 트랜잭션 경계설정 코드가 들어가 있음
> - 즉, 문제는 'UserService 코드를 보면, 비즈니스 로직 코드를 사이에 두고 트랜잭션 시작과 종료를 담당하는 코드가 앞뒤에 위치하고 있음'
> - 밑에 코드는 서로 다른 성격의 코드가 혼재되어 있음 - 트랜잭션 경계설정, 비즈니스 로직 
> - 이 두가지 코드는 성격이 다를 뿐 아니라 서로 주고 받는 것도 없는 독립적인 코드 
>   - 트랜잭션 경계설정 코드를 클래스 밖으로 분리해야함 

```java

public class UserService {
    public void upgradeLevels() {
        // (1) 트랜잭션 경계설정 코드 <- 외부로 분리해낼 코드 
        TransactionStatus status = 
            this.transactionManager.getTransaction(new DefaultTransactionDefinition());
        
        try {
            
            // (2) 비즈니스 로직 
            List<User> users = userDao.getAll();
            for (User user : users) {
                if (canUpgradeLevel(user)) {
                    upgradeLevel(user);
                }
            }
            
            // (1) 트랜잭션 경계설정 코드 - 커밋 <- 외부로 분리해낼 코드 
            this.transactionManager.commit(status);
        } catch (RuntimeException e) {
            // (1) 트랜잭션 경계설정 코드 - 롤백 <- 외부로 분리해낼 코드 
            this.transactionManager.rollback(status);
            throw e;
        }
    }
}

```

<br>

#### 👉 DI 적용을 이용한 트랜잭션 분리

> - DI는 실제 사용할 오브젝트의 클래스 정체를 감춘채 인터페이스를 통해 간접적으로 접근하는 것이 핵심 아이디어임
> - 우리가 하고자 하는 것은 'UserService에는 순수하게 비즈니스 로직을 담고 있는 코드만 놔두고 트랜잭션 경계설정을 담당하는 코드를 외부로 분리하는 것'
> - 이에 적합한 디자인 패턴이 있음. 바로 '데코레이터 패턴임'

<br>

#### 👉 분리된 트랜잭션 기능

```java
// 인터페이스 정의
public interface UserService {
	void add(User user);
	void upgradeLevels();
}

// UserServiceImpl 클래스, 비즈니스 로직을 담당하는 클래스 - 알맹이 
public class UserServiceImpl implements UserService {
    public static final int MIN_LOGCOUNT_FOR_SILVER = 50;
    public static final int MIN_RECCOMEND_FOR_GOLD = 30;

    private UserDao userDao;
    private MailSender mailSender;

    public void setUserDao(UserDao userDao) {
        this.userDao = userDao;
    }

    public void setMailSender(MailSender mailSender) {
        this.mailSender = mailSender;
    }

    public void upgradeLevels() {
        List<User> users = userDao.getAll();
        for (User user : users) {
            if (canUpgradeLevel(user)) {
                upgradeLevel(user);
            }
        }
    }

    private boolean canUpgradeLevel(User user) {
        Level currentLevel = user.getLevel();
        switch(currentLevel) {
            case BASIC: return (user.getLogin() >= MIN_LOGCOUNT_FOR_SILVER);
            case SILVER: return (user.getRecommend() >= MIN_RECCOMEND_FOR_GOLD);
            case GOLD: return false;
            default: throw new IllegalArgumentException("Unknown Level: " + currentLevel);
        }
    }

    protected void upgradeLevel(User user) {
        user.upgradeLevel();
        userDao.update(user);
        sendUpgradeEMail(user);
    }

    private void sendUpgradeEMail(User user) {
        SimpleMailMessage mailMessage = new SimpleMailMessage();
        mailMessage.setTo(user.getEmail());
        mailMessage.setFrom("useradmin@ksug.org");
        mailMessage.setSubject("Upgrade ¾È³»");
        mailMessage.setText("»ç¿ëÀÚ´ÔÀÇ µî±ÞÀÌ " + user.getLevel().name());

        this.mailSender.send(mailMessage);
    }

    public void add(User user) {
        if (user.getLevel() == null) user.setLevel(Level.BASIC);
        userDao.add(user);
    }
}

// 데코레이터 패턴을 적용한 트랜잭션 기능을 담당하는 UserServiceTx 클래스 - 껍데기 
public class UserServiceTx implements UserService {
    UserService userService;
    PlatformTransactionManager transactionManager;

    public void setTransactionManager(
            PlatformTransactionManager transactionManager) {
        this.transactionManager = transactionManager;
    }

    public void setUserService(UserService userService) {
        this.userService = userService;
    }

    public void add(User user) {
        this.userService.add(user);
    }

    public void upgradeLevels() {
        TransactionStatus status = this.transactionManager
                .getTransaction(new DefaultTransactionDefinition());
        try {
            userService.upgradeLevels();
            this.transactionManager.commit(status);
        } catch (RuntimeException e) {
            this.transactionManager.rollback(status);
            throw e;
        }
    }
}



```

> - 순수 비즈니스 로직을 처리하는 UserServiceImpl과 트랜잭션 처리를 담은 UserServiceTx 클래스를 만듦. 이를 데코레이터 패턴으로 구성함
> - <img src="/images/데코레이터패턴.jpeg" height="400" width="400">
> - 위의 구조를 DI를 적용하여 런타임 시점에 밑에와 같이 구성함 
> - <img src="/images/런타임오브젝트의존관계(AOP).jpeg" height="400" width="400">


<br>

#### 👉 고립된 단위 테스트

> - 단위 테스트는 '가능한 한 작은 단위로 쪼개서 테스트 하는 것'이 중요함
>   - (1) 실패 원인을 쉽고 빠르게 파악할 수 있음
>   - (2) 테스트의 의도, 내용이 분명해지고 만들기 쉬움
> - 현재 UserService는 UserDao, DsTransactionManager, JavaMailSenderImpl에 의존하고 있음. 총 3가지 의존 오브젝트가 존재함
> - 위의 의존 오브젝트로부터 자유롭게 구성시켜(독립시켜) 해당 테스트 대상인 UserService에 대해서만(비즈니스 로직에 대해서만) 테스트 할 수 있게 구성해야함

<br>

#### 👉 테스트 대상 오브젝트 고립시키기

> - <img src="/images/고립시킨UserServiceImpl테스트구조.jpeg" height="400" width="400">
> - 테스트 대상이 환경이나, 외부 서버, 다른 클래스의 코드에 종속되고 영향을 받지 않도록 고립시켜야함
>   - 테스트를 위한 대역(스텁)
>   - 목 오브젝트

<br>

#### 👉 단위 테스트와 통합 테스트

> - 단위 테스트는 절대적인 기준은 없음. 다만, 하나의 단위에 초점을 맞춘 테스트를 의미함
> - 통합 테스트는 두 개 이상의 성격이나 계층이 다른 오브젝트가 연동하도록 만들어 테스트 하거나 외부의 DB나 파일 서비스 등의 리소스가 참여하는 테스트를 의미함

<br>

#### 👉 목 프레임워크


> - 단위 테스트 작성시 스텁이나 목 오브젝트의 사용이 필수적임
> - Mockito 프레임워크, 해당 프레임워크를 사용하면 간단한 메서드 호출만으로 다이나믹하게 특정 인터페이스를 구현한 테스트용 오브젝트를 만들 수 있음
> - Mocktio 목 오브젝트 사용 과정
>   - (1) 인터페이스를 통해 목 오브젝트 생성
>   - (2) 예외나 리턴 값이 있으면 지정해줌
>   - (3) 테스트 대상 오브젝트에 DI해서 테스트 중에 목 오브젝트를 사용하도록 만듦
>   - (4) 테스트 대상 오브젝트를 사용한 후, 목 오브젝트의 특정 메서드가 호출됐는지, 어떤 값을 가지고 몇 번 호출했는지 검증함

<br>

#### 👉 다이내믹 프록시와 팩토리 빈
> - 프록시와 프록시 패턴, 데코레이터 패턴에 대해 학습할 계획임
> - 앞서 DI와 전략, 브릿지 패턴을 통해 오브젝트를 기능 단위로 분리함으로써 OCP, SRP를 충족시켜옴
> - 하지만, 트랜잭션을 적용하는 로직은 그대로 방치되어 있음
> - 이를 분리해야함. 부가기능(트랜잭션 관련 로직)과 핵심 기능(비즈니스 로직)을 분리해야함
>   - 부가기능을 담당하는 클래스는 부가기능 이외의 나머지 모든 기능은 핵심기능을 담당하는 클래스로 위임해야함
>   - 핵심 기능을 담당하는 클래스는 부가기능 클래스 존재 자체를 모름
>   - 클라이언트는 인터페이스를 통해 핵심기능을 사용하게 만들고 부가기능 자신도 같은 인터페이스를 구현한 뒤 자신이 그 사이에 끼어들어가게 만들어야함 
> - <img src="/images/핵심기능인터페이스의적용.jpeg" height="400" width="400">
> - 이와 관련된 디자인 패턴으로는 '데코레이터 패턴'과 '프록시 패턴'이 있음

<br>

#### 👉 프록시
> - 프록시는 프록시 패턴과 다른 개념임 
> - 프록시란? 클라이언트와 사용 대상 사이에 대리 역할을 맡은 오브젝트를 두는 방식
> - 자신이 클라이언트가 사용하려고 하는 실제 대상인 것 처럼 위장해서 클라이언트의 요청을 받아주는 것을 의미함
> - 프록시를 통해 최종적으로 요청을 위임 받아 처리하는 실제 오브젝트를 '타깃'이라고함
> - <img src="/images/핵심기능인터페이스의적용.jpeg" height="400" width="400">
> - 프록시의 특징은 타깃과 같은 인터페이스를 구현했고 프록시가 타깃을 제어할 수 있는 위치에 있다는 것임
> - 프록시를 사용하는 이유는 다음과 같음
>   - (1) 클라이언트가 타깃에 접근하는 방법을 제어하기 위함
>   - (2) 타깃에 부가적인 기능을 부여하기 위함


<br>

#### 👉 데코레이터 패턴 

> - 타깃에 부가적인 기능을 런타임시 다이나믹하게 부여하기 위해 프록시를 사용하는 패턴
> - 데코레이터 패턴의 특징은 여러개의 프록시를 설정할 수 있음
>   - 자바의 I/O 패키지에서는 데코레이터 패턴을 사용함
> - <img src="/images/데코레이터패턴적용예시.jpeg" height="400" width="400">
> - 데코레이터 패턴은 타깃의 코드를 손대지 않고 클라이언트가 호출하는 방법을 변경하지 않은 채로 새로운 기능을 추가할 때 유용함 

<br>

#### 👉 프록시 패턴 

> - 프록시를 사용하는 방법 중에서 타깃에 대한 접근 방법을 제어하려는 목적을 가진 패턴
> - 프록시 패턴의 프록시는 타깃의 기능을 확장하거나 추가하지 않음, 대신에 클라이언트가 타깃에 접근하는 방식을 변경해줌
> - 타깃 오브젝트를 생성하기가 복잡하거나 당장 필요하지 않은 경우에는 꼭 필요한 시점까지 오브젝트 생성을 딜레이시키는 것이 좋음. 그런데, 오브젝트에 대한 래퍼런스가 미리 필요할 때 해당 패턴이 유용함
> - 클라이언트가 프록시의 메서드를 통해 타깃을 사용하려고 할 때, 프록시가 타깃 오브젝트를 생성하고 요청을 위임해주는 방식임
> - 프록시 패턴은 타깃 기능 자체에는 관여하지 않으면서 접근하는 방법을 제어해주는 프록시를 이용함
> - 따라서, 프록시 패턴과 데코레이터 패턴을 적절히 혼용해서 사용하기도함 
> - <img src="/images/프록시패턴과데코레이터패턴혼용.jpeg" height="400" width="400">

<br>

#### 👉 다이나믹 프록시

> - 프록시를 동적(다이나믹하게)으로 생성하는 것을 의미함
> - 프록시 자체는 기존 코드에 영향을 주지 않으면서 타깃의 기능을 확장하거나 접근 방법을 제어할 수 있는 유용한 방식임
> - 프록시 자체를 클래스로 정의하고 관계설정하는 작업은 상당히 복잡함. 실제 디자인 패턴을 구현하고 의존관계 설정하는 것은 번거로움
> - java.lang.reflect (리플렉션 API) 를 통해 이를 해소함. 일일이 프록시 클래스를 정의하지 않고도 몇 가지 API를 이용하여 프록시처럼 동작하는 오브젝트를 동적으로 생성해줌
> - 프록시는 주로 2가지 기능으로 구성됨
>   - (1) 타깃과 같은 메서드를 구현하고 있다가 메서드가 호출되면 타깃 오브젝트로 위임함
>   - (2) 지정된 요청에 대해서는 부가기능을 수행함
> - 즉, 프록시의 역할은 '위임'과 '부가작업'으로 구분할 수 있음
> - 하지만, 프록시를 직접 만들어서 사용하면 다음과 같은 문제가 발생함
>   - (1) 타깃의 인터페이스를 구현하고 위임하는 코드를 작성해야함. 매우 번거로운 작업
>   - (2) 부가기능 코드가 중복될 가능성이 높음

<br>

#### 👉 리플렉션 API

> - 위에서 겪은 문제를 '리플렉션 API'를 통해 해소할 수 있음
> - 즉, JDK의 다이나믹 프록시를 사용하면 프록시를 직접 구현하지 않아도됨
> - 다이나믹 프록시는 리플렉션 기능을 통해 프록시를 생성함 
> - 리플렉션은 자바의 코드 자체를 추상화해서 접근하도록 만든 것
> - 자바의 모든 클래스는 설계도 객체가 있음(Class 타입 오브젝트)
> - 설계도 객체를 이용하면 클래스 코드에 대한 메타정보를 가져오거나 오브젝틀를 조작할 수 있음
> - 리플렉션 API 중에서 메서드에 대한 정의를 담은 Method라는 인터페이스를 이용해 메서드를 호출할 수 있음
> - java.lang.reflect.Method 인터페이스는 메서드에 대한 메타 정보와 이를 통해 특정 오브젝트의 메서드를 실행할 수 있음(invoke(obj, args)를 호출하면됨)

<br>

#### 👉 다이나믹 프록시 동작방법

```java

// InvocationHandler를 구현한 클래스
public class UppercaseHandler implements InvocationHandler {
    Object target;

    private UppercaseHandler(Object target) {
        this.target = target;
    }

    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        String ret = (String) method.invoke(target, args);
        return ret.toUpperCase();
    }
}

// 프록시 생성
/**
 * - 동적으로 생성되는 다이나믹 프록시 클래스의 로딩에 사용할 클래스 로더가 필요함
 * - 다이나믹 프록시 클래스가 구현해야할 인터페이스가 필요함
 * - 부가기능과 위임 코드를 담은 InvocationHandler 구현 오브젝트가 필요함
 */
Hello proxiedHello = (Hello) Proxy.newProxyInstance(
    getClass().getClassLoader(),
    new Class[] { Hello.class },
    new UppercaseHandler(new HelloTarget())
);

```

> - <img src="/images/다이나믹프록시동작방식.jpeg" height="400" width="400">
> - 다이나믹 프록시는 프록시 팩토리에 의해 런타임시 동적으로 만들어지는 오브젝트를 지칭함
> - 다이나믹 프록시가 인터페이스 구현 클래스 오브젝트를 만들어주지만, 프록시로서 필요한 부가기능 로직은 직접 작성해야함
> - 부가기능은 프록시 오브젝트와 독립적으로 InvocationHandler를 구현한 오브젝트에서 관리함
> - 다이나믹 프록시 오브젝트는 클라이언트의 모든 요청을 리플렉션 정보로 변환해서 InvocationHanler 구현 오브젝트의 invoke()에 전달함
> - 타깃 인터페이스의 모든 요청이 하나의 메서드로 집중되기 때문에 중복되는 기능을효과적으로 제공할 수 있음


<br>

#### 👉 다이나믹 프록시를 이용한 트랜잭션 부가기능

```java
// 트랜잭션 InvocationHandler
public class TransactionHandler implements InvocationHandler {
    Object target;
    PlatformTransactionManager transactionManager;
    String pattern;

    public void setTarget(Object target) {
        this.target = target;
    }

    public void setTransactionManager(
            PlatformTransactionManager transactionManager) {
        this.transactionManager = transactionManager;
    }

    public void setPattern(String pattern) {
        this.pattern = pattern;
    }

    public Object invoke(Object proxy, Method method, Object[] args)
            throws Throwable {
        if (method.getName().startsWith(pattern)) {
            return invokeInTransaction(method, args);
        } else {
            return method.invoke(target, args);
        }
    }

    private Object invokeInTransaction(Method method, Object[] args)
            throws Throwable {
        TransactionStatus status = this.transactionManager
                .getTransaction(new DefaultTransactionDefinition());
        try {
            Object ret = method.invoke(target, args);
            this.transactionManager.commit(status);
            return ret;
        } catch (InvocationTargetException e) {
            this.transactionManager.rollback(status);
            throw e.getTargetException();
        }
    }
}

```

> - 트랜잭션 부가기능을 제공하는 다이나믹 프록시를 만들어 적용하는 방법이 가장 효과적임
> - 트랜잭션 InvocationHandler를 만들어서 트랜잭션 부가기능을 제공하는 다이나믹 프록시를 만들어 적용함
> - 타깃 오브젝트의 모든 메서드에 트랜잭션을 적용하는 것이 아닌 선별적으로 적용하는 것
>   - 적용할 대상을 선별해야함. 패턴이 일치여부로 판단함


<br>

#### 👉 다이나믹 프록시를 위한 팩토리빈

> - 스프링은 내부적으로 리플렉션 API를 이용해서 빈 정의에 나오는 클래스 이름을 가지고 빈 오브젝트를 생성함
> - 다이나믹 프록시 오브젝트는 위와 같은 방식으로 프록시 오브젝트가 생성되지 않음. 해당 클래스 자체도 내부적으로 다이나믹하게 새로 정의해서 사용하기 때문
> - 사전에 프록시 오브젝트의 클래스 정보를 미리 알아내서 스프링의 빈에 정의할 수 없음

<br>

#### 👉 팩토리 빈

> - 팩토리 빈이란? 스프링을 대신해서 오브젝트의 생성 로직을 담당하도록 만들어진 특별한 빈
> - 스프링의 FactoryBean 인터페이스를 구현해서 사용할 수 있음
> - 팩토리 빈은 팩토리 메서드를 가진 오브젝트를 말함
> - 팩토리 빈 클래스의 오브젝트가 getObject() 메서드를 이용해 오브젝트를 가져오고 이를 빈 오브젝트로 사용함

<br>

#### 👉 다이나믹 프록시를 만들어주는 팩토리 빈

```java
// 트랜잭션 InvocationHandler
public class TransactionHandler implements InvocationHandler {
    Object target;
    PlatformTransactionManager transactionManager;
    String pattern;

    public void setTarget(Object target) {
        this.target = target;
    }

    public void setTransactionManager(
            PlatformTransactionManager transactionManager) {
        this.transactionManager = transactionManager;
    }

    public void setPattern(String pattern) {
        this.pattern = pattern;
    }

    public Object invoke(Object proxy, Method method, Object[] args)
            throws Throwable {
        if (method.getName().startsWith(pattern)) {
            return invokeInTransaction(method, args);
        } else {
            return method.invoke(target, args);
        }
    }

    private Object invokeInTransaction(Method method, Object[] args)
            throws Throwable {
        TransactionStatus status = this.transactionManager
                .getTransaction(new DefaultTransactionDefinition());
        try {
            Object ret = method.invoke(target, args);
            this.transactionManager.commit(status);
            return ret;
        } catch (InvocationTargetException e) {
            this.transactionManager.rollback(status);
            throw e.getTargetException();
        }
    }
}

// 프록시 팩토리 빈
public class TxProxyFactoryBean implements FactoryBean<Object> {
    // TransactionHanlder를 생성할 때 필요한 정보
    Object target;
    PlatformTransactionManager transactionManager;
    String pattern;
    
    // 다이나믹 프록시를 사용할 때 필요함. 범용적으로 인터페이스를 가진 타깃에도 적용 
    Class<?> serviceInterface;

    public void setTarget(Object target) {
        this.target = target;
    }

    public void setTransactionManager(PlatformTransactionManager transactionManager) {
        this.transactionManager = transactionManager;
    }

    public void setPattern(String pattern) {
        this.pattern = pattern;
    }

    public void setServiceInterface(Class<?> serviceInterface) {
        this.serviceInterface = serviceInterface;
    }
    
    // FactoryBean 인터페이스 구현 메서드
    public Object getObject() throws Exception {
        // DI 받은 정보를 활용해서 TransactionHandler를 생성하고 다이나믹 프록시를 생성함
        TransactionHandler txHandler = new TransactionHandler();
        txHandler.setTarget(target);
        txHandler.setTransactionManager(transactionManager);
        txHandler.setPattern(pattern);
        return Proxy.newProxyInstance(
                getClass().getClassLoader(),new Class[] { serviceInterface }, txHandler);
    }

    public Class<?> getObjectType() {
        return serviceInterface;
    }

    public boolean isSingleton() {
        return false;
    }
}
```

> - 팩토리 빈을 통해 다이나믹 프록시 오브젝트를 스프링 빈으로 만들 수 있음
> - <img src="/images/팩토리빈을이용한트랜잭션다이나믹프록시의적용.jpeg" width="400" height="400">


<br>

#### 👉 프록시 팩토리 빈 방식의 장점과 한계

> - 프록시 팩토리 빈의 재사용. 단순하게 스프링 설정만 변경해도 '다이나믹 프록시 생성'하는 과정 자체를 재활용할 수 있음
> - 프록시 팩토리 빈은 밑에 2가지 문제를 해결해줌
>   - (1) 타깃 인터페이스를 구현하는 프록시 클래스를 일일이 만들고 관리해야하는 번거로움
>   - (2) 부가적인 기능이 여러 메서드에 반복적으로 나타나게 돼서 코드 중복의 문제가 발생하는 것
> - 프록시 팩토리 빈에는 다음과 같은 한계가 있음
>   - (1) 한번에 여러 개의 클래스에 공통적인 부가기능을 제공하는 작업을 할 수 없음
>   - (2) 하나의 타깃에 여러 개의 부가기능을 적용하기 어려운 구조
>   - (3) TransactionHandler 오브젝트가 프록시 팩토리 빈 개수만큼 만들어짐
>     - 트랜잭션 부가기능을 제공하는 동일한 코드임에도 불구하고 타깃 오브젝트가 달라지면 새로운 TransactionHandler 오브젝트를 만들어야함


<br>

#### 👉 스프링의 프록시 팩토리 빈

> - 스프링은 프록시 기술에 서비스 추상화를 적용함. 즉, 스프링은 일관된 방법으로 프록시를 만들 수 있게 도와주는 추상 레이어를 제공함
> - 스프링은 프록시 오브젝트를 생성해주는 기술을 추상화한 팩토리 빈을 제공함
> - 스프링의 ProxyFactoryBean은 프록시를 생성해서 빈 오브젝트로 등록해주는 팩토리 빈임
> - 프록시에서 사용할 부가기능은 MethodInterceptor 인터페이스를 구현한 클래스로 만들어서 DI로 주입함
> - MethodInterceptor의 invoke()는 ProxyFactoryBean으로부터 타깃에 대한 정보까지 함께 제공받음
> - MethodInterceptor는 타깃에 상관없이 독립적으로 구성할 수 있음. 그래서 타깃이 다른 여러 프록시에서 함께 사용할 수 있고 싱글톤 빈으로 등록 가능함


<br>

#### 👉 어드바이스 : 타깃이 필요없는 순수한 부가기능

> - MethodInvocation은 일종의 콜백. proceed()를 실행하면 타깃의 메서드를 내부적으로 실행해주는 기능이 있음. 그렇다면 MethodInvocation 구현 클래스는 일종의 공유 가능한 템플릿 처럼 동작함 
> - ProxyFactoryBean은 작은 단위의 템플릿/콜백 구조를 응용해서 적용했기 때문에 템플릿 역할을 하는 MethodInvocation을 싱글톤으로 두고 공유할 수 있음
> - MethodInterceptor처럼 타깃 오브젝트에 적용하는 부가기능을 담은 오브젝트를 스프링에서는 '어드바이스'라고함 
> - ProxyFactoryBean에 있는 인터페이스 자동 검출 기능을 통해 타깃이 구현하고 있는 인터페이스를 알아내고 해당 인터페이스를 구현한 프록시를 생성함
> - 어드바이스는 '타깃 오브젝트에 종속되지 않는 순수한 부가기능을 담은 오브젝트'를 의미함

<br>

#### 👉 포인트 컷 : 부가기능 적용 대상 메서드 선정 방법

> - <img src="/images/다이나믹프록시적용방식비교.jpeg" height="400" width="400">
> - 메서드의 이름을 가지고 부가기능을 적용할 대상 메서드를 선정하는 것
> - 트랜잭션 적용 메서드 패턴은 프록시마다 다를 수 있기 때문에 여러 프록시가 공유하는 MethodInterceptor에 특정 프록시에만 적용되는 패턴을 넣으면 안됨
> - MethodInterceptor에는 재사용 가능한 순수한 부가기능 제공 코드만 남기고 프록시에 부가기능 적용 메서드를 선택하는 기능을 넣음
> - 기존의 JDK 다이나믹 프록시를 이용한 방식은 OCP를 충족시키지 못한 구조임. 이를 발전시킨 버전이 스프링의 ProxyFactoryBean임
> - 스프링은 부가기능을 제공하는 오브젝트를 '어드바이스'라고 하고 어드바이스를 적용할 메서드를 선정하는 방법을 '포인트 컷'이라고 함
> - 어드바이스와 포인트 컷은 모두 프록시에 DI로 주입돼서 사용됨. 어드바이스와 포인트 컷 모두 프록시에서 공유 가능하도록 싱글톤 빈으로 등록됨
> - 재사용 가능한 기능을 만들어 두고 변경되는 부분만 외부에서 주입해서 이를 작업흐름(부가기능 부여) 중에 사용하도록 하는 전형적인 '템플릿/콜백' 구조
>   - 어드바이스가 일종의 '템플릿'이고 타깃을 호출하는 기능을 갖고 있는 MethodInvocation 오브젝트가 '콜백'임
> - 어드바이스와 포인트 컷을 묶은 오브젝트를 어드바이저라고함
>   - 어드바이스 : 부가기능
>   - 포인트 컷 : 메서드 선정 알고리즘
> - 포인트 컷과 어드바이스를 따로 등록하면, 어떤 어드바이스에 대해 어떤 포인트 컷을 적용할지 애매해짐.
> - 따라서, 이 둘을 묶은 어드바이저 타입의 오브젝트를 담아서 조합으로 만들어 등록함 

```java

// 어드바이스 정의 
public class TransactionAdvice implements MethodInterceptor {
	PlatformTransactionManager transactionManager;

	public void setTransactionManager(PlatformTransactionManager transactionManager) {
		this.transactionManager = transactionManager;
	}

	public Object invoke(MethodInvocation invocation) throws Throwable {
		TransactionStatus status = this.transactionManager.getTransaction(new DefaultTransactionDefinition());
		try {
			Object ret = invocation.proceed();
			this.transactionManager.commit(status);
			return ret;
		} catch (RuntimeException e) {
			this.transactionManager.rollback(status);
			throw e;
		}
	}
}

// 포인트 컷 정의
public class NameMatchClassMethodPointcut extends NameMatchMethodPointcut {
    public void setMappedClassName(String mappedClassName) {
        this.setClassFilter(new SimpleClassFilter(mappedClassName));
    }

    static class SimpleClassFilter implements ClassFilter {
        String mappedName;

        private SimpleClassFilter(String mappedName) {
            this.mappedName = mappedName;
        }

        public boolean matches(Class<?> clazz) {
            return PatternMatchUtils.simpleMatch(mappedName, clazz.getSimpleName());
        }
    }
}


```

<br>

#### 👉 어드바이스와 포인트 컷의 재사용

> - <img src="/images/ProxyFactoryBean과Advide그리고Pointcut을적용한구조.jpeg" width="400" height="400">
> - ProxyFactoryBean은 스프링이 DI와 템플릿/콜백 패턴, 서비스 추상화 등의 모든 기법이 적용됨
> - 이로써 독립적이며 여러 프록시가 공유할 수 있는 어드바이스와 포인트 컷으로 확장 기능을 분리할 수 있음 


<br>

#### 👉 스프링 AOP

> - 결국 우리가 하고자 하는 작업은 다음과 같음
> - 비즈니스 로직에 반복적으로 등장하는 트랜잭션 코드를 깔끔하고 효과적으로 분리하는 것 
> - 즉, 메서드가 호출하는 과정에서 다이나믹하게 참여해서 부가기능을 제공해주는 것 


<br>

#### 👉 자동 프록시 생성

```java

@SuppressWarnings("serial")
public class ProxyFactoryBean extends ProxyCreatorSupport
		implements FactoryBean<Object>, BeanClassLoaderAware, BeanFactoryAware {

	/**
	 * This suffix in a value in an interceptor list indicates to expand globals.
	 */
	public static final String GLOBAL_SUFFIX = "*";


	protected final Log logger = LogFactory.getLog(getClass());

	@Nullable
	private String[] interceptorNames;

	@Nullable
	private String targetName;

	private boolean autodetectInterfaces = true;

	private boolean singleton = true;

	private AdvisorAdapterRegistry advisorAdapterRegistry = GlobalAdvisorAdapterRegistry.getInstance();

	private boolean freezeProxy = false;

	@Nullable
	private transient ClassLoader proxyClassLoader = ClassUtils.getDefaultClassLoader();

	private transient boolean classLoaderConfigured = false;

	@Nullable
	private transient BeanFactory beanFactory;

	/** Whether the advisor chain has already been initialized. */
	private boolean advisorChainInitialized = false;

	/** If this is a singleton, the cached singleton proxy instance. */
	@Nullable
	private Object singletonInstance;


	/**
	 * Set the names of the interfaces we're proxying. If no interface
	 * is given, a CGLIB for the actual class will be created.
	 * <p>This is essentially equivalent to the "setInterfaces" method,
	 * but mirrors TransactionProxyFactoryBean's "setProxyInterfaces".
	 * @see #setInterfaces
	 * @see AbstractSingletonProxyFactoryBean#setProxyInterfaces
	 */
	public void setProxyInterfaces(Class<?>[] proxyInterfaces) throws ClassNotFoundException {
		setInterfaces(proxyInterfaces);
	}

	/**
	 * Set the list of Advice/Advisor bean names. This must always be set
	 * to use this factory bean in a bean factory.
	 * <p>The referenced beans should be of type Interceptor, Advisor or Advice
	 * The last entry in the list can be the name of any bean in the factory.
	 * If it's neither an Advice nor an Advisor, a new SingletonTargetSource
	 * is added to wrap it. Such a target bean cannot be used if the "target"
	 * or "targetSource" or "targetName" property is set, in which case the
	 * "interceptorNames" array must contain only Advice/Advisor bean names.
	 * <p><b>NOTE: Specifying a target bean as final name in the "interceptorNames"
	 * list is deprecated and will be removed in a future Spring version.</b>
	 * Use the {@link #setTargetName "targetName"} property instead.
	 * @see org.aopalliance.intercept.MethodInterceptor
	 * @see org.springframework.aop.Advisor
	 * @see org.aopalliance.aop.Advice
	 * @see org.springframework.aop.target.SingletonTargetSource
	 */
	public void setInterceptorNames(String... interceptorNames) {
		this.interceptorNames = interceptorNames;
	}

	/**
	 * Set the name of the target bean. This is an alternative to specifying
	 * the target name at the end of the "interceptorNames" array.
	 * <p>You can also specify a target object or a TargetSource object
	 * directly, via the "target"/"targetSource" property, respectively.
	 * @see #setInterceptorNames(String[])
	 * @see #setTarget(Object)
	 * @see #setTargetSource(org.springframework.aop.TargetSource)
	 */
	public void setTargetName(String targetName) {
		this.targetName = targetName;
	}

	/**
	 * Set whether to autodetect proxy interfaces if none specified.
	 * <p>Default is "true". Turn this flag off to create a CGLIB
	 * proxy for the full target class if no interfaces specified.
	 * @see #setProxyTargetClass
	 */
	public void setAutodetectInterfaces(boolean autodetectInterfaces) {
		this.autodetectInterfaces = autodetectInterfaces;
	}

	/**
	 * Set the value of the singleton property. Governs whether this factory
	 * should always return the same proxy instance (which implies the same target)
	 * or whether it should return a new prototype instance, which implies that
	 * the target and interceptors may be new instances also, if they are obtained
	 * from prototype bean definitions. This allows for fine control of
	 * independence/uniqueness in the object graph.
	 */
	public void setSingleton(boolean singleton) {
		this.singleton = singleton;
	}

	/**
	 * Specify the AdvisorAdapterRegistry to use.
	 * Default is the global AdvisorAdapterRegistry.
	 * @see org.springframework.aop.framework.adapter.GlobalAdvisorAdapterRegistry
	 */
	public void setAdvisorAdapterRegistry(AdvisorAdapterRegistry advisorAdapterRegistry) {
		this.advisorAdapterRegistry = advisorAdapterRegistry;
	}

	@Override
	public void setFrozen(boolean frozen) {
		this.freezeProxy = frozen;
	}

	/**
	 * Set the ClassLoader to generate the proxy class in.
	 * <p>Default is the bean ClassLoader, i.e. the ClassLoader used by the
	 * containing BeanFactory for loading all bean classes. This can be
	 * overridden here for specific proxies.
	 */
	public void setProxyClassLoader(@Nullable ClassLoader classLoader) {
		this.proxyClassLoader = classLoader;
		this.classLoaderConfigured = (classLoader != null);
	}

	@Override
	public void setBeanClassLoader(ClassLoader classLoader) {
		if (!this.classLoaderConfigured) {
			this.proxyClassLoader = classLoader;
		}
	}

	@Override
	public void setBeanFactory(BeanFactory beanFactory) {
		this.beanFactory = beanFactory;
		checkInterceptorNames();
	}


	/**
	 * Return a proxy. Invoked when clients obtain beans from this factory bean.
	 * Create an instance of the AOP proxy to be returned by this factory.
	 * The instance will be cached for a singleton, and create on each call to
	 * {@code getObject()} for a proxy.
	 * @return a fresh AOP proxy reflecting the current state of this factory
	 */
	@Override
	@Nullable
	public Object getObject() throws BeansException {
		initializeAdvisorChain();
		if (isSingleton()) {
			return getSingletonInstance();
		}
		else {
			if (this.targetName == null) {
				logger.info("Using non-singleton proxies with singleton targets is often undesirable. " +
						"Enable prototype proxies by setting the 'targetName' property.");
			}
			return newPrototypeInstance();
		}
	}

	/**
	 * Return the type of the proxy. Will check the singleton instance if
	 * already created, else fall back to the proxy interface (in case of just
	 * a single one), the target bean type, or the TargetSource's target class.
	 * @see org.springframework.aop.framework.AopProxy#getProxyClass
	 */
	@Override
	@Nullable
	public Class<?> getObjectType() {
		synchronized (this) {
			if (this.singletonInstance != null) {
				return this.singletonInstance.getClass();
			}
		}
		try {
			// This might be incomplete since it potentially misses introduced interfaces
			// from Advisors that will be lazily retrieved via setInterceptorNames.
			return createAopProxy().getProxyClass(this.proxyClassLoader);
		}
		catch (AopConfigException ex) {
			if (getTargetClass() == null) {
				if (logger.isDebugEnabled()) {
					logger.debug("Failed to determine early proxy class: " + ex.getMessage());
				}
				return null;
			}
			else {
				throw ex;
			}
		}
	}

	@Override
	public boolean isSingleton() {
		return this.singleton;
	}


	/**
	 * Return the singleton instance of this class's proxy object,
	 * lazily creating it if it hasn't been created already.
	 * @return the shared singleton proxy
	 */
	private synchronized Object getSingletonInstance() {
		if (this.singletonInstance == null) {
			this.targetSource = freshTargetSource();
			if (this.autodetectInterfaces && getProxiedInterfaces().length == 0 && !isProxyTargetClass()) {
				// Rely on AOP infrastructure to tell us what interfaces to proxy.
				Class<?> targetClass = getTargetClass();
				if (targetClass == null) {
					throw new FactoryBeanNotInitializedException("Cannot determine target class for proxy");
				}
				setInterfaces(ClassUtils.getAllInterfacesForClass(targetClass, this.proxyClassLoader));
			}
			// Initialize the shared singleton instance.
			super.setFrozen(this.freezeProxy);
			this.singletonInstance = getProxy(createAopProxy());
		}
		return this.singletonInstance;
	}

	/**
	 * Create a new prototype instance of this class's created proxy object,
	 * backed by an independent AdvisedSupport configuration.
	 * @return a totally independent proxy, whose advice we may manipulate in isolation
	 */
	private synchronized Object newPrototypeInstance() {
		// In the case of a prototype, we need to give the proxy
		// an independent instance of the configuration.
		// In this case, no proxy will have an instance of this object's configuration,
		// but will have an independent copy.
		ProxyCreatorSupport copy = new ProxyCreatorSupport(getAopProxyFactory());

		// The copy needs a fresh advisor chain, and a fresh TargetSource.
		TargetSource targetSource = freshTargetSource();
		copy.copyConfigurationFrom(this, targetSource, freshAdvisorChain());
		if (this.autodetectInterfaces && getProxiedInterfaces().length == 0 && !isProxyTargetClass()) {
			// Rely on AOP infrastructure to tell us what interfaces to proxy.
			Class<?> targetClass = targetSource.getTargetClass();
			if (targetClass != null) {
				copy.setInterfaces(ClassUtils.getAllInterfacesForClass(targetClass, this.proxyClassLoader));
			}
		}
		copy.setFrozen(this.freezeProxy);

		return getProxy(copy.createAopProxy());
	}

	/**
	 * Return the proxy object to expose.
	 * <p>The default implementation uses a {@code getProxy} call with
	 * the factory's bean class loader. Can be overridden to specify a
	 * custom class loader.
	 * @param aopProxy the prepared AopProxy instance to get the proxy from
	 * @return the proxy object to expose
	 * @see AopProxy#getProxy(ClassLoader)
	 */
	protected Object getProxy(AopProxy aopProxy) {
		return aopProxy.getProxy(this.proxyClassLoader);
	}

	/**
	 * Check the interceptorNames list whether it contains a target name as final element.
	 * If found, remove the final name from the list and set it as targetName.
	 */
	private void checkInterceptorNames() {
		if (!ObjectUtils.isEmpty(this.interceptorNames)) {
			String finalName = this.interceptorNames[this.interceptorNames.length - 1];
			if (this.targetName == null && this.targetSource == EMPTY_TARGET_SOURCE) {
				// The last name in the chain may be an Advisor/Advice or a target/TargetSource.
				// Unfortunately we don't know; we must look at type of the bean.
				if (!finalName.endsWith(GLOBAL_SUFFIX) && !isNamedBeanAnAdvisorOrAdvice(finalName)) {
					// The target isn't an interceptor.
					this.targetName = finalName;
					if (logger.isDebugEnabled()) {
						logger.debug("Bean with name '" + finalName + "' concluding interceptor chain " +
								"is not an advisor class: treating it as a target or TargetSource");
					}
					this.interceptorNames = Arrays.copyOf(this.interceptorNames, this.interceptorNames.length - 1);
				}
			}
		}
	}

	/**
	 * Look at bean factory metadata to work out whether this bean name,
	 * which concludes the interceptorNames list, is an Advisor or Advice,
	 * or may be a target.
	 * @param beanName bean name to check
	 * @return {@code true} if it's an Advisor or Advice
	 */
	private boolean isNamedBeanAnAdvisorOrAdvice(String beanName) {
		Assert.state(this.beanFactory != null, "No BeanFactory set");
		Class<?> namedBeanClass = this.beanFactory.getType(beanName);
		if (namedBeanClass != null) {
			return (Advisor.class.isAssignableFrom(namedBeanClass) || Advice.class.isAssignableFrom(namedBeanClass));
		}
		// Treat it as a target bean if we can't tell.
		if (logger.isDebugEnabled()) {
			logger.debug("Could not determine type of bean with name '" + beanName +
					"' - assuming it is neither an Advisor nor an Advice");
		}
		return false;
	}

	/**
	 * Create the advisor (interceptor) chain. Advisors that are sourced
	 * from a BeanFactory will be refreshed each time a new prototype instance
	 * is added. Interceptors added programmatically through the factory API
	 * are unaffected by such changes.
	 */
	private synchronized void initializeAdvisorChain() throws AopConfigException, BeansException {
		if (!this.advisorChainInitialized && !ObjectUtils.isEmpty(this.interceptorNames)) {
			if (this.beanFactory == null) {
				throw new IllegalStateException("No BeanFactory available anymore (probably due to serialization) " +
						"- cannot resolve interceptor names " + Arrays.toString(this.interceptorNames));
			}

			// Globals can't be last unless we specified a targetSource using the property...
			if (this.interceptorNames[this.interceptorNames.length - 1].endsWith(GLOBAL_SUFFIX) &&
					this.targetName == null && this.targetSource == EMPTY_TARGET_SOURCE) {
				throw new AopConfigException("Target required after globals");
			}

			// Materialize interceptor chain from bean names.
			for (String name : this.interceptorNames) {
				if (name.endsWith(GLOBAL_SUFFIX)) {
					if (!(this.beanFactory instanceof ListableBeanFactory lbf)) {
						throw new AopConfigException(
								"Can only use global advisors or interceptors with a ListableBeanFactory");
					}
					addGlobalAdvisors(lbf, name.substring(0, name.length() - GLOBAL_SUFFIX.length()));
				}

				else {
					// If we get here, we need to add a named interceptor.
					// We must check if it's a singleton or prototype.
					Object advice;
					if (this.singleton || this.beanFactory.isSingleton(name)) {
						// Add the real Advisor/Advice to the chain.
						advice = this.beanFactory.getBean(name);
					}
					else {
						// It's a prototype Advice or Advisor: replace with a prototype.
						// Avoid unnecessary creation of prototype bean just for advisor chain initialization.
						advice = new PrototypePlaceholderAdvisor(name);
					}
					addAdvisorOnChainCreation(advice);
				}
			}

			this.advisorChainInitialized = true;
		}
	}


	/**
	 * Return an independent advisor chain.
	 * We need to do this every time a new prototype instance is returned,
	 * to return distinct instances of prototype Advisors and Advices.
	 */
	private List<Advisor> freshAdvisorChain() {
		Advisor[] advisors = getAdvisors();
		List<Advisor> freshAdvisors = new ArrayList<>(advisors.length);
		for (Advisor advisor : advisors) {
			if (advisor instanceof PrototypePlaceholderAdvisor ppa) {
				if (logger.isDebugEnabled()) {
					logger.debug("Refreshing bean named '" + ppa.getBeanName() + "'");
				}
				// Replace the placeholder with a fresh prototype instance resulting from a getBean lookup
				if (this.beanFactory == null) {
					throw new IllegalStateException("No BeanFactory available anymore (probably due to " +
							"serialization) - cannot resolve prototype advisor '" + ppa.getBeanName() + "'");
				}
				Object bean = this.beanFactory.getBean(ppa.getBeanName());
				Advisor refreshedAdvisor = namedBeanToAdvisor(bean);
				freshAdvisors.add(refreshedAdvisor);
			}
			else {
				// Add the shared instance.
				freshAdvisors.add(advisor);
			}
		}
		return freshAdvisors;
	}

	/**
	 * Add all global interceptors and pointcuts.
	 */
	private void addGlobalAdvisors(ListableBeanFactory beanFactory, String prefix) {
		String[] globalAdvisorNames =
				BeanFactoryUtils.beanNamesForTypeIncludingAncestors(beanFactory, Advisor.class);
		String[] globalInterceptorNames =
				BeanFactoryUtils.beanNamesForTypeIncludingAncestors(beanFactory, Interceptor.class);
		if (globalAdvisorNames.length > 0 || globalInterceptorNames.length > 0) {
			List<Object> beans = new ArrayList<>(globalAdvisorNames.length + globalInterceptorNames.length);
			for (String name : globalAdvisorNames) {
				if (name.startsWith(prefix)) {
					beans.add(beanFactory.getBean(name));
				}
			}
			for (String name : globalInterceptorNames) {
				if (name.startsWith(prefix)) {
					beans.add(beanFactory.getBean(name));
				}
			}
			AnnotationAwareOrderComparator.sort(beans);
			for (Object bean : beans) {
				addAdvisorOnChainCreation(bean);
			}
		}
	}

	/**
	 * Invoked when advice chain is created.
	 * <p>Add the given advice, advisor or object to the interceptor list.
	 * Because of these three possibilities, we can't type the signature
	 * more strongly.
	 * @param next advice, advisor or target object
	 */
	private void addAdvisorOnChainCreation(Object next) {
		// We need to convert to an Advisor if necessary so that our source reference
		// matches what we find from superclass interceptors.
		addAdvisor(namedBeanToAdvisor(next));
	}

	/**
	 * Return a TargetSource to use when creating a proxy. If the target was not
	 * specified at the end of the interceptorNames list, the TargetSource will be
	 * this class's TargetSource member. Otherwise, we get the target bean and wrap
	 * it in a TargetSource if necessary.
	 */
	private TargetSource freshTargetSource() {
		if (this.targetName == null) {
			// Not refreshing target: bean name not specified in 'interceptorNames'
			return this.targetSource;
		}
		else {
			if (this.beanFactory == null) {
				throw new IllegalStateException("No BeanFactory available anymore (probably due to serialization) " +
						"- cannot resolve target with name '" + this.targetName + "'");
			}
			if (logger.isDebugEnabled()) {
				logger.debug("Refreshing target with name '" + this.targetName + "'");
			}
			Object target = this.beanFactory.getBean(this.targetName);
			return (target instanceof TargetSource targetSource ? targetSource : new SingletonTargetSource(target));
		}
	}

	/**
	 * Convert the following object sourced from calling getBean() on a name in the
	 * interceptorNames array to an Advisor or TargetSource.
	 */
	private Advisor namedBeanToAdvisor(Object next) {
		try {
			return this.advisorAdapterRegistry.wrap(next);
		}
		catch (UnknownAdviceTypeException ex) {
			// We expected this to be an Advisor or Advice,
			// but it wasn't. This is a configuration error.
			throw new AopConfigException("Unknown advisor type " + next.getClass() +
					"; can only include Advisor or Advice type beans in interceptorNames chain " +
					"except for last entry which may also be target instance or TargetSource", ex);
		}
	}

	/**
	 * Blow away and recache singleton on an advice change.
	 */
	@Override
	protected void adviceChanged() {
		super.adviceChanged();
		if (this.singleton) {
			logger.debug("Advice has changed; re-caching singleton instance");
			synchronized (this) {
				this.singletonInstance = null;
			}
		}
	}


	//---------------------------------------------------------------------
	// Serialization support
	//---------------------------------------------------------------------

	private void readObject(ObjectInputStream ois) throws IOException, ClassNotFoundException {
		// Rely on default serialization; just initialize state after deserialization.
		ois.defaultReadObject();

		// Initialize transient fields.
		this.proxyClassLoader = ClassUtils.getDefaultClassLoader();
	}


	/**
	 * Used in the interceptor chain where we need to replace a bean with a prototype
	 * on creating a proxy.
	 */
	private static class PrototypePlaceholderAdvisor implements Advisor, Serializable {

		private final String beanName;

		private final String message;

		public PrototypePlaceholderAdvisor(String beanName) {
			this.beanName = beanName;
			this.message = "Placeholder for prototype Advisor/Advice with bean name '" + beanName + "'";
		}

		public String getBeanName() {
			return this.beanName;
		}

		@Override
		public Advice getAdvice() {
			throw new UnsupportedOperationException("Cannot invoke methods: " + this.message);
		}

		@Override
		public String toString() {
			return this.message;
		}
	}

}

```

> - 프록시 팩토리 빈 방식의 접근법의 한계는 다음과 같음
> - (1) 부가기능이 타깃 오브젝트마다 새로 셍성해야함
> - (2) 부가기능의 적용이 필요한 타깃 오브젝트마다 비슷한 내용의 ProxyFactoryBean 빈 설정 정보를 추가해야함


<br>

#### 👉 중복 문제의 접근 방법

> - 변치않는 타깃으로의 위임과 부가기능 적용여부 판단이라는 부분은 코드 생성 기법을 이용하는 다이나믹 프록시 기술에 맡기고 변하는 부가기능 코드를 별도로 만들어서 다이나믹 프록시 생성 팩토리에 DI로 제공하는 방법을 사용
> - 부가기능 로직인 트랜잭션 경계설정은 코드로 만들게하고, 기계적인 코드인 타깃 인터페이스의 구현, 위임, 부가기능 연동 부분은 자동 생성 처리

<br>

#### 👉 빈 후처리기를 이용한 자동 프록시 생성기

> - 한번에 여러 개의 빈에 프록시를 적용할만한 방법이 없음
> - 스프링은 컨터에너로서 제공하는 기능 중에서 변치않는 핵심 부분외에 대부분은 확장할 수 있도록 확장 포인트를 제공함
> - BeanPostProcessor 인터페이스를 구현해서 만드는 '빈 후처리기' 
>   - 빈 오브젝트를 다시 후처리할 수 있게 만듦(가공)
> - DefaultAdvisorAutoProxyCreator는 어드바이저를 이용한 자동 프록시 생성기
> - 스프링은 빈 후처리기가 빈으로 등록되어 있으면, 빈 오브젝트가 생성될 때마다 빈 후처리기에 보내서 후처리를 진행함
> - 스프링이 생성하는 빈 오브젝트의 일부를 프록시로 포장하고, 프록시를 빈으로 대신 등록할 수 있음. 이것이 바로 '자동 프록시 생성 빈 후처리기'
> - <img src="/images/빈후처리기를이용한프록시자동생성.jpeg" width="400" height="400">
> - 적용할 빈을 선정하는 로직이 추가된 '포인트 컷'이 담긴 '어드바이저(어드바이스 + 포인트컷)'를 등록하고 빈 후처리기를 사요하면 여러 개의 타깃 오브젝트에 자동으로 프록시가 적용되게 할 수 있음


<br>

#### 👉 확장된 포인트 컷 

> - 포인트 컷, 타깃 오브젝트의 메서드 중에서 어떤 메서드에 부가기능을 적용할지 선정해주는 역할을 담당
> - '포인트 컷'은 '클래스 필터'와 '메서드 매처' 두 가지를 돌려주는 메서드를 갖고 있음
> - 어드바이스 적용 판단 과정
>   - (1) 적용할 클래스가 맞는지 확인 -> '클래스 필터'
>   - (2) 적용할 메서드가 맞는지 확인 -> '메서드 매처'

<br>

#### 👉 DefaultAdvisorAutoProxyCreator 적용

```java

public class NameMatchClassMethodPointcut extends NameMatchMethodPointcut {
	public void setMappedClassName(String mappedClassName) {
		this.setClassFilter(new SimpleClassFilter(mappedClassName));
	}
	
	static class SimpleClassFilter implements ClassFilter {
		String mappedName;
		
		private SimpleClassFilter(String mappedName) {
			this.mappedName = mappedName;
		}

		public boolean matches(Class<?> clazz) {
			return PatternMatchUtils.simpleMatch(mappedName, clazz.getSimpleName());
		}
	}
}

```

> - NameMatchClassMethodPointcut은 메서드 이름만 비교하던 포인트 컷 
> - 이를 상속해서 주어진 이름 패턴을 가지고 클래스 이름을 비교하는 ClassFilter를 만듦


<br>

#### 👉 어드바이저를 이용하는 자동 프록시 생성기 등록

```java

@SuppressWarnings("serial")
public class DefaultAdvisorAutoProxyCreator extends AbstractAdvisorAutoProxyCreator implements BeanNameAware {

	/** Separator between prefix and remainder of bean name. */
	public static final String SEPARATOR = ".";


	private boolean usePrefix = false;

	@Nullable
	private String advisorBeanNamePrefix;


	/**
	 * Set whether to only include advisors with a certain prefix in the bean name.
	 * <p>Default is {@code false}, including all beans of type {@code Advisor}.
	 * @see #setAdvisorBeanNamePrefix
	 */
	public void setUsePrefix(boolean usePrefix) {
		this.usePrefix = usePrefix;
	}

	/**
	 * Return whether to only include advisors with a certain prefix in the bean name.
	 */
	public boolean isUsePrefix() {
		return this.usePrefix;
	}

	/**
	 * Set the prefix for bean names that will cause them to be included for
	 * auto-proxying by this object. This prefix should be set to avoid circular
	 * references. Default value is the bean name of this object + a dot.
	 * @param advisorBeanNamePrefix the exclusion prefix
	 */
	public void setAdvisorBeanNamePrefix(@Nullable String advisorBeanNamePrefix) {
		this.advisorBeanNamePrefix = advisorBeanNamePrefix;
	}

	/**
	 * Return the prefix for bean names that will cause them to be included
	 * for auto-proxying by this object.
	 */
	@Nullable
	public String getAdvisorBeanNamePrefix() {
		return this.advisorBeanNamePrefix;
	}

	@Override
	public void setBeanName(String name) {
		// If no infrastructure bean name prefix has been set, override it.
		if (this.advisorBeanNamePrefix == null) {
			this.advisorBeanNamePrefix = name + SEPARATOR;
		}
	}


	/**
	 * Consider {@code Advisor} beans with the specified prefix as eligible, if activated.
	 * @see #setUsePrefix
	 * @see #setAdvisorBeanNamePrefix
	 */
	@Override
	protected boolean isEligibleAdvisorBean(String beanName) {
		if (!isUsePrefix()) {
			return true;
		}
		String prefix = getAdvisorBeanNamePrefix();
		return (prefix != null && beanName.startsWith(prefix));
	}

}

```

> - DefaultAdvisorAutoProxyCreator는 등록된 빈 중에서 Advisor의 인터페이스를 구현한 것을 모두 찾음
> - 그 다음 생성되는 모든 빈에 대해 어드바이저의 포인트 컷을 적용해보면서 프록시 적용 대상을 선정함
> - 빈 클래스가 프록시 선정 대상이라면 프록시 생성하여 원래 빈 오브젝트와 바꿔치기함 
> - 원래 빈 오브젝트는 프록시 뒤에 연결돼서 프록시를 통해서만 접근 가능하게 바꿈
> - 자동 프록시 생성기를 적용한 후에는 더 이상 ProxyFactoryBean을 사용할 필요가 없음


<br>


#### 👉 포인트 컷 표현식을 이용한 포인트 컷 

> - 포인트 컷 '메서드의 이름과 클래스의 이름 패턴을 각각 클래스 필터와 메서드 매처 오브젝트로 비교해서 선정하는 방식'
> - 위의 클래스 필터나 메서드 매처 오브젝트를 일일이 만드는 것은 번거로움
> - 스프링은 간단하고 효과적인 방법으로 포인트 컷의 클래스와 메서드 선정하는 알고리즘을 작성할 수 있는 방법을 제공함. 그것이 바로 '포인트 컷 표현식'임


<br>


#### 👉 포인트컷 표현식(AspectJ 포인트 컷 표현식)

> - AspectJExpressionPointcut을 통해서 포인트 컷 표현식을 지원하는 포인트 컷을 적용할 수 있음
> - 해당 클래스는 클래스와 메서드의 선정 알고리즘을 포인트 컷 표현식을 이용해 한 번에 지정할 수 있음
>   - 간단한 문자열로 복잡한 선정 조건을 쉽게 만들어낼 수 있는 강력한 표현식을 지원함
> - AspectJ 포인트 컷 표현식은 포인트 컷 지시자를 이용해서 작성함
>   - 대표적으로 execution 지시자가 있음
> - 또 특정 어노테이션이 타입, 메서드, 파라미터에 적용되어 있는 것을 보고 메서드를 선정하게 하는 포인트 컷을 만들 수 있음
>   - 대표적으로 @Transactional 어노테이션을 이용한 선정이 있음
> - 포인트 컷 표현식의 클래스 이름에 적용되는 패턴은 클래스 이름 패턴이 아니라 타입 패턴임
> - 포인트 컷 표현식을 적용하고 나서 이에 대해 적절한 테스트를 해야함
>   - (1) 부가기능이 제대로 적용되는지 확인
>   - (2) 적용대상이 아닌 빈들에 적용되지 않는지 확인

<br>


#### 👉 AOP란 무엇인가?

> - AOP란
>   - 애플리케이션에 산재ㄷ해서 나타나는 부가기능을 모듈화할 수 있는 기술을 말함
>   - OOP만으로는 모듈화하기 힘든 부가기능을 효과적으로 모듈화하도록 도와주는 보조 기술 
>   
> - 앞의 과정을 총 정리하면서 AOP 개념 설명
> - (1) 트랜잭션 서비스 추상화
>   - 트랜잭션 경계 설정 코드와 비즈니스 로직이 혼재되어 있었음
>   - 이에 따라 특정 트랜잭션 기술에 종속되어 버린 코드가 됨. 예를들어서, JDBC, JTA, Hibernate 등은 트랜잭션 코드가 다름
>   - 스프링은 이를 해결하고자 '서비스 추상화' 기술을 적용한 '트랜잭션 추상화 기술' 지원
>     - 트랜잭션 적용이라는 추상적인 작업 내용은 유지한 채로 구체적인 구현법을 자유롭게 구성할 수 있도록 만듦
> 
> - (2) 프록시와 데코레이터 패턴
>   - 트랜잭션을 어떻게 다룰 것인가는 '서비스 추상화'를 통해 코드에서 제거했지만, 여전히 비즈니스 로직에는 트랜잭션을 적용하고 있다는 사실은 드러나 있음
>   - 이를 해결하고자 고전적인 디자인 패턴 적용 방식을 사용함
>   - DI를 이용하여 데코레이터 패턴을 적용함
>   - 투명한 부가기능 부여를 가능하게 하는 데코레이터 패턴의 적용 덕에 비즈니스 로직을 담당하는 클래스와 부가기능을 담당하는 프록시(데코레이터)를 만들고 이를 DI로 연결함.
> 
> - (3) 다이나믹 프록시와 프록시 팩토리 빈
>   - 비즈니스 로직 인터페이스의 모든 메서드마다 트랜잭션 기능을 부여하는 코드를 넣어 프록시 클래스를 만드는 것은 번거로움(디자인 패턴을 직접 적용하는 것은 번거로움)
>   - 프록시 오브젝트를 런타임시에 만들어주는 JDK 다이나믹 프록시 기술을 적용함
>   - 스프링의 프록시 팩토리 빈을 이용하면 다이나믹 프록시 생성 방법에 DI를 적용함
>   - 내부적으로 '템플릿/콜백'을 활용하는 스프링의 프록시 팩토리 빈 덕분에 '어드바이스'와 '포인트컷'은 프록시에서 분리될 수 있었고 여러 프록시에서 공유 가능함
> 
> - (4) 자동 프록시 생성 방법과 포인트 컷
>   - 트랜잭션 적용 대상이 되는 빈마다 일일이 프록시 팩토리 빈을 설정해줘야함 
>   - 스프링 컨테이너의 '빈 생성 후처리' 기법을 활용해 컨테이너 초기화 시점에서 자동으로 프록시를 만들어 주는 방법을 도입함
> 
> - (5) 부가기능 모듈화
>   - 트랜잭션 같은 부가기능은 핵심 기능과 같은 방식으로 모듈화하기 매우 어려움
>   - 왜냐하면, 부가기능은 독립적인 방식으로 존재해서는 적용되기 어렵기 때문
>   - 즉, 타깃이 존재하지 않으면 '부가기능'은 의미가 없음
>   - 많은 개발자는 '핵심기능을 담당하는 코드 여기저기에 흩어져 나타나야 했던 이런 부가기능을 어떻게 독립적인 모듈로 만들지 노력함'
>     - DI, 데코레이터패턴, 다이나믹 프록시, 오브젝트 생성 후처리, 자동 프록시 생성, 어드바이저(어드바이스 + 포인트 컷)이 만들어짐
>   - 여태까지 한 모든 작업은 '핵심기능에 부여되는 부가기능을 효과적으로 모듈화하는 방법을 찾는 것이었고, 어드바이스와 포인트 컷을 결합한 어드바이저가 단순하지만 이런 특성을 가진 모듈의 원시적인 형태로 만들어짐'


<br>

#### 👉 AOP : 애스팩트 지향 프로그래밍, 관점 지향 프로그래밍

> - 애스팩트란 그 자체를 애플리케이션의 핵심 기능을 담고 있지는 않지만, 애플리케이션을 구성하는 중요한 한 가지 요소이고, 핵심기능에 부가되어 의미를 갖는 특별한 모듈을 의미함
> - 애스팩트는 어드바이스와 포인트 컷을 함께 갖고 있음. 즉, 어드바이저는 단순한 형태의 애스팩트임
> - 객체지향적인 코드를 작성했지만 부가기능이 핵심 기능의 모듈에 침투해 들어가면서 설계와 코드가 모두 지저분해짐
> - <img src="/images/독립애스팩트를이용한부가기능의분리화모듈화.jpeg" width="400" height="400">
> - 런타임시에는 왼쪽 그림처럼 각 부가기능 애스팩트는 자기가 필요한 위치에 다이나믹하게 합쳐짐(참여함)
> - 하지만, 설계와 개발은 오른쪽 그림처럼 다른 특성을 띈 애스팩트들을 독립적인 관점으로 작성하게함
> - 핵심적인 기능에서 부가적인 기능을 분리해서 애스팩트라는 독특한 모듈로 만들어서 설계하고 개발하는 방법을 '애스팩트 지향 프로그래밍(AOP)' 라고함
>   - AOP는 OOP를 보조하는 기술임


<br>

#### 👉 AOP 적용 기술 

> - 스프링에서 AOP를 적용하는 기술은 크게 2가지 방식이 있음
> - (1) 프록시를 이용한 AOP
>   - AOP에서의 핵심은 '프록시'를 이용한다는 것
>   - 프록시를 만들어서 DI로 연결된 빈 사이에 적용해 타깃의 메서드 호출과정에 참여해서 부가기능을 제공하도록 만듦
>   - 독립적으로 개발한 부가기능 모듈을 다양한 타깃 오브젝트의 메서드에 다이나믹하게 적용해줌
> - (2) 바이트코드 생성과 조작을 통한 AOP
>   - AspectJ는 타깃 오브젝트를 뜯어 고쳐서 부가기능을 직접 넣어주는 방식(바이트 코드 조작)
>   - 클래스 파일 자체로 수정하거나 클래스가 JVM에 로딩되는 시점을 가로쳐서 바이트 코드를 조작하는 복잡한 방법을 사용함
> - 바이트 코드 조작 방식을 사용하는 이유
>   - (1) DI 컨테이너의 도움을 받아서 자동 프록시 생성 방식을 사용하지 않아도 AOP를 적용할 수 있음
>   - (2) 프록시 방식보다 훨씬 강력하고 유연한 AOP가 가능함
>     - 프록시 방식은 위, 아래, 위/아래만 코드를 추가할 수 있음. 중간에 코드를 추가못함
>     - 또한, 타깃 내부적으로 호출되는 메서드 사이에도 코드를 추가하기 어려움


<br>

#### 👉 AOP 용어 

> - 타깃 : 어드바이스(부가기능)을 부여한 대상, 주로 핵심기능을 담은 클래스를 지칭함
> - 어드바이스 : 타깃 오브젝트에게 제공할 부가기능을 담은 모듈
> - 조인 포인트 : 어드바이스가 적용될 수 있는 위치를 말함. 타깃 오브젝트가 구현한 인터페이스의 모든 메서드는 조인 포인트가됨
> - 포인트 컷 : 어드바이스를 적용할 조인 포인트를 선별하는 작업. 또는 그 기능을 정의한 모둘을 말함
> - 프록시 : 클라이언트와 타깃 오브젝트 사이에 투명하게 존재하면서 부가기능을 제공하는 오브젝트를 말함
>   - 클라이언트의 메서드 호출을 대신 받아서 타깃에게 위임해줌
> - 어드바이저 : '어드바이스'와 '포인트 컷'을 하나씩 갖고 있는 오브젝트
> - 애스팩트 : AOP의 기본 모듈, 한 개 또는 그 이상의 포인트 컷과 어드바이스의 조합으로 만들어짐

<br>

#### 👉 AOP 네임스페이스 

```java

// aop 네임스페이스 선언
// aop 네임스페이스를 적용한 aop 설정 빈 
// XML 파일 
<beans xmlns="http://www.springframework.org/schema/beans"
xmlns:aop="http://www.springframework.org/schema/aop"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="
http://www.springframework.org/schema/beans
http://www.springframework.org/schema/beans/spring-beans.xsd
http://www.springframework.org/schema/aop
http://www.springframework.org/schema/aop/spring-aop.xsd">

    <!-- AOP 기능 활성화 -->
    <aop:aspectj-autoproxy/>

    <!-- Target 클래스 정의 -->
    <bean id="myService" class="com.example.MyService" />

    <!-- Aspect 클래스 정의 -->
    <bean id="loggingAspect" class="com.example.LoggingAspect" />

</beans>

// Aspect 클래스 정의 (Java 코드)
@Aspect
public class LoggingAspect {

    @Before("execution(* com.example.MyService.*(..))")
    public void logBeforeMethod() {
        System.out.println("A method in MyService is about to be called.");
    }
}


// Target 클래스 정의 (Java 코드)
public class MyService {

    public void performTask() {
        System.out.println("Task is being performed.");
    }
}

```

> - AOP를 적용하려면 최소한 네 가지 빈을 등록해야함
>   - (1) 자동프록시 생성기 
>     - 빈 오브젝트를 생성하는 과정에서 빈 후처리기로 참여함
>     - 빈으로 등록된 어드바이저를 이용해서 프록시를 자동으로 생성함
>   
>   - (2) 어드바이저
>     - 부가기능을 구현한 클래스를 빈으로 등록함
>   
>   - (3) 포인트 컷
>   
>   - (4) 어드바이저 
>     - 어드바이스와 포인트 컷을 갖고 있는 오브젝트
>     - 자동 프록시 생성기에 의해 자동 검색되어 사용됨


<br>

#### 👉 트랜잭션 속성

```java

// 트랜잭션 경계 설정 코드 
```

> - TransactionDefinition 인터페이스는 트랜잭션의 동작 방식에 영향을 줄 수 있는 네 가지 속성을 정의하고 있음
> - (1) 트랜잭션 전파 
>   - 트랜잭션의 경계에서 이미 진행중인 트랜잭션이 있거나 없을 때 어떻게 동작할지 결정함 
>   - <img src="/images/트랜잭션전파속성요약.png" width="400" height="400">
>   - (1) PROPAGATION_REQUIRED : 진행중인 트랜잭션이 없으면 새로 시작하고, 이미 시작된 트랜잭션이 있으면 이에 참여함
>   - (2) PROPAGATION_REQUIRES_NEW : 항상 새로운 트랜잭션을 시작함
>   - (3) PROPAGATION_SUPPORTS : 진행중인 트랜잭션이 있으면 참여하고, 없으면 트랜잭션 없이 실행함
>   - (4) PROPAGATION_NOT_SUPPORTED : 트랜잭션 없이 동작하도록 만들 수 있음, 진행 중인 트랜잭션이 있어도 무시함
>   
> - (2) 격리 수준
>   - 여러 트랜잭션이 동시에 처리될 때, 특정 트랜잭션이 다른 트랜잭션에서 변경하거나 조회하는 데이터를 볼 수 있게 허용할지 여부를 결정하는 것
>   - <img src="/images/격리수준종류.png" width="400" height="400">
>   - 모든 DB 트랜잭션은 격리수준을 갖고 있어야함
>   - 적절하게 격리수준을 조정해서 가능한 한 많은 트랜잭션을 동시에 진행시키면서도 문제가 발생하지 않게 하는 제어가 필요함
>     - (1) 제한시간 
>       - 트랜잭션을 수행하는 제한시간을 설정할 수 있음
>     
>     - (2) 읽기 전용
>       - 트랜잭션 내에서 데이터를 조작하는 시도를 막을 수 있음
>       - 또한, 데이터 액세스 기술에 따라 성능이 향상될 수 있음
>   - 참고할 만한 블로그 : https://mangkyu.tistory.com/299


<br>

#### 👉 트랜잭션 인터셉터와 트랜잭션 속성

> - TransactionInterceptor는 스프링에서 트랜잭션 경계설정 어드바이스를 사용할 수 있도록 만듦
> - TransactionAdvice와 동작 방식이 크게 다르지 않지만, 트랜잭션 정의를 메서드 이름 패턴을 이용해서 다르게 지정할 수 있는 방법이 추가됨
> - TransactionInterceptor는 2 가지 종류의 예외처리 방식이 있음
>   - (1) 런타임 예외가 발생하면 트랜잭션을 롤백함
>   - (2) 체크 예외가 발생하면, 예외 상황으로 해석하지 않고 일종의 비즈니스 로직에 따른 의미가 있는 리턴 방식의 한가지로 인식해서 트랜잭션을 커밋함


<br>

#### 👉 메서드 이름 패턴을 이용한 트랜잭션 속성 지정

```java

// XML 기반 트랜잭션 속성 정의
<beans xmlns="http://www.springframework.org/schema/beans"
xmlns:tx="http://www.springframework.org/schema/tx"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="
http://www.springframework.org/schema/beans
http://www.springframework.org/schema/beans/spring-beans.xsd
http://www.springframework.org/schema/tx
http://www.springframework.org/schema/tx/spring-tx.xsd">

    <!-- 트랜잭션 매니저 설정 -->
    <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
        <property name="dataSource" ref="dataSource"/>
    </bean>

    <!-- 트랜잭션 속성 정의 -->
    <tx:advice id="txAdvice">
        <tx:attributes>
            <!-- 모든 메서드에 기본 트랜잭션 속성 적용 -->
            <tx:method name="*" propagation="REQUIRED" isolation="DEFAULT" timeout="30" read-only="false" rollback-for="java.lang.Exception"/>
        </tx:attributes>
    </tx:advice>

    <!-- 트랜잭션 관리 적용 -->
    <aop:config>
        <aop:pointcut id="servicePointcut" expression="execution(* com.example.service.*.*(..))"/>
        <aop:advisor advice-ref="txAdvice" pointcut-ref="servicePointcut"/>
    </aop:config>

</beans>

// 애너테이션으로 트랜잭션 속성 지정

@Service
public class MyService {

    // 기본 트랜잭션 속성
    @Transactional
    public void defaultTransaction() {
        // 트랜잭션 관리되는 비즈니스 로직
    }

    // 트랜잭션 속성 정의
    @Transactional(
            propagation = Propagation.REQUIRED,  // 전파 수준
            isolation = Isolation.READ_COMMITTED,  // 격리 수준
            timeout = 30,  // 타임아웃(초)
            readOnly = false,  // 읽기/쓰기 모드
            rollbackFor = Exception.class  // 롤백 조건
    )
    public void customTransaction() {
        // 커스텀 트랜잭션 관리되는 비즈니스 로직
    }
}



```

> - 트랜잭션 속성은 위와 같이 정의할 수 있음


<br>

#### 👉 포인트 컷과 트랜잭션 속성의 적용 전략

> - (1) 트랜잭션 포인트 컷 표현식을 타입 패턴이나 빈 이름을 이용함
>   - 트랜잭션을 적용할 타깃 클래스의 메서드를 모두 트랜잭션 적용 후보가 되는 것이 좋음
>   - 비즈니스 로직을 담고있는 클래스라면 메서드 단위까지 세밀하게 포인트컷을 정의할 필요는 없음
>   - 트랜잭션 전파 방식을 고려해야함. 특정 트랜잭션이 다른 트랜잭션에 참여할 가능성이 있음. 예를들어서, UserService.add()
>   - 쓰기 작업이 없는 단순한 조회 작업만하는 메서드에도 모두 트랜잭션을 적용하는 게 좋음
>   - 조회의 경우 읽기 전용으로 트랜잭션 속성을 설정해두면 그만크 성능의 향상을 가져올 수 있음
>   - 트랜잭션용 포인트 컷 표현식에는 메서드나 파라미터, 예외에 대한 패턴을 적용하지 않는게 좋음
> 
> - (2) 공통된 메서드 이름 규칙을 통해 최소한의 트랜잭션 어드바이스와 속성을 정의함
>   - 기준이 되는 몇 가지 트랜잭션 속성을 정의하고 그에 따라 적절한 메서드 명명 규칙을 만들어서 하나의 어드바이스만으로 애플리케이션의 모든 서비스 빈에 트랜잭션 속성을 지정
>   - 예외적인 경우는 트랜잭션 어드바이스와 포인트 컷을 새롭게 추가할 필요가 있음
> 
> - (3) 프록시 방식 AOP 같은 타깃 오브젝트 내의 메서드를 호출할 때는 적용되지 않음
>   - <img src="/images/타깃안에서의호출에는적용되지않는프록시.png" width="400" height="400">
>   - 타깃 오브젝트가 자기 자신의 메서드를 호출할 때는 프록시를 통한 부가기능의 적용이 일어나지 않음
>   - 위의 그림을 설명하자면, 타깃 오브젝트 내로 들어와서 타깃 오브젝트의 다른 메서드를 호출하는 경우에는 프록시를 거치지 않고 직접 타깃 메서드가 호출되기 때문에 부가기능이 적용되지 않음
>   - 타깃 안에서의 호출에는 프록시가 적용되지 않는 문제를 해결할 수 있는 방법은 아래와 같이 2가지 방식이 있음
>     - (1) 스프링 API 이용, 프록시를 이용하도록 강제함(별로 추천하지 않는 방식)
>     - (2) 타깃 오브젝트의 바이트 코드를 직접 조작함(AspectJ를 이용한 방식)
  

<br>

#### 👉 트랜잭션 속성 적용, 트랜잭션 경계설정의 일원화

```java

// XML 설정 기반 포인트컷 표현식 등록 예시 
<beans xmlns="http://www.springframework.org/schema/beans"
xmlns:aop="http://www.springframework.org/schema/aop"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="
http://www.springframework.org/schema/beans
http://www.springframework.org/schema/beans/spring-beans.xsd
http://www.springframework.org/schema/aop
http://www.springframework.org/schema/aop/spring-aop.xsd">

    <!-- Aspect 정의 -->
    <bean id="loggingAspect" class="com.example.LoggingAspect"/>

    <!-- 포인트컷 표현식 등록 -->
    <aop:config>
        <!-- 포인트컷 정의: com.example.service 패키지의 모든 메서드 -->
        <aop:pointcut id="servicePointcut"
expression="execution(* com.example.service.*.*(..))"/>

        <!-- 포인트컷을 기반으로 Aspect 적용 -->
        <aop:advisor advice-ref="loggingAspect" pointcut-ref="servicePointcut"/>
    </aop:config>

</beans>

// Aspect 클래스 예시 
@Aspect
public class LoggingAspect {

    @Before("execution(* com.example.service.*.*(..))")
    public void logBeforeMethod() {
        System.out.println("A method in service is about to be called.");
    }
}

```

> - 트랜잭션 경계설정의 부가기능을 여러 계층에서 중구난방으로 적용하는 것은 좋지 않음
> - 일반적으로 특정 계층의 경계를 트랜잭션 경계와 일치시키는 것이 바람직함
> - 비즈니스 로직을 담고있는 서비스 계층 오브젝트의 메서드가 트랜잭션 경계를 부여하기에 적절함


<br>


#### 👉 트랜잭션 속성을 가진 트랜잭션 어드바이스 등록

```java

<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:tx="http://www.springframework.org/schema/tx"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="
           http://www.springframework.org/schema/beans
           http://www.springframework.org/schema/beans/spring-beans.xsd
           http://www.springframework.org/schema/tx
           http://www.springframework.org/schema/tx/spring-tx.xsd
           http://www.springframework.org/schema/aop
           http://www.springframework.org/schema/aop/spring-aop.xsd">

    <!-- DataSource 설정 (예시) -->
    <bean id="dataSource" class="org.apache.commons.dbcp2.BasicDataSource">
        <!-- DataSource 속성 설정 -->
    </bean>

    <!-- 트랜잭션 매니저 설정 -->
    <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
        <property name="dataSource" ref="dataSource" />
    </bean>

    <!-- 트랜잭션 속성을 정의하는 TransactionInterceptor -->
    <bean id="transactionInterceptor" class="org.springframework.transaction.interceptor.TransactionInterceptor">
        <property name="transactionManager" ref="transactionManager" />
        <property name="transactionAttributes">
            <props>
                <!-- 기본 트랜잭션 설정 -->
                <prop key="*">PROPAGATION_REQUIRED,ISOLATION_DEFAULT,timeout_30,readOnly</prop>
                
                <!-- get으로 시작하는 메서드: 읽기 전용 트랜잭션 -->
                <prop key="get*">PROPAGATION_REQUIRED,ISOLATION_DEFAULT,readOnly</prop>
                
                <!-- save로 시작하는 메서드: 새로운 트랜잭션 시작 -->
                <prop key="save*">PROPAGATION_REQUIRES_NEW,ISOLATION_DEFAULT</prop>
            </props>
        </property>
    </bean>

    <!-- AOP 설정: 포인트컷과 트랜잭션 어드바이저 정의 -->
    <aop:config>
        <aop:pointcut id="serviceLayer"
                      expression="execution(* com.example.service.*.*(..))"/>
        <aop:advisor pointcut-ref="serviceLayer" advice-ref="transactionInterceptor"/>
    </aop:config>

</beans>
```

> - TransactionAdvice 클래스로 정의했던 어드바이스 빈을 스프링의 TransactionInterceptor를 이용하도록 변경

<br>

#### 👉 어노테이션 트랜잭션 속성과 포인트 컷

> - 가끔 클래스나 메서드에 따라 제각각 속성이 다른, 세밀하게 튜닝된 트랜잭션 속성을 적용해야하는 경우가 있음
> - 설정 파일에서 패턴으로 분류 가능한 그룹을 만들어서 일관적으로 속성을 부여하는 방식 대신에 직접 타깃에 트랜잭션 속성정보를 가진 '애노테이션'을 지정하는 방법 사용


<br>

#### 👉 트랜잭션 어노테이션, @Transactional

```java

/**
 * Describes transaction attributes on a method or class.
 * <p>
 * Can be used directly on a method or a class. If you put it on a class, all methods of the class will share the same transaction configuration.
 */
@Target({ElementType.METHOD, ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Inherited
@Documented
public @interface Transactional {

    // 트랜잭션 전파 수준을 설정 (기본값은 REQUIRED)
    Propagation propagation() default Propagation.REQUIRED;

    // 트랜잭션 격리 수준을 설정 (기본값은 DEFAULT)
    Isolation isolation() default Isolation.DEFAULT;

    // 트랜잭션 타임아웃을 설정 (기본값은 -1, 타임아웃 없음)
    int timeout() default TransactionDefinition.TIMEOUT_DEFAULT;

    // 트랜잭션이 읽기 전용인지 여부 설정 (기본값은 false)
    boolean readOnly() default false;

    // 트랜잭션 롤백을 트리거할 예외 유형을 설정
    Class<? extends Throwable>[] rollbackFor() default {};

    // 롤백을 트리거할 예외의 클래스 이름을 설정
    String[] rollbackForClassName() default {};

    // 트랜잭션이 롤백되지 않도록 할 예외 유형을 설정
    Class<? extends Throwable>[] noRollbackFor() default {};

    // 트랜잭션이 롤백되지 않도록 할 예외의 클래스 이름을 설정
    String[] noRollbackForClassName() default {};
}
```

> - @Transactional 애너테이션의 타깃은 메서드와 타입. 따라서 메서드, 클래스, 인터페이스에 적용 가능함
> - 스프링은 @Transactional이 부여된 모든 오브젝트를 자동으로 타깃 오브젝트로 인식함
> - @Transactional은 기본적으로 트랜잭션 속성을 정의하는 것이지만 동시에 포인트 컷의 자동등록에도 사용됨

<br>

#### 👉 대체 정책 

```java
// 대체정책 코드 

// @Transactional 애너테이션을 이용한 트랜잭션 속성 정의

```

> - 스프링은 @Transactional을 적용할 때 4 단계의 '대체 정책'을 이용하게 해줌
> - 메서드의 속성을 확인할 때 타깃 메서드, 타깃 클래스, 선언 메서드, 선언 타입의 순서에 따라 @Transactional이 적용됐는지 확인함
> - 가장 먼저 발견되는 속성 정보를 사용하게 하는 방법

<br>

#### 👉 선언적 트랜잭션과 트랜잭션 전파 속성

```java
// 트랜잭션 속성을 사용하는 어드바이스 

// 스키마의 태그를 이용한 트랜잭션 어드바이스 정의 

```

> - <img src="/images/트랜잭션경계와트랜잭션전파.jpeg" width="400" height="400">
> - 스프링은 트랜잭션 전파 속성을 선언적으로 적용할 수 있는 기능을 지원함
> - REQUIRED 전파 속성을 가진 메서드를 결합해서 다양한 크기의 트랜잭션 작업을 형성할 수 있음
> - 트랜잭션 전파 속성 적용 예시
>   - '그 날의 이벤트의 선정 내역을 받아서 한 번에 처리하는 기능, 처리되지 않는 이벤트 신청 정보를 모두 가져와 DB에 등록하고 그에 따른 정보를 조작해줌'
>   - 하루치 이벤트 신청 내역을 처리하는 기능은 반드시 하나의 작업 단위로 처리되어야함, 즉 트랜잭션 경계 설정을 통해 크기를 조절해야함 
>   - EventService.processDailyEventRegistration()으로 구현
>   - processDailyEventRegistration() 에서 작업 중간에 사용자 등록을 할 필요가 있음. 즉, 중간 중간에 UserService.add()를 호출함
>   - UserService.add()는 독자적인 트랜잭션을 시작하는 대신에 processDailyEventRegistration()의 트랜잭션에 참여해야함
>   - '트랜잭션 전파'라는 기법을 통해 UserService.add()는 독자적인 트랜잭션 단위가 될 수도 있고, 다른 트랜잭션 일부로 참여할 수 있음
> - AOP를 이용해 코드 외부에서 트랜잭션의 기능을 부여해주고 속성을 지정할 수 있게 하는 방식을 '선언적 트랜잭션'이라고함
> - TransactionTemplate이나 개별 데이터 기술의 트랜잭션 API를 사용해 직접 코드 안에서 사용하는 방법을 '프로그램에 의한 트랜잭션'이라고함

<br>

#### 👉 트랜잭션 동기화와 테스트

> - 트랜잭션의 자유로운 전파와 그로인해 유연한 개발이 가능할 수 있었던 기술적인 배경에는 2가지 기술이 있음
>   - (1) AOP 덕분에 프록시를 이용한 트랜잭션 부가기능을 간단하게 애플리케이션 전반에 적용
>   - (2) 스프링 트랜잭션인 추상화(서비스 추상화)
>     - DAO 에서 일어나는 작업들을 하나의 트랜잭션으로 묶어서 추상 레벨에서 관리하게 해주는 기술

<br>

#### 👉 트랜잭션 매니저와 트랜잭션 동기화

> - 트랜잭션 추상화 기술의 핵심은 '트랜잭션 매니저'와 '트랜잭션 동기화'
> - '트랜잭션 동기화' 덕분에 진행 중인 트랜잭션이 있는지 확인하고, 트랜잭션 전파 속성에 따라 이에 참여하도록 만듦

<br>

#### 👉 @Rollback

> - @Transactional은 기본적으로 트랜잭션을 강제 롤백시키도록 설정되어 있음
> - 롤백 기능을 제어하려면 별도의 어노테이션을 사용해야함
> - @Rollback은 롤백 여부를 지정하는 값을 갖고 있음
> - @Rollback(false)로 설정하면 롤백을 하지 않도록 설정할 수 있음


<br>

#### 👉 @TransactionConfiguration 

```java

// @TransactionConfiguration 예시 코드 

```

> - 클래스 레벨에 트랜잭션 설정을 부여할 수 있음
> - 해당 어노테이션을 사용하면 '롤백'에 대한 공통속성을 지정할 수 있음
> - @Transactional(propagation = Propagation.NEVER) 메서드에 부여하면 클래스 레벨의 @Transactional 설정을 무시함



<br>
<br>

## 📌 07. 스프링 핵심 기술의 응용


