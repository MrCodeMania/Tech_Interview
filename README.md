# 기술, CS 관련
좋은 코드란?
1. 일관성 있는 코드 (프로젝트 팀원 간의 그라운드 룰 바탕)
2. 중복이 없는 코드  
    - 중복이 있다면 A를 수정할 시 다른 오래된 코드 A는 수정이 안 됨
3. 확장성 있는 코드 (함수, 메소드의 파라미터 타입을 폭넓게 받기 등)  
    - 적절한 확장성이 설계되어 있지 않은 코드의 경우, 내부적으로 많은 변경이 필요하고 코드를 읽기 어렵게 만듦.

---

# C#

인터페이스와 추상, 가상함수
- Virtual : 하나의 기능을 하는 완전한 클래스이며, 파생클래스에서 상속해서 추가적인 기능추가 및 virtual 한정자가 달린 것을 재정의해서 사용가능

- Abstract : 여러개의 파생 클래스에서 공유할 기본 클래스의 공통적인 정의만 하고, 파생클래스에서 abstract 한정자가 달린 것을 모두 재정의(필수)해야 함

- Interface : abstract와 비슷하지만 멤버변수를 사용할 수 없고 보통 abstract는 개념적으로 계층적인 구조에서 사용이 되며(동물이나 어떤 사물의 계층적인 구조가 있을 때) Interface는 서로 다른 계층이나 타입이라도 같은 기능을 추가하고 싶을 때 사용함(사람이나 기계가 speak 하는 인터페이스를 추가할 때)

**Unity는 다양한 플랫폼 환경을 지원하므로 CLR을 지원하는 C#을 사용.**



## 클래스

속성과 메소드를 공유하는 유사한 성질의 객체들을 하나로 그룹화한 것이다.




## 오버로딩, 오버라이딩

- 오버로딩(Overloading): 같은 클래스 내 이름은 같게 매개변수를 다르게 하여 여러 메서드 정의.  
컴파일 시간에 처리 -> 정적 바인딩(Static Binding)

- 오버라이딩(Overriding): 상위 클래스의 연산을 하위 클래스에서 재정의.  
실행 시간에 처리 -> 동적 바인딩(Dynamic Binding)



## 업캐스팅, 다운캐스팅

- 업캐스팅(UpCasting): 하위 객체가 상위 객체를 참조  
ex) Food food = new SeaFood();  
- 다운캐스팅(DownCasting): 상위 객체를 하위 객체에 담음  
ex) SeaFood seaFood = (Food)food; -> 명시적 형변화



## 배열과 리스트

- 배열은 인덱스를 가진 데이터의 집합 / 리스트는 인덱스 없이 순차적으로 저장된 데이터의 집합.  
- 배열은 메모리에 연속적으로 저장되고 / 리스트는 메모리에 분산 되어 저장.  
- 배열은 Random Access가 가능 / 리스트는 불가능  
- 배열은 중간에 데이터 삽입,삭제가 어렵고 / 리스트는 쉽다.



## namespace, partial

- namespace – 클래스 이름이 겹칠 때, 클래스는 overload가 적용되지 않기 때문에 클래스 명이 중복되어 실행이 되지 않는 것을 방지하기 위해 사용.  
- partial – 클래스의 크기가 길어지는 경우, 가독성이 떨어지는 것을 방지하기 위해 분할해서 작성할 수 있게 함.

## C# 박싱과 언박싱

object는 참조 형식

### **박싱**
- 값 형식을 object 형식으로 변환하는 것.  
- 메모리를 힙 영역에 생성, 값을 힙 영역에 할당된 메모리로 복사, object에 메모리 주소를 할당

### **언박싱** 
- object 형식 개체에 boxing 상태의 값 형식 데이터를 추출하는 것.  
- 박싱값인지 확인, 박싱된 값이라면 값 타입 변수에 복사, 박싱한 메모리와 언박싱한 메모리 2개 존재(가비지 발생)

사용 이유
- 편리성 때문에 쓰임, 시간 소요, 가비지 등으로 인해 성능상의 단점이 있음.

박싱과 언박싱이 이루어질 때,  
저장되는 공간이 다르고 불필요한 형변환이 이루어져 Overhead(처리로 인한 간접적인 시간 소요) 발생 가능.



## 가비지에 대하여

가비지 콜렉터가 발생하는 경우
1. 객체를 할당하는 임계치가 넘어갈 때
2. GC.Collect 메서드 호출 시
3. 시스템의 메모리가 부족할 때

## 지역변수와 전역변수  
- 전역변수 – data 영역에 저장  
- 지역변수 – stack 영역에 저장 (컴파일 타임에 크기가 결정됨)   
- heap – 동적 할당, 해제 시 사용되는 메모리 영역 (런 타임에 크기가 결정됨)  
- code – 프로그램의 코드가 저장되는 영역



## 프로퍼티

get, set 제공하는 것



## delegate와 event 차이

- delegate – 콜백 함수. 메소드의 대리자 역할. 사용 시 다른 클래스에 직접적으로 불필요적 접근을 하지 않을 수 있음. 여러 함수를 연결 시 반드시 등록된 순서대로 실행되는 것은 아님.  
- event – 어떠한 일이 생겼을 때 알려주는 객체. 델리게이트와 동작 원리가 비슷함. 외부에서 접근 불가능하기 때문에 객체의 상태 변화나 사건의 발생을 알리는 용도로 사용.  
- delegate는 메소드를 참조, event는 delegate를 사용하여 이벤트 처리기와 연결



