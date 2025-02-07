## UML
- 시스템을 시각적으로 설계하고 문서화하는데 사용되는 표준화된 모델링 언어
- 객체지향 설계 개념을 기반으로 하여, 다양한 다이어그램을 통해 시스템의 구조, 행위, 상호작용 등을 표현

![[Pasted image 20241214014745.png]]
구조, 행위, 상호작용 다이어그램이 있음

### 클래스 다이어그램
시스템을 구성하는 클래스, 속성과 메서드, 클래스 간의 관계 등을 시각적으로 표현

세 칸의 직사각형 모양으로 클래스 표현
- 클래스 이름
	- 다른 클래스와 구별되는 유일한 이름을 가짐
- 속성(필드)
	- 클래스가 가지는 특성 또는 변수
- 메서드
	- 클래스가 수행할 수 있는 동작 또는 함수
![[Pasted image 20241214014851.png]]

#### 가시성
속성과 메서드의 접근 권한을 지정하는 방식
![[Pasted image 20241214015014.png]]

#### 클래스 간의 관계
1. 연관 관계
2. 일반화 관계
3. 집합 관계
4. 합성 관계
5. 의존 관계
6. 실체화 관계

##### 1. 연관 관계
클래스 간에 서로 메시지를 주고받으며 이용하는 관계
한 클래스가 상대 클래스에서 제공하는 기능을 사용

**양방향 연관 관계**
![[Pasted image 20241214015111.png]]
단순한 연관 관계.

**역할이 부여된 연관 관계**
![[Pasted image 20241214015132.png]]

**다중 연관 관계**
선 위에 다중성을 표기해 나타냄. 다대다 관계도 있을 수 있으나, 일대 다 관계를 변환해 사용하는 것이 대부분
![[Pasted image 20241214020137.png]]

![[Pasted image 20241214020206.png]]
`.` : 또는
`..` : ~부터 ~까지
`*` :다수

**단방향 연관 관계**
한쪽만 아는 관계.
`학생->교수` 형태라면, 학생만 교수를 알고있는 것
![[Pasted image 20241214020401.png]]

**연관 클래스**
연관 관계를 더 구체적으로 나타내고 싶을 때 클래스를 추가하는 것.
점선을 사용해 나타내며, 이렇게 만들어진 연관 클래스도, 다른 클래스와 관계를 맺을 수 있음
![[Pasted image 20241214020443.png]]

##### 2. 일반화 관계
일반화: 공통점을 가지고 있는 여러 클래스를 묶어서 새로운 클래스를 만들고, 공통적인 이름을 붙인 것.
상속 구조이며, 하위 클래스는 상위 클래스의 모든 것을 상속받아 사용
![[Pasted image 20241214020718.png]]

##### 3. 집합 관계
상위 클래스가 하위클래스들로 **구성되어 있는** 경우. 모든 객체가 독립적으로 동작하고, 필요할 때 다른 객체로 변경하기도 용이함
![[Pasted image 20241214020807.png]]
컴퓨터는 모니터, 본체, 키보드로 구성됨. 키보드가 작동하지 않으면 새 키보드로 교체할 수 있음
##### 4. 합성 관계
집합 관계와 유사하나, 모든 객체들이 전체 객체에 완전히 종속되어 독립된 객체로 존재할 수 없음
모든 객체가 같은 생명 주기를 가지고 있으므로 각각 독립적으로 동작할 수 없는 강한 결합관계
![[Pasted image 20241214020854.png]]
노트북은 모니터, 본체, 키보드가 일체형으로 되어있고, 따로 분리할 수 없음

##### 5. 의존 관계
한 클래스가 **다른 클래스의 존재에 의존**하는 경우
**짧은 시간 동안** 다른 클래스의 객체나 메서드를 사용

**연관관계와의 차이점**
연관 관계는 상대 클래스를 인식하기 위한 멤버변수를 가져야 함.
![[Pasted image 20241214021043.png]]
Repeater 클래스에는 Scan 클래스를 멤버 변수로 사용하여 인식하고 있음.

의존관계는 메서드에서 상대 객체를 사용함.
클래스 A의 메서드가 클래스 B 객체 자체를 파라미터로 받아, 필요한 시간동안만 사용

![[Pasted image 20241214021143.png]]
이 Repeater 클래스는 Scan 객체를 가지고 있기 때문에, main 함수로부터 객체를 넘겨받을 필요가 있음

##### 실체화 관계
**메서드**의 공통 특성을 묶어 새로운 인터페이스 클래스를 생성.
이 클래스는 변수를 정의할 수 없고, 추상 메서드를 가지며, 이 메서드에 대한 구체적인 실현은 하위 클래스에서 구현
하위 클래스와의 관계는 일반화 관계와 다르게 점선으로 나타냄

**일반화** 관계: 클래스의 공통 특성을 묶어서 상위 클래스 생성
**실체화** 관계: 메서드의 공통 특성을 묶어서 인터페이스 클래스 생성


