## Object Oriented Programming(OOP – 객체 지향 프로그래밍)

코드에 대한 재사용성이 높아짐, 자주 사용되는 로직을 라이브러리로 만들어두면 신뢰성 확보, 예외 처리로 인한 디버깅으로 버그 발생이 줄어듦, 캡슐화로 인한 생산성이 높아짐, 객체 단위로 코드가 작성되기 때문에 디버깅이 쉽고 유지보수에 용이

### **객체 지향적 설계 원칙 5가지**
1. SRP(Single Responsibility Principle) : 단일 책임 원칙
클래스는 단 하나의 책임을 가져야 하며 클래스를 변경하는 이유는 단 하나의 이유이어야 한다.
2. OCP(Open-Closed Principle) : 개방-폐쇄 원칙
확장에는 열려 있어야 하고 변경에는 닫혀 있어야 한다.
3. LSP(Liskov Substitution Principle) : 리스코프 치환 원칙
상위 타입의 객체를 하위 타입의 객체로 치환해도 상위 타입을 사용하는 프로그램은 정상적으로 동작해야 한다.
4. ISP(Interface Segregation Principle) : 인터페이스 분리 원칙
인터페이스는 그 인터페이스를 사용하는 클라이언트를 기준으로 분리해야 한다.
5. DIP(Dependency Inversion Principle) : 의존 역전 원칙
고수준 모듈은 저수준 모듈의 구현에 의존해서는 안된다.


### **객체지향 4요소 (추상화, 캡슐화, 상속성, 다형성)** 

1. 추상화(Abstraction) - 공통의 속성이나 기능을 묶어서 이름을 붙이는 것  
객체 지향 관점에서 클래스를 정의하는 것이 추상화  
절차 지향 프로그래밍에서는 구조체 해당  

2. 캡슐화(Encapsulation) - 데이터를 외부에서 접근하지 않고 오로지 메소드를 통해서만 접근이 가능하도록 해야함.
    - 캡슐화 + 은닉화 + 무결성
3. 상속성(Inheritance) - 클래스의 멤버와 메소드를 다른 클래스에 물려주거나 물려받는 것
    - 코드의 재사용성, 확장성, 유지보수성, 프로그램 구조에 대한 이해도
4. 다형성(Polymorphism) – Overloading, Overriding을 통해 여러 개의 형태로 변화하는 것



## Test-Driven Development (TDD)

새로운 기능에 대한 자동화된 테스트케이스를 작성하고 해당 테스트를 통과하는 가장 간단한 코드를 작성한다. 상황에 맞게 리팩토링하는 과정을 거치는 것.

- 테스트가 코드 작성을 주도하는 개발 방식.

- TDD는 코드를 작성하기 전, 보다 요구사항에 집중할 수 있도록 도와준다.  
- 리팩토링 속도가 빨라지고 코드의 퀄리티(객체지향적이고 확장성이 용이한 코드, 재설계의 시간을 단축시킬 수 있는 코드, 디버깅 시간이 단축되는 코드)가 향상된다.

- 코드량이 늘어남, 테스트 코드 진입 장벽 존재,
모든 코드에 대해서 테스트 코드를 작성할 수 없고 작성할 필요도 없다. 테스트 코드를 작성한다고 해서 버그가 발생하지 않는 것도 아님.

---


# 운영체제 (OS)

## 프로그램

어떤 작업을 위해 실행할 수 있는 파일



## 프로세스와 스레드


### 프로세스
- 의미
    - 메모리에 올라와 실행되고 있는 프로그램의 인스턴스
    - 운영체제로부터 시스템 자원을 할당받는 자원의 단위
    - 실행된 프로그램을 의미
- 할당받는 시스템 자원의 예
    - CPU 시간
    - 운영되기 위해 필요한 주소 공간
    - Code, Data, Stack, Heap의 구조로 되어 있는 독립된 메모리 영역
- 특징
    - 프로세스당 최소 1개의 스레드를 가지고 있음
    - 다른 프로세스의 변수나 자료구조에 접근할 수 없음
    - 다른 프로세스의 자원에 접근하려면 프로세스 간의 통신을 사용


### Process Control Block (PCB – 프로세스 제어 블록)
- 특정 프로세스에 대한 중요한 정보를 저장하고 있는 OS의 자료구조
- 프로세스의 생성과 동시에 고유한 PCB 생성

### PCB에 저장되는 정보
- 프로세스 ID,
- 프로세스 상태 : new, ready, running, waiting, terminated 등
- 프로그램 카운터 : 프로세스가 다음에 실행할 명령어의 주소
- CPU 레지스터
- CPU 스케줄링 정보 : 프로세스의 우선순위, 스케줄 큐에 대한 포인터 등
- 메모리 관리 정보 : 페이지 테이블 또는 세그먼트 테이블 등과 같은 정보를 포함
- 입출력 상태 정보 : 프로세스에 할당된 입출력 장치들과 열린 파일 목록
- 어카운팅 정보 : 사용된 CPU 시간, 시간제한, 계정번호 등

### 멀티 프로세스  
하나의 응용프로그램을 여러 개의 프로세스로 구성하여 각 프로세스가 하나의 작업을 처리하도록 하는 것

- 장점  
    - 여러 개의 자식 프로세스 중 하나에 문제가 발생하면 그 자식 프로세스만 죽는 것 이상으로 다른 영향이 확산되지 않음.

- 단점  
    - Context Switching에서의 오버헤드 발생 (단순히 CPU 레지스터 교체뿐만 아니라 RAM, CPU 사이의 캐쉬 메모리에 대한 데이터까지 초기화되서 오버헤드가 큼)
    - 프로세스 사이의 어렵고 복잡한 통신 기법(IPC)

### 스레드  
- 의미
    - 프로세스 내에서 실행되는 여러 흐름의 단위
    - 프로세스의 특정한 수행 경로
    - 프로세스가 할당받은 자원을 이용하는 실행의 단위
- 특징
    - 스레드는 프로세스 내에서 각각 Stack만 따로 할당받고 Code, Data, Heap 영역은 공유
    - 프로세스 내의 주소 공간이나 자원들은 같은 프로세스 내의 스레드끼리 공유하면서 실행
    - 스레드가 프로세스 자원을 변경하면, 다른 스레드도 변경 결과를 즉시 볼 수 있음

### 멀티 스레드
- 의미
    - 하나의 응용프로그램을 여러 개의 스레드로 구성하고 각 스레드로 하여금 하나의 작업을 처리하도록 하는 것
    - 윈도우, 리눅스 등 운영체제들이 멀티 프로세싱을 지원하고 있지만 멀티 스레딩을 기본으로 하고 있음
    - 웹 서버는 대표적인 멀티 스레드 응용프로그램
- 장점
    - 시스템 자원 소모 감소 (자원의 효율성 증대) (프로세스를 생성하지 않음 – 시스템 콜이 줄음)
    - 시스템 처리량 증가 (처리 비용 감소)
    - 스레드 간 데이터를 주고받는 것이 간단해지고 스레드 간 작업량이 작아 Context Switching이 빠름
    - 간단한 통신 방법으로 프로그램 응답 시간 단축
- 단점
    - 주의 싶은 설계 필요
    - 디버깅이 까다로움
    - 다른 프로세스에서 스레드를 제어할 수 없음
    - 동기화 문제가 발생할 수 있음
    - 하나의 스레드에 문제가 발생하면 전체 프로세스가 영향을 받음

    

- 사용하는 이유  
    - 프로그램을 여러 개 키는 것보다 하나의 프로그램 안에서 여러 작업을 해결하기 위함
    1. 자원의 효율성 증대
    2. 처리 비용 감소 및 응답 시간 단축



## 스케줄러  

프로세스를 스케줄링하기 위한 Queue

장기 스케줄러, 중기 스케줄러, 단기 스케줄러



## API

Application Programming Interface – 컴퓨터나 컴퓨터 프로그램 사이의 연결



## AOT와 JIT, 인터프리터

AOT – ahead-of-time compile 미리 컴파일하는 방식
JIT – just-in-time compile 파일을 받고 컴파일해서 렌더링하는 방식



## Paging

- 프로세스를 일정 크기인 페이지로 잘라서 메모리에 적재하는 방식
- 페이징을 사용함으로써 논리 메모리는 물리 메모리에 저장될 때, 연속되어 저장될 필요가 없고 물리 메모리의 남는 프레임에 적절히 배치됨으로써 외부 단편화를 해결
- 내부단편화가 발생하지만 메모리를 거의 100%에 가깝게 쓸 수 있음

## Segmentation

- 서로 다른 논리적 단위인 세그먼트로 분할하여 세그먼트의 기준, 길이를 저장
- 서로 다른 크기의 세그먼트들이 적재되고 제거되는 일이 반복되면 외부 단편화 발생



## Virtual Memory (가상 메모리)

프로세스 전체가 메모리 내에 적재되지 않더라도 실행이 가능하도록 하는 기법

### **Demand Paging (요구 페이징)**

- 프로그램 시작 시, 프로그램 전체를 물리 메모리에 적재하는 대신, 초기에 필요한 것들만 적재하는 전략
- 프로세스 내의 개별 페이지들은 페이저(Pager)에 의해 관리된다.
- 사용되지 않을 페이지를 가져오는 시간낭비와 메모리 낭비를 줄일 수 있다.

### **페이지 교체**
- 필요한 페이지를 요청하는 과정에서 page fault(페이지 부재)가 발생하게 되면, 원하는 페이지를 보조저장장치에서 가져와야 하는데 만약, 물리 메모리가 모두 사용 중인 상황이라면, 페이지 교체가 이뤄져야 한다.

### **페이지 교체 알고리즘**
- FIFO (First-In, First-Out)
- OPT (최적 페이지 교체) : 앞으로 가장 오랫동안 사용되지 않을 페이지를 찾아 교체
- LRU (Least-Recently-Used) : 가장 오랫동안 사용되지 않은 페이지를 선택하여 교체
- LFU (Least-Frequently-Used) : 참조 횟수가 가장 적은 페이지를 교체
- MFU (Most-Frequently-Used) : 참조 횟수가 가장 적은 페이지가 최근에 메모리에 올라왔기 때문에 앞으로 계속 사용될 것이라는 가정



## L1, L2, L3 캐시

- CPU의 속도와 시스템 메모리의 속도 차이를 해결하기 위해 CPU 안에 포함되는 작고 빠른 메모리
- CPU가 메모리를 읽는 과정에서 자주 이용하는 정보를 캐시 메모리에 저장함으로써 재사용 시 빠르게 접근 가능

### 캐시의 지역성
- *시간 지역성* : 최근에 참조된 주소의 내용은 곧 다음에 다시 참조되는 특성
- *공간 지역성* : 대부분의 실제 프로그램이 참조된 주소와 인접한 주소의 내용이 다시 참조되는 특성

### 컴퓨터 구조에서 캐시 히트와 캐시 미스  
*캐시 히트* – 참조하고자 하는 메모리가 캐시에 존재할 경우  
*캐시 미스* - 참조하고자 하는 메모리가 캐시에 존재하지 않을 경우



## 컨텍스트 스위칭

- CPU에서 여러 프로세스를 돌아가면서 작업을 처리하는 과정.  
- 동작 중인 프로세스가 대기를 하면서 PCB에 해당 프로세스의 상태(Context)를 보관하고, 대기하고 있던 다음 순서의 프로세스가 동작하면서 이전에 PCB에 보관했던 프로세스의 상태를 복구하는 작업.  
- 콜스택



## 임계영역(Critical Section)  

동일한 자원을 동시에 접근하는 작업을 실행하는 코드 영역

### 교착상태(Deadlock)
둘 이상의 프로세스가 다른 프로세스가 점유하고 있는 자원을 서로 기다릴 때 무한 대기에 빠지는 상황
- 예방
1. 자원의 상호 배제 조건 방지 : 한 번에 여러 프로세스가 공유 자원을 사용할 수 있게함.
-> 동기화 관련 문제가 발생 가능
2. 점유 대기 조건 방지 : 프로세스 실행에 필요한 모든 자원을 한꺼번에 요구하고 허용할 때까지 작업을 보류해서, 나중에 다른 자원을 점유하기 위한 대기 조건을 성립하지 않도록 함.
3. 비선점 조건 방지 : 다른 프로세스에게 할당된 자원이 선점권이 없다고 가정할 때, 높은 우선순위의 프로세스가 해당 자원을 선점할 수 있도록 함.
4. 순환 대기 조건 방지 : 자원을 순환 형태로 대기하지 않도록 일정한 한 쪽 방향으로만 자원을 요구할 수 있도록 함.

### 해결책  
*Lock* – 하드웨어 기반, 진입한 프로세스가 Lock을 획득하고 방출함으로써 동시에 접근이 되지 않도록 한다.  
*Semaphores* – 소프트웨어상에서 임계영역 문제를 해결하기 위한 동기화 도구
- Counting Semaphores(가용한 자원의 개수)
- Binary Semaphores(MUTEX – 0과 1 값)



## 모니터

- 개발자의 코드를 상호배제하게끔 만든 추상화된 데이터 형태
- 공유 자원에 접근하기 위한 키 획득과 자원 사용 후 해제를 모두 처리한다. (Semaphores는 직접 처리가 필요)



## 동기와 비동기

동기 – 메소드를 실행시키고 값이 반환되기 전까지는 blocking
비동기 – 이벤트 큐, 백그라운드 스레드에게 해당 task를 위임하고 다음 코드를 실행

---

# 자료구조

list, vector, map

요소 전체 순회시 가장 빠른 순서대로 나열 및 BigO 표기

삽입 및 삭제의 속도가 빠른 순서대로 나열 및 BigO 표기

랜덤 액세스가 빠른 순서대로 나열 및 BigO 표기

사용해야하는 상황, 하지 말아야 할 상황 구분하기



## 해시 함수  

특별한 알고리즘을 통해 key 값들을 작은 범위의 값들로 바꾸는 함수.

- 무조건 1:1 대응으로 만드는 것보다 충돌을 최소화하는 방향으로 설계하고 발생하는 충돌에 대비해 어떻게 대응할 것인가가 더 중요하다.  
- 1:1 대응이 되도록 만드는 것이 거의 불가능하기도 하지만 만들어봤자 array와 다를 바 없고 메모리를 너무 차지하게 된다.  
- 좋은 hash function을 선택하는 것은 hash table의 성능 향상에 필수적인 것.



## 해시 테이블

- (key,value)로 데이터를 저장하는 자료구조

### 충돌 해결법
1. Open Address (개방주소법)  
- 다른 해시 버킷에 해당 자료를 삽입하는 방식  
- Linear Probing, Quadratic Probing, Double Hashing Probing 
2. Separate Chaining (분리연결법)  
- 연결리스트를 사용해 버켓의 다음 데이터의 주소를 저장, 쉬운 구현 및 삭제,
트리를 사용하는 방식도 있음, 연결된 데이터가 많다면 트리가 유용  
- 데이터 수가 많아지면 캐시의 효율성이 감소

Open Address 방식은 연속된 공간에 데이터를 저장하기 때문에 캐시 효율이 높다.  
따라서 데이터의 개수가 충분히 적다면 성능은 Open Address > Separate Chaining
Separate Chaining 방식은 테이블의 확장을 보다 늦출 수 있다.  
해시 버킷의 개수가 75%가 되면 해시 버킷의 개수를 두 배로 동적 확장시킨다.  



## 그래프

정점과 간선의 집합.  
트리 또한 그래프이며 사이클이 허용되지 않는 그래프를 말함.

그래프 탐색 방법 2가지  
1. DFS  
    - 한 정점으로부터 연결되어있는 한 정점으로만 나아가는 방법을 우선으로 탐색.
    - Stack 사용
2. BFS  
    - 한 정점으로부터 연결되어있는 모든 정점으로 나아간다
    - Queue 사용.
    - BFS로 구한 경로는 최단 경로임



## Spanning Tree

모든 정점이 cycle 없이 연결된 형태



## Minimum Spanning Tree

그래프 G의 spanning tree 중 edge weight의 합이 최소인 spanning tree를 말함.

### *Minimum Spanning Tree 알고리즘*

1. Kruskal Algorithm
    - 정점들로 그래프를 구성하고, weight가 작은 edge를 추가하는 데 추가할 때 cycle이 생기지 않는 경우에만 추가한다.

2. Prim Algorithm
    - 한 개의 정점으로 그래프를 구성하고, 그래프 A 내부에 있는 정점과 외부에 있는 정점이 연결된 edge 중 weight가 가장 작은 edge를 추가한다.

---

# 보안
PE구조

커널모드와 유저모드

IOCTL

드라이버

프로세스와 모듈, 스레드

---

# 언어
C와 C++의 차이점

C#과 C++의 차이점

C++11/C++14/C++17 다뤄본 것

C++ 가상함수 테이블
- 한 개 이상의 Virtual 함수를 포함하는 클래스에 대해서 컴파일러가 가상함수 테이블을 만듬. 테이블은 Key와 Value로 구성. A 객체의 Func1 호출하면 A 클래스의 가상함수 테이블의 주소 참조.
- 일반 함수는 정적 바인딩, 가상 함수는 동적 바인딩.
- 가상함수(동적 바인딩)의 장단점
장점 : 실행시 다형성이 생김.
단점 : 실행 속도에서는 손해.

C++ 스마트포인터
포인터를 자동으로 메모리에서 할당 해제함. 자바는 GC, C++은 사용자가 직접 메모리 누수 방지를 해줘야 함.
shared_ptr, unique_ptr, weak_ptr 이 있음.

C++ 캐스팅 종류와 작동방식 static_cast, dynamic_cast, interpret_cast, const_cast

C++ stdcall과 cdecl 차이

C++ 구조체 패딩

C++ 이중 포인터를 이용한 이차원 동적할당과 이차원 배열과의 차이점
메모리의 낭비를 줄이기 위해 동적 할당
 


---


# Unity 관련
Unity 엔진 관련

코루틴과 Invoke
1. 코루틴
- 여러 개의 루틴이 동시에 실행되며 서로 제어를 넘겨주는 방식.
- yield return을 사용하여 현재 위치를 기억하고 다른 루틴에게 수행 권한을 넘겨서 여러 개의 쓰레드가 동시 동작하는 것과 같은 효과를 제공한다.
- 단일 쓰레드여서 멀티쓰레드가 가지는 교착 상태 등의 문제에서 자유롭다는 장점이 있다.
- 특정 조건이 충족될 때까지 실행 상태를 지연시킬 수 있다.
- GameObject의 Active가 off가 된다면 실행 중이던 코루틴은 정지되며, 정지된 코루틴은 GameObject가 다시 Active되더라도 재실행되지 않는다.
2. Invoke
- 매개변수로 넘겨주는 시간만큼 함수를 지연호출할 수 있다.
- GameObject의 Active가 off 상태에서도 호출된다.
- InvokeRepeat를 사용할 때 지연 시간을 변수로 두고 변경하더라도 최초에 넘겼던 파라미터의 값으로 적용된다.
- 지연시간 이외의 파라미터를 전달할 수 없다.

코루틴과 비동기에 대하여
유니티에서의 대부분 로직은 동기로 작성. 흐름을 관리하거나 시간을 조절해서 시행해야 하는 작업은 코루틴으로 구현.
게임 개발에서는 비동기 사용이 적다. 게임 로직을 비동기로 동시에 사용할 수 있게 제공하더라도 효율성보다 준비단계에서의 부담이 더 크므로 필요성을 느끼지 못함.
1. 코루틴
- 유니티에서 코루틴은 근본적으로 동기처리
- 코루틴의 로직은 메인 스레드의 진행을 block하고 있으며, 이는 렌더링 프레임 수치에 직접적인 영향력을 행사.
- 코루틴에 작업을 load할 때는 해당 프로세스의 복잡도가 얼마나 높은지, 최대로 걸릴 수 있는 시간이 어느정도인지 충분히 인지하고 로직을 작성해야 함.
2. 비동기
- 네트워크 통신, 파일 시스템 접근에서 비교적 효과를 볼 수 있음.
- 여러 스레드에 작업을 할당하여 로딩 속도에서 이점을 볼 수 있음.
- 불필요한 멀티스레드 환경을 만들 수 있음.

결국 비동기와 코루틴의 적절한 활용이 필요. ( 대부분은 코루틴, 비동기의 남용 자제 )


최적화 전략 수립 과정
스크립팅 최적화
- SendMessage 와 BroadcastMessage 함수 사용자제
- Find 관련 함수 사용자제
- 자식이 많은 오브젝트 transform 변경시 많은 비용 발생
- Update , LateUpdate 등 함수가 비어있으면 지워라 , 빈 Update 종류 함수는 비용발생
- Vector2 및 Vector3 연산을 줄여라
- Camera.main 의 결과를 캐싱하거나 사용하지 않고 수동으로 카메라에 대한 참조를 관리해라

가비지 컬렉터(힙 메모리) 최적화
- 캐싱 사용
우리 코드가 힙 할당으로 이어지는 함수를 반복적으로 호출하고 결과를 폐기하면 불필요한 쓰레기가 생성됩니다.
대신, 우리는 이러한 객체에 대한 참조를 저장하고 재사용하는 기술을 캐싱이라고 합니다.
- 자주 호출되는 함수에는 힙메모리 할당을 하지 않는다.
- 오브젝트 풀링 사용
- 문자열 관련
1) 필요한 문자열 생성을 줄여야합니다. 동일한 문자열 값을 두 번 이상 사용하는 경우 문자열을 한 번 만들고 값을 캐시해야합니다.
2) 우리는 불필요한 문자열 조작을 줄여야합니다. 예를 들어 자주 업데이트되고 연결된 문자열이 포함 된 텍스트 구성 요소가있는 경우 두 개의 텍스트 구성 요소로 구분할 수 있습니다.
3) 런타임에 문자열을 작성해야 한다면 StringBuilder 클래스를 사용해야 합니다 .
4) 디버깅을 위해 더 이상 필요하지 않게 되면 Debug.Log ()에 대한 호출을 제거해야 합니다.
- 함수 관련
1) GameObject.tag 대신 GameObject.CompareTag 사용하기
2) Input.GetTouch 와 Input.touchCount 대신 Input.touches 사용하기
3) Physics.SphereCastNonAlloc 대신 Physics.SphereCastAll 사용하기
- 박싱으로 이어지는 함수 호출 제거
- 코루틴 함수 관련
1) StartCoroutine 을 사용할때 약간의 가비지가 발생한다.
2) yield new return 에서 new 를 할때마다 가비지가 생성 된다.
- foreach 문 자제
- 수동으로 가비지컬렉터 실행 자제

그래픽 관련 최적화
1. CPU 의 작업량을 줄이는 방법
1) 가까이에 있는 오브젝트를 수동이나 Unity 의 드로우 콜 배칭을 활용해 결합합니다.
2) 큰 텍스처 아틀라스에 개별적 텍스처를 넣는 등의 방법으로 오브젝트의 머티리얼 수를 줄입니다.
3) 오브젝트가 여러 번 렌더링되는 요소(반사, 그림자, 픽셀 별 광원 등)를 덜 사용합니다.
2. GPU 모델 지오메트리 최적화
1) 필요 이상으로 삼각형을 사용하지 않습니다.
2) UV 매핑의 경계 부분과 하드 에지(버텍스가 두 배)의 수를 가능한 적게 유지합니다.
3. 조명(Lighting) 퍼포먼스
1) 전역 조명을 베이크하고 라이트 매퍼를 사용
4. GPU: 텍스처(Texture) 압축과 밉맵
1) 3D 씬에서 사용되는 텍스처에 항상 밉맵 생성을 활성화
5. 실시간 섀도우
1) 실시간 섀도우 사용을 줄인다.

기타 최적화 방법
프로파일링을(기본 or 툴 사용) 해서 어디서 과부화가 걸리는지 확인

1. 에셋 관련

1) 텍스처

- Read/Write enabled 플래그 비활성화 (기본 비활성화)
- 밉맵(하지만 그래픽적인 차이가 좀 있음 그러므로 상황봐서)
- 모든 텍스처를 압축

2) 모델

- Read/Write enabled 플래그 비활성화(기본 활성화)
- 애니메이션화되지 않는 모델의 리그를 비활성화
- 애니메이션화되는 모델에 게임 오브젝트 최적화 옵션 활성화
- Optimize Game Objects 활성화
- 가능한 한 메시 압축 사용

2. 힙 메모리 관련

- 오브젝트 풀링 사용
- 박싱을 최대한 피해야 한다. ex) - enum 타입을 Dictionary 의 키로 사용하면 박싱이 발생한다.
- Foreach 루프문 사용 시 루프가 종료되는 시점마다 박싱이 발생했었다.(몇번 반복하든 foreach 문 하나당 한 번씩) 버전 업그레이드를 하면서 Foreach문의 박싱은 사라졌지만 CPU 성능에 차이가 있다.(결론은 아무튼 자제하는 게 좋다.)
- 배열 기반 Unity API 
링크 : https://docs.unity3d.com/kr/2018.2/Manual/BestPracticeUnderstandingPerformanceInUnity4-1.html

3. Resources 폴더사용 하지 말고 AssetBundle 을 사용하자.

4. 기타
- 부동 소수점보다 정수 연산의 속도가 빠르며, 부동 소수점 연산의 속도가 벡터, 매트릭스 또는 쿼터니언 연산보다 빠르다
- Object.Find와 Object.FindObjectOfType의 사용을 모두 제거하는 것이 일반적으로 가장 좋다.(싱글톤은 예외)
- 일차원 배열 사용, 다차원 배열이 필요한 경우 다차원 배열 말고 가변 배열을 사용
- 적은 콜백 함수 사용 (Update, FixedUpdate, LateUpdate 같은)
- 델리게이트 사용시 추가 제거가 자주 일어난다면 다른 데이터 구조 사용을 고려

게임을 더 빠르게 만드는 간단한 체크리스트
- PC 용으로 빌드할 때(타겟 GPU 에 따라) 버텍스 수를 프레임당 200K 및 3M 아래로 유지합니다.
- 빌트인 셰이더를 사용하는 경우 Mobile 이나 Unlit 의 카테고리에서 선택합니다.
비모바일 플랫폼에서도 작동은 하지만 복잡한 셰이더를 단순화시키고 비슷하게 만듭니다.
- 씬 별로 서로 다른 머티리얼의 수를 적게 유지하고 다른 오브젝트 간에 최대한 많은 머티리얼을 공유합니다.
- 움직이지 않는 오브젝트에는 Static 프로퍼티를 설정하여, 정적 배칭과 같은 내부 최적화가 가능하도록 해야 합니다.
- 다수 보다는 단일(가능하다면 방향성) pixel light 만 지오메트리에 영향을 주도록 해야 합니다.
- 동적 조명을 사용하기보다 조명을 베이크해야 합니다.
- 가능하면 압축 텍스처 사용하고 32 비트보다는 16 비트를 사용해야 합니다.
- 가능하면 안개의 사용을 피해야 합니다.
- 오클루전 컬링을 사용하여 오클루전이 많아 복잡한 정적 씬에서 드로우 콜과 가시적 지오메트리를 줄이는 데 활용합니다. 오클루전 컬링을 염두에 두고 레벨을 디자인합니다.
- 스카이박스를 써서 멀리 있는 지오메트리를 “진짜처럼 보이게” 합니다.
- 멀티 패스 접근 방식 대신 픽셀 셰이더나 텍스처 컴바이너를 활용해 여러 텍스처를 혼합합니다.
- 가능하면 half 정밀도 변수를 사용합니다.
- 픽셀 셰이더에서 pow, sin, cos 등 복잡한 수학 연산의 사용을 최소화합니다.
- 프래그먼트 별 텍스처 사용을 줄입니다.


게임 루프와 델타 타임에 대한 이해

게임 루프 – 한 프레임마다 반복되는 실행
입력 처리 -> 게임 업데이트 - > 렌더링 출력 (각각 한 프레임이 지나고 진행)
입력 지연 시간에 민감한 게임은 게임 루프를 잘 설계해서 최적화를 해야 함. (격투 게임)

Time.deltaTime – 마지막 프레임이 완료되기까지 걸린 시간
델타 타임으로 총알이나 캐릭터의 진행 속도 등 조절하면, FPS가 달라도 동일한 크기로 수행할 수 있다.

String Concat 루프 대책 {

string s = “”;

for(int I = 0; I < 1000; I++)
	s += “1”;

s += “1”  ->  s = s + “1” 

string 클래스는 불변성을 가지고 있다. 직접 유동적으로 자신이 추가하고 삭제하는 문자열 버퍼를 가지고 있지 않다. 대상 문자열을 참조하고 있을 뿐이다.

위와 같은 식을 사용할 시, 문자열을 이어붙이기 위해 새로운 string 객체를 계속 만들어내고 있다. -> 지속적인 가비지(Garbage) 발생

대책

StringBuilder 클래스를 사용하여 append로 붙이고	ToString으로 변환하여 사용

string이 불변성을 가진 이유 (참조만 하는 이유)
1. 멀티스레드 환경에서 안전하다.
스레드의 최소 작업 단위는 하나의 어셈블리 명령 단위.
string의 단순 대상 참조 명령은 스레드의 최소 단위이므로 도중에 스레드 제어가 넘어가지 않는다.
만약 스레드 제어가 넘어갔다면 -> A = “hello” , B = “world” , A + B = “heworllldo”

2.중복적으로 사용 시 재사용성이 증가합니다.
단순 참조만 하기 때문에 버퍼 공간을 만들 필요가 없어 재사용성이 증가합니다.
(상수 문자열이 두드러진 효과를 나타냄)

결론
빈번한 문자 이어붙이기가 일어날 경우 StringBuilder를 사용하는 것이 도움이 될 수 있다. 다만 그렇지 않은 경우는 오히려 불리해지는 경우도 있으므로 상황에 맞게 잘 고려해서 사용해야 한다.
}


Mono와 IL2CPP {
Unity는 크로스 컴파일(크로스 컴파일러는 컴파일러가 실행되는 플랫폼이 아닌 다른 플랫폼에서 실행 가능한 코드를 생성할 수 있는 컴파일러(개발을 편하게 하기 위함))을 제공.

중간언어인 C#을 지원함으로써 다양한 플랫폼에 대한 컴파일 된 프로그램들을 얻을 수 있음.

Mono)
코드를 build하면 Assembly-CSharp.dll 파일이 생성.
해당 형태를 IL(Intermediate Language)이라고 함.
mono(libmono.so)가 IL 코드를 Assembly로 변환하여 실행.

il2cpp(C++로 변환하는 IL))
IL 코드를 C++ native code로 변환하여 실행.
빌드 시, Assembly-Csharp.dll 대신 libil2cpp.so 파일이 생성.
성능, 보안 및 플랫폼 호환성 개선

}


Update, FixedUpdate, LateUpdate
- Update : 1프레임에 한 번 호출. (타이머, 키 입력, 물리 효과가 적용되지 않은 오브젝트의 움직임)
- FixedUpdate : Fixed Timestep에 설정된 값에 따라 일정한 간격으로 호출. (물리 효과가 적용된 오브젝트)
- LateUpdate : 모든 Update 함수가 호출된 후, 마지막으로 호출. (카메라)

OnApplicationQuit, OnEnable, OnDisable, OnDestroy
- OnApplicationQuit : 어플리케이션이 종료되기 직전 모든 게임 내 객체들에게 전송.
- OnEnable : 해당 Behaviour가 활성화 상태가 되면 호출.
- OnDisable : 해당 Behaviour가 비활성화 상태가 되면 호출. 객체가 파괴될 때도 호출. 해당 구간에서 자원 해제(cleanup) 코드를 사용할 수도 있음.
- OnDestroy : 부착된 Behaviour가 파괴되는 경우 호출. 해당 Behaviour가 활성화 상태였던 경우에만 호출.

스태틱 게임오브젝트와 배칭{

움직이지 않고 동일한 재질을 공유하는 오브젝트들을 일괄 처리함으로써 드로우콜을 줄일 수 있다.
정적 배칭을 활성화하면 씬을 시작할 때 동일한 재질을 공유하는 정적 오브젝트를 결합하여 하나의 공유된 버텍스와 이를 위한 인덱스 버퍼를 구축한다. 오브젝트들은 드로우콜 사이의 상태변경을 거의 일으키지 않아 드로우 콜의 개수를 줄일 수 있다.

}

스크립트 실행 순서
Awake – prefab이 인스턴스화 된 직후에 호출. 오브젝트가 활성화되는 순간 호출. 최초 1회만 호출.
OnEnable – 오브젝트 활성화 직후 호출. Awake와는 다르게 비활성화 -> 활성화할 때마다 호출.
Start – 스크립트 인스턴스가 활성화된 경우에 호출. 게임 오브젝트 + 스크립트 모두 활성화되어 있을 때 최초 1회 한정 호출. 호출 시기는 첫 번째 프레임 업데이트 전.
Awake, Start 차이 -
Awake가 Start보다 빠름. 모든 오브젝트의 Awake를 실행하고 Start가 실행됨.
Start간의 순서는 유니티가 내부적으로 결정하므로 랜덤 (Instance ID를 가지고 순차적으로 호출됨) (Execution Order를 변경하여 순서 변경 가능)
Awake는 스크립트가 비활성 상태라도 호출됨.
Awake는 자신이 초기화할 수 있는 작업을 수행하고 Start는 다른 Class를 참조하는 경우 사용.

FixedUpdate - Fixed Timestep에 설정된 값에 따라 일정한 간격으로 호출. (물리 효과가 적용된 오브젝트)
OnTriggerXXX – 두 오브젝트가 물리 연산을 하지 않고 충돌을 하려고 할 때 사용. 부딪혔을 때 통과하게 됨.
OnCollistionXXX – 두 오브젝트가 물리 법칙에 영향을 받을 때 사용. 부딪혔을 때 충돌을 감지한다.
yield WaitForFixedUpdate – FixedUpdate 끝날 때 호출.
Update – 프레임당 한 번 호출. 프레임 업데이트를 위한 주요 작업 함수.
yield 함수들 (코루틴)
yield null
yield WaitForSecond
yield WWW
yield StartCoroutine
LateUpdate - 모든 Update 함수가 호출된 후, 마지막으로 호출. (카메라)
렌더링 관련 함수
yield WaitForEndOfFrame – 하나의 프레임이 완전히 종료될 때 호출.
OnApplicationPause
OnApplicationQuit - 어플리케이션이 종료되기 직전 모든 게임 내 객체들에게 전송.
OnDisable - 해당 Behaviour가 비활성화 상태가 되면 호출. 객체가 파괴될 때도 호출. 해당 구간에서 자원 해제(cleanup) 코드를 사용할 수도 있음.
OnDestroy - 부착된 Behaviour가 파괴되는 경우 호출. 해당 Behaviour가 활성화 상태였던 경우에만 호출.

Prefab – 게임 오브젝트를 생성, 설정 및 저장 가능하고 Prefab으로 변환 시 모든 복사본을 자동으로 동기화할 수 있기 때문에 게임 오브젝트를 단순히 복사해서 붙여넣는 것보다 효율적.

rigidbody를 가진 오브젝트가 이동이나 회전을 멈추면 asleep 상태로 들어가 스크립트 진행을 멈춘다고 함.

---

# 그래픽스
버텍스 셰이더와 픽셀 셰이더
래스터라이저
포워드와 디퍼드 렌더링
디더링
텍스처 압축 포맷
드로우콜
오클루전 컬링과 프러스텀 컬링
소프트마스크
스텐실
알파테스트, 알파블렌딩

---

# 알고리즘
DFS 구현 방식

DFS와 다익스트라 차이, 장단점

퀵소트 버블소트

가장 빠른 머지소트 구현법

쿼드트리, 옥트리

 ---

# 네트워크
TCP/UDP 차이

Little-Endian, Big-Endian

Big Endian – 최상위 바이트부터 차례로 저장
Unix의 RISC 계열의 프로세서가 사용.
네트워크에서 사용하는 바이트 오더링.
앞에서부터 스택에 PUSH
비교 연산에서 Little Endian보다 속도가 빠름

Little Endian – 최하위 바이트부터 차례로 저장
Intel 계열의 프로세서가 사용.
뒤에서부터 스택에 PUSH
계산연산에서 Big Endian보다 속도가 빠름

패킷 컨테이너

소켓

P2P, 릴레이, 데디케이트 서버
