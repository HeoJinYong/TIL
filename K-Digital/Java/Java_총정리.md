## 1. 자바 시작하기

- jdk 11 설치
- 이클립스 2020-09 버전 설치

#### 💡 이클립스 jdk 따로 적용하는 방법

> 나는 jdk 8을 쓰고 있었고 이클립스도 다른 버전을 사용 중이었는데, 새로 다운 받은 이클립스에서 jdk 11를 못 찾아서 실행이 되지 않았음

1. 이클립스 압축 해제한 폴더에서 eclipse.ini 파일 열기

2. jdk 폴더에서 javaw.exe의 경로를 가져와 아래와 같이 작성

   ```
   -vm
   C:\Program Files\Java\jdk-11.0.10\bin\javaw.exe
   ```

   - `-vm`은 버츄얼머신의 약자로, vm의 경로를 하단에 적어준 path로 잡아주라는 의미

### 환경 설정

- Window - Preferences - 'encoding' 검색
  - 전부 `UTF-8`로 바꾸기
- Window - Preferences - Java - Installed JREs - Add - standard VM
  - jdk 연결(Program files - java - jdk)하고 선택

### 프로젝트 생성

- File - New - Project
- 특수문자 사용 X
- 영어와 숫자, 첫글자는 영어

### 클래스 생성

- New - Class
- 첫 글자는 대문자로
- public static void main(String[] args) 체크

```
public class Hello {
	public static void main(String[] args) {
		System.out.println("Hello Java!");
	}
}
```

- 명령어는 함수 안에, 함수는 클래스 안에 있어야 함
- 클래스 파일명과 코드 내 클래스명이 같아야 함



## 2. 변수와 타입

### 변수 선언

```
// 타입 변수이름
int age;
double value;
```

- 선언된 위치 내에서만 쓸 수 있음

  ```
  int val1 = 10;
  if (true){
      int val2 = 20;
      System.out.println(val1); // 10
      System.out.println(val2); // 20
  }
  System.out.println(val2); // error
  ```

### 변수 명명 규칙 (naming convention)

- 첫번째 글자 : 영어 소문자, $, _
  - $price, _companyName
- 영어 대소문자 구분
  - firstname != firstName
- 카멜 케이스
  - userList, newTodoList

#### 💡 case styles

- 카멜식(Camel case)
  - `첫 단어는 소문자`로 시작, 두번째 단어는 대문자로 시작
  - 단어끼리 붙임
  - **t**his**I**s**J**ava
- 파스칼식(Pascal case)
  - 모든 단어를 `대문자로 시작`
  - 단어끼리 붙임
  - **T**his**I**s**J**ava
- 스네이크식(Snake case)
  - 각 단어를 `_`로 연결
  - this`_`is`_`java
- 케밥식(Kebab case)
  - 모든 단어 소문자
  - 각 단어를 `-`로 연결
  - this`-`is`-`java

### 데이터 타입

- char : 정수
  - 각 문자에 해당하는 숫자(아스키 코드)가 있기 때문
- 오버플로우를 방지하기 위해 메모리 사용 크기(byte) 알아두기!
  - 정수 : byte(1), char(2), short(2), **int**(4), long(8)
  - 실수 : float(4), **double**(8)
  - 논리 : boolean(1)



## 3. 연산자

- 피연산자 중 문자열이 있으면 문자열로 결합

  ```
  String str1 = "JDK" + 6.0;
  String str2 = str1 + "특징";
  System.out.println(str2); // JDK6.0 특징
  
  String str3 = "JDK" + 3 + 3.0;
  String str4 = 3 + 3.0 + "JDK";
  System.out.print(str3); // JDK33.0
  System.out.print(str4); // 6.0JDK
  ```

- 'h' != "h"

  ```
  char ch = "h"; // error
  ```

  - `""` 뒤에 null이 있어서 char보다 크기가 커서 에러 남
  - char는 한 글자만 가능

- 삼항조건연산자

  ```
  조건식? 식1:식2;
  ```

  조건식이 참일 경우 식1 실행, 거짓일 경우 식2 실행



## 4. 조건문과 반복문

```
제어문 (조건식) {
    실행문;
    ...
}
```

- 제어문 = 조건문 + 반복문 + break, continue

- 조건식을 판별하여 참이면 중괄호 안의 명령어를 실행, 거짓이면 건너 뛰고 다음 명령어 실행

- 실행문이 하나일 경우, 중괄호를 생략할 수 있음

  ```
  if (i > 10) break;
  ```

### 조건문

> 조건식 결과 따라 중괄호 블록을 실행할지 여부 결정

#### if문

```
if (조건문1) {
    실행문;
} else if (조건문2) {
    실행문;
} else if (조건문3) {
    실행문;
} else {
    실행문;
}
```

- 조건문1을 먼저 판단하고, 거짓일 경우 다음 조건문을 판단
- 참일 경우, 해당 조건문의 명령어들을 실행하고, if문을 빠져나옴

```
public class IfExample {
	public static void main(String[] args) {
		int score = 85;
		if (score >= 90) {
			System.out.println('A');
		} else if (score >= 80) { // 위 조건을 만족하지 않을 때만 비교, 만족한다면 if문 전체를 빠져나옴
			System.out.println('B');
		} else if (score >= 70) {
			System.out.println('C');
		} else if (score >= 60) {
			System.out.println('D');
		} else {
			System.out.println('F');
		}
		System.out.println("종료");
	}
}
// 출력
B
종료
```

- 단순한 if-else문은 삼항연산으로 표현 가능

  ```
  (조건식) ? (값 또는 연산식) : (값 또는 연산식)
  ```

  ```
  String grade = (score>=60) ? "pass" : "fail"
  ```

- 주사위

  ```
  int num = (int)(Math.random()*6)+1;
  ```

  - 0 <= `Math.random()` < 1

### Switch문

> 변수나 연산식의 값에 따라 실행문 선택

```
switch(변수) {
    case 값1:
        ...
        break;
    case 값2:
        ...
        break;
    default:
        ...
}
```

- break를 안 쓰면 다음 케이스의 실행문도 실행됨
- default 생략 가능
- if보다 switch 권장

### 반복문

#### for문

> 반복 횟수를 알고 있을 때 주로 사용

```
for (초기화식; 조건식; 증감식) {
    실행문;
}
```

- 중첩 for문

  ```
  // 구구단
  for (int i=2; i<10; i++) {
      for (int j=1; j<10; j++) {
          System.out.println(i+"*"+j+"="+i*j);
      }
      System.out.println();
  }
  ```

- 무한 루프

  ```
  for (;;) {
      ...
  }
  ```

  - 초기화식, 조건식, 증감식 생략 가능

#### while문

> 조건에 따라 반복문을 계속할지 결정

```
while (조건문) {
    실행문;
}
```

- 중첩 while문

  ```
  // 구구단
  int i = 1;
  while (i<10) {
      int j = 2;
      while (j<10) {
          System.out.println(i+"*"+j+"="+i*j);
          j++;
      }
      System.out.println();
      i++;
  }
  ```

### 💡 입출력

- #### 출력

  ```
  System.out.println(); // 한 줄 띄움
  System.out.print();
  ```

- #### 입력

  - System.in.read()

    ```
    int keycode = System.in.read();
    ```

    - 하나의 키 코드만 읽으므로 콘솔에 입력된 문자열을 한 번에 읽을 수 없음

  - Scanner

    ```
    import java.util.Scanner; // Scanner 클래스를 사용하기 위해 필요
    Scanner sc = new Scanner(System.in); // Scanner 객체 생성
    String input = scanner.nextLine(); // 입력값을 input 변수에 저장
    ```

    - Scanner 객체를 생성하여, 콘솔에 입력된 문자열을 한 번에 읽음

🍯 자동으로 import 해주는 단축키 : `ctrl + shift + O`

### do-while문

```
// while
// while의 조건문을 바꿀 수 없으므로 while문 내에 if-break를 이용해 처리해줘야 함
while(true) {
    String input = sc.nextLine();
    int n = Integer.parseInt(input);
    if (n==0) break;
    sum += n;
}
System.out.println(sum);

// do-while
// 반복 처리를 먼저 하고 조건 비교
int n;
do {
    String input = sc.nextLine();
    n = Integer.parseInt(input);
    sum += n;
} while(n!=0); // 세미콜론 써야 함
System.out.println(sum);
```



### continue

> continue 이후의 코드를 실행하지 않고 조건식으로 돌아감 반복문을 종료하지 않고 계속 반복 수행

```
int sum = 0;
for (int i=1; i<=100; i++) {
    if (i%3==0) continue;
    sum += i;
}
```

- 3의 배수는 제외하고 더함

### break

> 반복문 종료

```
int sum = 0;
int i = 1;
while (true) {
    sum += i;
    if (sum >= 100) break;
    i += 1;
}
```

- 100 이상 되면 종료

### Label

> 바깥쪽 반복문까지 종료시키고 싶으면 해당 반복문에 라벨을 붙임

```
Outter: for(int i=0; i<10; i++) {
    for (int j=0; j<10; j++) {
        System.out.println("i: "+i+", j: "+j);
        if (j==5) break Outter; // Outter label이 붙어있는 반복문을 빠져나옴
    }
}
```

- 라벨이 없었다면 내부 반복문(j)만 종료됨



## 5. 참조 타입

> 객체(Object)의 번지를 참조하는 타입 배열, 열거, 클래스, 인터페이스 타입

| 기본 타입 변수             | 참조 타입 변수          |
| -------------------------- | ----------------------- |
| 실제 `값`을 변수 안에 저장 | `주소`를 통해 객체 참조 |

### 메모리 사용 역역

- 메소드 영역
  - JVM 시작할 때 생성
  - 로딩된 클래스 바이트 코드 내용을 분석 후 저장
  - 모든 스레드가 공유
- 힙 영역
  - JVM 시작할 때 생성
  - 객체/배열 저장
  - 사용되지 않는 객체는 Garbage Collector가 자동 제거
- JVM 스택
  - 스레드 별 생성
  - 메소드 호출할 때마다 Frame을 스택에 추가(push)
  - 메소드 종료하면 Frame 제거(pop)

### 참조 변수의 ==, != 연산

> **동일한 객체를 참조**하는지 다른 객체를 참조하는지 조사 (기본 타입 변수(char, int 등)는 변수의 **값**이 같은지 다른지 조사)

```
String str1 = new String("java");
String str2 = new String("java");
if (str1==str2) {
    System.out.println("same");
} else {
    System.out.println("not same");
}

// not same
// String의 경우 데이터의 값을 비교하고 싶을 때 equals 사용
String str1 = new String("java");
String str2 = new String("java");
if (str1.equals(str2)) {
    System.out.println("same");
} else {
    System.out.println("not same");
}

// same
```

### Null과 NullPointerException

- 예외(Exception) : 사용자의 잘못된 조작이나 잘못된 코딩으로 인해 발생하는 프로그램 오류

- NullPointerException : 참조 변수가 null 값을 가지고 있는데, 객체의 필드나 메소드를 사용하려고 했을 때 발생

  ```
  int[] intArray = null;
  inAraay[0] = 10; // NullPointerException
  ```

### String 타입

- 문자열 리터럴이 동일하다면 String 객체 공유

  ```
  String name1 = "java";
  String name2 = "java";
  // name1 == name2
  ```

- new 연산자를 이용해 객체를 생성하면, 다른 객체를 가리킴

  ```
  String name1 = new String("java");
  String name2 = new String("java");
  // name1 != name2
  ```

### 배열 타입

> 같은 타입의 데이터를 연속된 공간에 저장하는 자료구조

- 각 데이터 저장 위치는 인덱스를 부여해 접근

- 중복된 변수 선언을 줄이기 위해 사용

  ```
  // 배열을 쓰지 않는 경우
  score1 = 100;
  score2 = 88;
  score3 = 78;
  ...
  score100 = 66;
  
  // 배열을 쓰는 경우
  // 1. 배열 선언 후, 생성
  int[] nary1;
  nary1 = new int[10];
  // 2. 동시에 배열 선언, 생성
  int[] nary2 = new int[10];
  // 3. 동시에 배열 선언, 초기화
  int[] scores2 = new int[] {100, 88, 78, ... 66}
  int[] scores1 = {100, 88, 78, ... 66} // 이 경우에만 new int[] 생략 가능
  ```

- 반복문을 이용해 요소들을 쉽게 처리

  ```
  // 배열을 쓰지 않는 경우
  int sum = 0;
  sum += score1;
  sum += score2;
  ...
  sum += score100;
  
  // 배열을 쓰는 경우
  int sum = 0;
  for (int i=0; i<100; i++) {
      sum += scores[i]
  }
  ```

### 다차원 배열

```
int[][] ary2 = new int[2][3]; // 2행 3열 배열
System.out.println(ary2.length); // 2
System.out.println(ary2[0].length); // 3
```

#### 가변 배열

> 각 행의 개수를 가변적으로 설정 가능

```
int[][] vary = new int[2][];
vary[0] = new int[2];
vary[1] = new int[3];
```

- 다차원 배열의 합 구하기

  ```
  int[][] iary = {{1,2},{3,4,5}};
  int sum = 0;
  for (int i=0; i<iary.length; i++) {
      for (int j=0; j<iary[i].length; j++) {
          sum += iary[i][j];
      }
  }
  System.out.println(sum); // 15
  ```

### 복사

- 얕은 복사

  - 원래 배열의 항목이 참조하는 객체를 참조

- 깊은 복사

  ```
  // src : 원본 배열
  // srcPos : 복사할 값의 시작 인덱스
  // dest : 새 배열
  // destPos : 붙여넣을 시작 인덱스
  // length : 복사할 개수
  
  System.arraycopy(Object src, int srcPos, Object dest, int destPos, int length);
  ```

  - 배열의 항목 값 복사
  - 참조하는 객체를 별도로 생성

```
int[] ary = new int[] {10,20,30};
int[] cpy1 = new int[3];
int[] cpy2 = new int[3];

cpy1 = ary; // 얕은 복사 (주소값 복사)
System.arraycopy(ary, 0, cpy2, 0, ary.length); // 깊은 복사 (메모리와 분리하여 복사)

ary[0] = 100; // cpy1[0]은 같이 바뀌나, cpy2[0]은 바뀌지 않음

System.out.println("---원본 데이터---");
for (int i=0; i<ary.length; i++) {
    System.out.println(ary[i]);
} // 100 20 30

System.out.println("---얕은 복사---");
for (int i=0; i<cpy1.length; i++) {
    System.out.println(cpy1[i]);
} // 100 20 30

System.out.println("---깊은 복사---");
for (int i=0; i<cpy2.length; i++) {
    System.out.println(cpy2[i]);
} // 10 20 30
```

### 향상된 for문

> 배열/컬렉션 항목의 개수만큼 반복, 자동으로 for문 종료

```
int[] ary = {10,20,30,40,50};
int sum = 0;
for (int data : ary) {
    sum += data;
}
System.out.println(sum); // 150
```

💡 파이썬에서 리스트를 바로 for문에 쓰는 방법과 비슷한 듯!

```
# python
ary = [10,20,30,40,50]
sum = 0
for data in ary:
    sum += data
print(sum)
```

## 5. 참조 타입

- 배열을 이용해 로또 번호 구하기

  ```
  // 1. 1~45 정수값을 저장할 배열 선언과 할당
  int[] num = new int[46];
  
  // 2. 1에서 할당한 배열에 1~45 값 넣기
  for (int i=0; i<46; i++) {
      num[i] = i;
  }
  
  // 3. 1~45 중 랜덤 값 2개 구하여 배열 중 그 순번에 있는 배열의 값 바꾸기
  // 4. 3을 1000번 반복
  for (int j=0; j<1000; j++) {
      int a = (int)(Math.random()*45)+1;
      int b = (int)(Math.random()*45)+1;
      int tmp = num[a];
      num[a] = num[b];
      num[b] = tmp;
  }
  
  // 5. 배열의 요소 중 앞에서 6개를 로또 당첨 번호로 출력
  for (int k=1; k<7; k++) {
      System.out.print(num[k]+" ");
  }
  ```

🍯 `ctrl + shift + F` : 자동으로 줄 맞춤, 띄어쓰기

### 열거 타입

> 한정된 값만을 갖는 데이터 타입

- 열거 타입 변수 선언

  ```
  Week today;
  Week reservationDay;
  ```

- 열거 상수 값 저장

  ```
  열거타입 변수 = 열거타입.열거상수;
  ```

  ```
  Week today = Week.SUNDAY;
  ```

- 참조타입이므로 null값 저장 가능

  ```
  Week today = null;
  ```

------

- `enum`으로 열거 타입 선언

  ```
  public enum Week {
  	MONDAY,
  	TUESDAY,
  	WENDESDAY,
  	THURSDAY,
  	FRIDAY,
  	SATURDAY,
  	SUNDAY
  }
  ```

  - 상수값을 `대문자`와 `언더바`를 이용해 선언

- enum에 정의된 열거 타입 변수 사용

  ```
  public class EnumTest {
  	public static void main(String[] args) {
  		Week today = Week.WENDSDAY;
  		System.out.println(today); // WENDSDAY
  	}
  }
  ```

### 메소드

> 열거 객체는 열거 상수의 문자열을 내부 데이터로 가지고 있음

- `Calendar`는 오늘 날짜에 대한 정보를 가져올 수 있음



## 6. 클래스

### 객체 지향 프로그래밍

> OOP(Object Oriented Programming)
>
> 부품 객체를 먼저 만들고 이것들을 하나씩 조립해 완성된 프로그램을 만드는 기법

- 객체(Object)
  - 물리적으로 존재하는 것
  - 필드(속성)과 메소드(동작)로 구성된 자바 객체로 모델링 가능
  - 객체들은 서로 간에 기능(동작)을 이용하고 데이터를 주고 받음
  - 객체 간의 관계 : 집합, 사용, 상속

### 특징

#### 캡슐화(Encapsulation)

> 객체의 필드, 메소드를 하나로 묶고, 실제 구현 내용을 감추는 것 (정보 은닉)

- 외부 객체는 객체 내부 구조를 알지 못하며, 객체가 노출해 제공하는 필드와 메소드만 이용 가능
- 외부의 잘못된 사용으로 인해 객체가 손상되지 않게 하기 위함
- 접근 제한자를 사용하여 캡슐화된 멤버의 노출 여부 결정

#### 상속

> 상위 객체의 필드와 메소드를 하위 객체에게 물려주는 행위

- 하위 객체는 확장 가능 (추가적인 필드와 메소드를 가질 수 있음)
- 효과
  - 상위 객체를 재사용해서 하위 객체를 빨리 개발 가능
  - 코드 중복 줄임
  - 유지보수 용이
  - 객체의 다형성 구현

#### 다형성(Polymorphism)

> 같은 타입이지만 실행 결과가 다양한 객체를 대입할 수 있는 성질

- 부모 타입에는 모든 자식 객체가 대입
- 인터페이스 타입에는 모든 구현 객체가 대입
- 효과
  - 객체 부품화 가능
  - 유지보수 용이

## 객체와 클래스

- 클래스 : 객체를 생성하기 위한 필드와 메소드가 정의됨
- 인스턴스(instance) : 클래스로부터 만들어진 객체
- 하나의 클래스로 여러 인스턴스를 만들 수 있음

```
// 파일명과 다른 이름의 클래스는 public을 붙이지 않음
class Account {
	String account_number; // 계좌 번호
	String name; // 이름
	int balance; // 잔액
	
    // 입금
	public void deposit(int amount) {
		if (amount>0) {
			balance += amount;
		}
	}
    // 출금 : 잔액이 남아있는 경우에만 출금할 수 있게 함
	public void withdraw(int amount) {
		if (balance >= amount) {			
			balance -= amount;
		} else {
			System.out.println("잔액 부족");
		}
	}
    // 계좌 정보
	public String info() {
		return "계좌번호:"+account_number+", 이름:"+name+", 잔액:"+balance; 
	}
}

// 파일명과 같은 이름의 클래스는 public
public class AccountTest {
	public static void main(String[] args) {
		Account ac1 = new Account();
		Account ac2 = new Account();
		
		ac1.account_number = "101";
		ac1.name = "홍길동";
		ac1.balance = 100000;
		ac2.account_number = "102";
		ac2.name = "김길동";
		ac2.balance = 200000;
		
		System.out.println(ac1.info());
		System.out.println(ac2.info());
		
		ac1.deposit(10000);
		ac2.withdraw(20000);
		
		System.out.println(ac1.info());
		System.out.println(ac2.info());
	}
}
```

- 하나의 파일에 여러 개의 클래스가 있을 수 있지만, `public`은 (main이 있는) 하나의 클래스에만 붙음

### 클래스 선언

- 하나 이상의 문자
- 대문자로 시작
- `$`, `_` 외의 특수 문자 사용 불가능
- 다음 단어의 첫 글자는 대문자
- 두 개 이상의 클래스도 한 파일 안에서 선언 가능하나, 파일과 같은 이름의 클래스에만 public을 붙임

### 객체 생성과 클래스 변수

- `new`를 이용하여 클래스로부터 객체 생성
- 클래스의 용도
  - 라이브러리(API)용 : 자체적으로 실행되지 않고, 다른 클래스로부터 이용됨
  - 실행용 : main() 메소드를 가지고 있는 클래스로, 실행할 목적으로 만든 클래스

### 클래스의 구성 멤버

#### 필드(Field)

> 객체의 데이터가 저장되는 곳

#### 생성자(Constructor)

> 객체 생성 시 **초기화** 역할 담당

```
class Account {
	String account_number;
	String name;
	int balance;
	
    // 생성자
    // 생성자를 이용해 필드 값을 지정해주지 않을 경우, 해당 필드가 null 값으로 초기화된 객체가 생성됨
	public Account() {
		account_number = "100";
		name = "없음";
		balance = 0;
	}
    ...
	public String info() {
		return "계좌번호:"+account_number+", 이름:"+name+", 잔액:"+balance; 
	}
}

public class AccountTest {
	public static void main(String[] args) {
        ...
        Account ac3 = new Account();
		System.out.println(ac3.info()); // 계좌번호:100, 이름:없음, 잔액:0
	}
}
```

- new 연산자에 의해 객체 생성 시 자동으로 호출 됨
- 클래스명과 동일한 이름
- 리턴 타입을 붙이지 않음

#### 💡 오버로드

- 여러 개의 생성자를 만들 수 있음 (같은 이름을 사용)
- 매개 변수의 `개수`가 다르거나, 매개 변수의 `타입`이 달라야 함

```
public class Person {
	String name;
	int age;
	
	// 생성자
	public Person() {
		this.name = "none";
		this.age = 0;
	}
	public Person(String name, int age) {
		// 객체의 필드명과 함수의 매개변수명이 같으므로 객체의 필드명 앞에 this를 붙여야 함
		this.name = name;
		this.age = age;
	}
	public Person(String name) {
		this.name = name;
		this.age = 0;
	}
	public Person(int age) {
		this.name = "none";
		this.age = age;
	}
	
 	public String info() {
		return "이름: "+name+", 나이: "+age;
	}
}
public class Person_ex {
	public static void main(String[] args) {
		Person p = new Person();
		System.out.println(p.info()); // 이름: none, 나이: 0
		
		Person p3 = new Person("c", 20);
		System.out.println(p3.info()); // 이름: c, 나이: 20
		
		Person p4 = new Person("django");
		System.out.println(p4.info()); // 이름: django, 나이: 0
		
		Person p5 = new Person(26);
		System.out.println(p5.info()); // 이름: none, 나이: 26
		
//		Person p6 = new Person(26, "spring"); // error
	}
}
```

- `this`를 이용해 더 간단하게 생성자 만들 수 있음

  ```
  public Person() {
      this("none",0);
  }
  public Person(String name, int age) {
      this.name = name;
      this.age = age;
  }
  public Person(String name) {
      this(name,0);
  }
  public Person(int age) {
      this("none",age);
  }
  ```

  - this() : 또다른 생성자 호출, 생성자에서만 호출 가능

### 메소드(Method)

> 객체의 동작에 해당하는 실행 블록

- 필요에 의해 입력값(매개 변수, 파라미터)을 넣어야 함

- 일반적으로, public을 붙임

- 리턴 값이 있는 메소드는 반드시 해당 타입의 리턴 값을 지정해야 함

- 메소드 호출

  - 클래스 내부 메소드는 메소드 이름으로 호출

    ```
    run();
    ```

  - 클래스 외부 메소드는 객체 생성 후 참조 변수를 이용해 호출

    ```
    Car car = new Car();
    car.run();
    ```

#### 메소드 오버로딩(Overloading)

> 클래스 내에 같은 이름의 메소드를 여러 개 선언하는 것

- 하나의 메소드 이름으로 다양한 매개값 받기 위함

- 매개 변수의 타입이나 개수가 달라야 함

  ```
  int f(int x, int y) {
      ...
  }
  double f(int x, int y) {
      ...
  }
  ```

  - 메소드의 타입은 다르지만, 매개 변수의 타입과 개수가 같으므로 error (메소드 타입은 무관!)

## 인스턴스 멤버와 this

### 인스턴스 멤버

> 객체마다 가지고 있는 피드와 메소드

- 객체에 소속된 멤버이기 때문에 객체 없이는 사용 불가

  ```
  class Calculator {
  	public int add(int x, int y) {
  		return x+y;
  	}
  	public int sub(int x, int y) {
  		return x-y;
  	}
  	public int mul(int x, int y) {
  		return x*y;
  	}
  	public double div(int x, int y) {
  		return y==0? y:(double)(x/y);
  	}
  }
  
  public class CalculatorTest {
  	public static void main(String[] args) {
  		Calculator c1 = new Calculator();
  		System.out.println(c1.add(10, 20));
  		System.out.println(c1.sub(10, 20));
  		System.out.println(c1.mul(20, 8));
  		System.out.println(c1.div(2, 3));
  	}
  }
  ```

- 클래스 안의 변수를 공유하기 위해 인스턴스화 하는 것임

  - 변수들을 공유하지 않는다면 인스턴스화 할 필요 없음 => `static`

    ```
    class Calculator2 {
    	public static int add(int x, int y) {
    		return x+y;
    	}
    	public static int sub(int x, int y) {
    		return x-y;
    	}
    	public static int mul(int x, int y) {
    		return x*y;
    	}
    	public static double div(int x, int y) {
    		return y==0? y:(double)(x/y);
    	}
    }
    
    public class CalculatorTest2 {
    	public static void main(String[] args) {
            // 객체를 생성하지 않음
    		System.out.println(Calculator2.add(10, 20));
    		System.out.println(Calculator2.sub(10, 20));
    		System.out.println(Calculator2.mul(20, 8));
    		System.out.println(Calculator2.div(2, 3));
    	}
    }
    ```

    - `Math`.random()처럼 객체를 생성하지 않고 씀
    - `static` 함수는 객체를 생성하지 않고 바로 클래스에서 메소드 호출

## 정적 멤버와 static

> 클래스에 고정된 필드와 메소드

- 클래스에 소속된 멤버
- 객체 내부에 존재하지 않고, 메소드 영역에 존재
- 객체를 생성하지 않고 클래스로 바로 접근해 사용
- 필드/메소드 선언 시 `static` 붙임

```
class Product {
	int serialNum = 0;
	static int snum = 100;
	public Product() {
		serialNum++;
		snum++;
		System.out.println("serialNum:"+serialNum+", snum:"+snum);
	}
}

public class StaticTest {
	public static void main(String[] args) {
		Product[] prs = new Product[5];
		for (int i=0; i<prs.length; i++) {
			prs[i] = new Product();
		}
	}
}
// 출력
serialNum:1, snum:101
serialNum:1, snum:102
serialNum:1, snum:103
serialNum:1, snum:104
serialNum:1, snum:105
```

- serialNum은 각 객체마다 가지고 있는 변수 (객체 소속)
- snum은 각 객체가 가지고 있는 것이 아닌, 공유하는 변수 (클래스 소속)

```
class Test {
	int ival;
	static int sval; // 클래스 로딩 시(프로그램 시작 시) 변수 할당
	public void iMethod() {
		ival = 100; // instance 메소드에서 instance 변수 접근 가능
		sval = 200; // instance 메소드에서 static 변수 접근 가능
	}
	public static void sMethod() {
//		ival = 10; // static 메소드에서는 instance 변수 접근 불가능
		sval = 20; // static 메소드에서 static 변수 접근 가능
//		this.sval = 30; // static 메소드는 this 사용 불가
	}
}

public class StaticInstanceTest {
	public static void main(String[] args) {
		Test.sval = 10; // static 변수는 객체 생성 없이 클래스명으로 접근 가능
//		Test.ival = 20; // instance 변수는 클래스명으로 접근 불가능
		Test.sMethod(); // static 메소드는 객체 생성 없이 클래스명으로 호출 가능
//		Test.iMethod(); // instance 메소드는 클래스명으로 접근 불가능
		Test t = new Test();
		t.ival = 20; // instance 변수는 반드시 객체 생성하여 참조 변수를 통해 접근해야 함
		t.iMethod(); // 생성된 객체를 통해서만 호출 가능
	
	}
}
```

## final 필드와 상수(static final)

```
class MyClass {
	static final int num = 20; // 선언과 동시에 반드시 초기화
	public MyClass(int num) {
//		this.num = num; // 클래스 내 fianl 변수는 생성자나 메소드에서 변경 불가능
	}
}

public class FinalTest {
	public static void main(String[] args) {
		final int num = 10;
//		num = 20; // final 변수는 변경할 수 없음
		int num2 = 30;
		num2 = 50;
	}
}
```

### final 필드

> 최종적인 값을 갖고 있는 필드 = 값을 변경할 수 없는 필드

- 객체당 가지고 있는 불변의 인스턴스 필드 (static이 아님)

### 상수(static final)

> 상수 = **정적** final 필드

- 객체마다 가지고 있지 않음
- 메소드 영역에 클래스별로 관리되는 불변의 정적 필드
- 공용 데이터로서 사용
- 이름은 전부 대문자로 작성
- 단어는 `_`로 연결

## 패키지

```
public class Person {
	// 다른 패키지에서 필드에 접근 가능하게 하려면 public으로 선언
	// 보통은 은닉하기 위해 public을 붙이지 않음
	// 대신 getter,setter를 이용하여 다른 패키지에서도 변경할 수 있게 함
	
	String name;
	int age;
	
	// getter, setter
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getAge() {
		return age;
	}
	public void setAge(int age) {
		if (age>0) {
			this.age = age;			
		}
	}
	...
}
```

- 패키지 내에서는 서로 공유됨
  - 다른 파일의 클래스를 사용할 수 있음
  - 다른 파일에 선언된 클래스와 같은 이름의 클래스를 만들 수 없음
- 다른 패키지의 클래스를 사용하려면 패키지를 import해줘야 함
- 해당 클래스의 변수에 접근하려면, 그 변수들은 public으로 선언돼 있어야 함
- `Source - Generate Getters and Setters`를 이용해 getter, setter를 만들어 다른 패키지에서도 메소드를 통해 해당 변수의 값을 얻거나 변경할 수 있게 함

# 6. 클래스

## 접근 제한자

> 클래스 및 클래스의 구성 멤버에 대한 접근을 제한하는 역할

- `클래스` 제한 : 다른 패키지에서 클래스를 사용하지 못하도록

- `생성자` 제한 : 클래스로부터 객체를 생성하지 못하도록

- `필드`와 `메소드` 제한 : 특정 필드와 메소드를 숨김처리

- public에서 private로 갈수록 접근 제한이 강해짐

  | 접근 제한 | 적용 대상                    | 접근할 수 없는 클래스                          |
  | --------- | ---------------------------- | ---------------------------------------------- |
  | public    | 클래스, 필드, 생성자, 메소드 | 없음                                           |
  | protected | 필드, 생성자, 메소드         | 자식 클래스가 아닌 다른 패키지에 소속된 클래스 |
  | default   | 클래스, 필드, 생성자, 메소드 | 다른 패키지에 소속된 클래스                    |
  | private   | 필드, 생성자, 메소드         | 모든 외부 클래스                               |

## 어노테이션(Annotation)

> 프로그램에게 추가적인 정보를 제공해주는 메타데이터(metadata)

- 용도

  - 컴파일러에게 코드 작성 문법 에러 체크하도록 정보 제공
  - 소프트웨어 개발 툴이 빌드나 배치 시 코드를 자동 생성하게 정보 제공
  - 실행 시(런타임 시) 특정 기능 실행하도록 정보 제공

- 정의

  ```
  public @interface AnnotationName {
  }
  ```

- 적용 : `@AnnotationName`

------

## 확인 문제

- 필드 변수는 자동으로 초기화 됨

- 함수 내의 로컬 변수만 초기화 되지 않음

- 객체를 생성할 때, 내가 생성자를 호출할 필요는 없지만, 반드시 호출이 됨

  - 기본생성자(매개 변수가 없는 생성자)가 자동 생성됨

  - 생성자를 따로 만들면(오버로딩), 반드시 **기본생성자도 직접 만들어줘야 함**

    ```
    private MyClass() {} // 기본 생성자
    public MyClass(int num) {
        this.num = num;
    }
    ```

- `private` : 외부에서 객체를 생성하거나 접근할 수 없도록 함

- static 블록에서는 static 변수만 접근할 수 있음

  ```
  static int[] n = new int[10];
  static { // 정적 블록
      for (int i=0; i<n.length; i++) {
          n[i] = (int)(Math.random{}*100)+1;
      }
  }
  ```

  - static 변수의 초기화 : 정적 블록에서 하지 않으면 객체가 생성될 때마다 실행되기 때문에, 일반적으로 정적 블록에서 이루어짐

- `default` 접근 제한은 같은 패키지 내에서의 접근 허용

# 7. 상속(Inheritance)

> 자식 클래스가 부모 클래스의 멤버(필드와 메소드)를 물려받는 것

- 부모 클래스 재사용 => 자식 클래스 빨리 개발 가능
- 반복된 코드 중복 줄임
- 유지 보수 편리성 제공
- 객체 다형성 구현 가능
- 상속 대상 제한
  - 부모 클래스의 `private` 필드와 메소드
  - **다른 패키지**의 부모클래스의 `default` 필드와 메소드

## 클래스 상속(extends)

### extends

> 자식 클래스가 상속할 부모 클래스를 지정하는 키워드

- **단일** 상속 => 부모 클래스 나열 불가

  ```
  // 다중 상속 불가능
  class 자식 클래스 extends 부모클래스1, 부모클래스2 {
  }
  ```

- 부모 클래스의 메소드를 수정하고 싶을 경우 오버라이드를 통해 재정의

  - `Source - Override/Implement Methods` 💡

  ```
  @Override
  public String info() {
      return super.info()+", 전공: "+major;
  }
  ```

## 부모 생성자 호출

```
public Student(int age, String name,String major) {
    super(age, name);
    this.major = major;
}
Student s = new Student(26,"고길동","수학과");
```

### 💡 Overloading vs Overriding ❓

#### Overloading

- 한 클래스 내에 **동일한 이름의 메소드가 여러 개**
- 매개 변수의 개수나 매개 변수의 타입이 다름
- 메소드의 리턴 타입은 무관함

#### Overriding

- **상속**받은 클래스의 메소드를 **재정의**
- 리턴 타입, 메소드명, 매개변수 모두 부모와 동일해야 함
- `@Override`를 붙임
- final 붙여진 메소드는 오버라이딩 안 됨

## protected 접근 제한자

> 상속과 관련된 접근 제한자

같은 패키지에서는 default와 동일하고, **다른 패키지의 경우 자식 클래스만 접근 허용**

## 타입 변환과 다형성

- 자식 객체를 부모 타입 변수에 넣을 수 있음 (upcasting)

  ```
  Person p = new Student(26,"고길동","수학과");
  p.getMajor() // 불가능
  ```

  - 부모에 없는 필드의 값을 변경하거나 가져오는 것 불가능

- 부모 객체를 자식 타입 변수에 넣음 (downcasting)

  ```
  Student s2 = (Student)p;
  ```

### 다형성(polymorphism)

> 상속과 오버라이딩을 한 자식 클래스를 생성하여 부모 변수에 넣었을 때, 부모의 변수를 통해 오버라이딩한 메소드를 호출할 경우 자식 메소드가 호출됨

- 부모 타입에 자식 객체를 저장해도 자식 객체의 메소드를 따름

  ```
  Person p = new Student(20,"고길동","수학");
  System.out.println(p.info()); // 이름:고길동, 나이:20, 전공:수학
  ```

- 다형성을 구현하는 기술적 방법

  - 부모 타입으로 자동 변환
  - 재정의된 메소드(오버라이딩)

- 하나의 배열로 객체 관리

  ```
  static Person[] pers = new Person[10];
  
  pers[0] = new Student(20,"고길동","수학");
  pers[1] = new Student(30,"하길동","컴퓨터공학");
  pers[2] = new Professor(50,"나교수","정보과학부");
  
  for (int i=0; i<3; i++) {
      System.out.println(pers[i].info());
  }
  
  // 출력
  // 이름:고길동, 나이:20, 전공:수학
  // 이름:하길동, 나이:30, 전공:컴퓨터공학
  // 이름:나교수, 나이:50, 부서:정보과학부
  ```

### 강제 타입 변환(Casting)

> 부모 타입을 자식 타입으로 변환하는 것

- 모두 자식 타입으로 강제 타입 변환할 수 있는 것은 아님

  - ClassCastException 예외 발생 가능

- 자식 타입인지 확인 => `instanceof` 자식 클래스

  ```
  for (int i=0; i<3; i++) {
      if (pers[i] instanceof Student) {
          System.out.println(pers[i].info());
      }
  }
  // 출력
  // 이름:고길동, 나이:20, 전공:수학
  // 이름:하길동, 나이:30, 전공:컴퓨터공학
  ```

  - 교수는 나오지 않고, 학생만 출력됨

  - 오버라이딩된 메소드는 자식 클래스를 따르지만, 자식 클래스의 메소드는 사용할 수 없음

    ```
    for (int i=0; i<3; i++) {
        if (pers[i] instanceof Student) {
            System.out.println(pers[i].getMajor()); //error
        }
    }
    ```

  - 자식 클래스의 메소드를 사용하고 싶은 경우 자식 클래스로 강제 변환해줘야 함

    ```
    for (int i=0; i<3; i++) {
        if (pers[i] instanceof Student) {
            Student s = (Student)pers[i];
            System.out.println(s.getMajor());
        }
    }
    // 출력
    // 수학
    // 컴퓨터공학
    ```

## 추상 클래스 (Abstract Class)

> 실체 클래스들의 공통되는 필드와 메소드를 정의한 클래스

- 객체 생성 불가능
- **오버라이딩**하기 위해 사용
- 실체 클래스의 부모 클래스 역할
  - 실체 클래스 : 객체를 만들어 사용할 수 있는 클래스

### 추상 클래스의 용도

- 실체 클래스의 공통된 필드와 메소드의 이름을 통일
  - 여러 명이 실체 클래스를 설계할 경우, 필드/메소드가 각각 다른 이름을 가질 수 있음
- 실체 클래스를 작성할 때 시간 절약
  - 추가적인 필드와 메소드만 선언
- 실체 클래스 설계 규격을 만들고자 할 때
  - 실체 클래스가 가져야 할 필드와 메소드를 추상 클래스에 미리 정의
  - 실체 클래스는 추상 클래스를 무조건 상속 받아 작성

### 추상 메소드

> 메소드 이름은 동일하지만, 실행 내용은 실체 클래스마다 다른 메소드

------

# 🍯 워크스페이스에 파일 추가

- `File - Import - General - Existing Projects into Workspace`에서 해당 폴더 선택
  - 실제로 워크스페이스에도 추가할 거라면 `Add project to working sets` 체크
- JDK 버전이 안 맞아서 가져온 프로젝트가 실행이 안 될 수도 있음
  - 해당 프로젝트에서 `Build Path - Configure Build Path - Libraries` 가서 JDK 버전 바꾸기

# 💡 next() vs nextLine() ❓

> **next()** : `공백`(스페이스) 전까지 입력받은 문자열 반환 **nextLine()** : `엔터` 치기 전까지 쓴 문자열 모두 반환

🔒 입력하지 않았는데 다음으로 넘어가서 제대로 입력되지 않음

```
System.out.print("계좌번호: ");
String ano = scanner.nextLine();
System.out.print("계좌주: ");
String owner = scanner.nextLine();
System.out.print("초기입금액: ");
int balance = scanner.nextInt();
```

- 콘솔에 입력하고 엔터를 누를 때, 그 직전의 값을 반환하여 ano에 저장하고, 누른 엔터 값을 바로 다음 입력값으로 읽어버림

🔑 다음에 입력을 받아야 하는 경우, 그 전 값은 next()로 입력 받기

```
System.out.print("계좌번호: ");
String ano = scanner.next();
System.out.print("계좌주: ");
String owner = scanner.next();
System.out.print("초기입금액: ");
int balance = scanner.nextInt();
```

🔒 `NumberFormatException` 발생

```
System.out.print("초기입금액: ");
int balance = scanner.nextInt();
System.out.print("등급(VIP:1, Gold:2, Silver:3, Normal:4): ");
int ngrade = Integer.parseInt(scanner.nextLine());
```

- **NumberFormatException**는 숫자로 변환될 수 없는 문자열을 숫자로 변환할 경우에 발생
- nextInt() 때문에 바로 뒤에 nextLine()에 빈값이 들어가고, 그 값을 정수로 바꿀 수 없어서 발생한 듯!

🔑 다음 값을 입력받기 전에, nextLine()으로 한 줄 더 입력 받아서 엔터 값 없애기

```
System.out.print("초기입금액: ");
int balance = scanner.nextInt();
scanner.nextLine(); // 엔터 입력 받기
System.out.print("등급(VIP:1, Gold:2, Silver:3, Normal:4): ");
int ngrade = Integer.parseInt(scanner.nextLine());
```

## 추상 클래스

- `abstract`를 붙여 선언

  ```
  public abstract class Employee {
  }
  ```

- 자식 클래스는 추상 클래스의 함수를 다 구현해야 함

  - 추상 클래스에서는 쓰이지 않고 자식 클래스에만 쓰이는 필드가 있고, 그 관련 메소드를 사용해야 할 때

    ```
    // 추상 클래스 (부모)
    // 리턴 값 없이 선언만 해줌
    abstract public int getPay();
    ```

    ```
    // 추상 클래스의 자식 클래스
    @Override
    public int getPay() {
        return super.getPay()+getIncentive();
    }
    ```

  - abstract 메소드가 있으면 그 클래스도 abstract

- 추상 클래스의 객체는 생성할 수 없음 (인스턴스화 불가능)

# 8. 인터페이스

> 개발 코드와 객체가 서로 통신하는 접점

- 추상 클래스의 추상화 정도가 큰 것
- 개발 코드는 **인터페이스의 메소드만 알고 있으면 됨**
- 인터페이스로 상속 받은 자식들을 하나로 묶을 수 있음 (upcasting)
- 개발 코드가 객체에 종속되지 않게 => 객체 교체할 수 있도록 함
- 개발 코드 변경 없이 리턴 값 또는 실행 내용이 다양해질 수 있음(다형성)

## 선언

```
interface 인터메이스명 {
    타입 상수명 = 값;
    타입 메소드명(매개변수, ...);
    default 타입 메소드명(매개변수, ...){
        ...
    }
    static 타입 메소드명(매개변수) {
        ...
    }
}
```

- 상수 필드만 선언 가능
  - 데이터 저장하지 않음
- 상수 필드는 모두 public static final로 선언됨
- 상수 필드는 선언과 동시에 초기값을 지정해야 함
  - static 블록 작성이 불가능함

## 구현

- 프로젝트에서 `New - Interface`로 생성

- 인터페이스를 상속 받을 때는 `implements` 키워드로 명시

  ```
  pubblic class 구현 클래스명 implements 인터페이스명 {
      // 인터페이스에 선언된 추상 메소드의 실체 메소드 선언
  }
  ```

- 여러 개의 인터페이스를 상속 받을 수 있음

- 인터페이스도 `instanceof`를 이용해 해당 인터페이스를 상속받았는지 확인할 수 있음

# 9. 중첩 클래스와 중첩 인터페이스

## 중첩 클래스

> 클래스 멤버로 선언된 클래스

```
class ClassName {
    class NestedClassName { // 중첩 클래스
    }
}
```

- 멤버 클래스

  - 인스턴스 멤버 클래스 : A 객체를 생성해야만 사용할 수 있는 B 중첩 클래스

    ```
    class A {
        class B { ... }
    }
    ```

  - 정적 멤버 클래스 : A 클래스로 바로 접근할 수 있는 B 중첩 클래스

    ```
    class A {
        static class B { ... }
    }
    ```

- 로컬 클래스 : method()가 실행할 때만 사용할 수 있는 B 중첩 클래스

  ```
  class A {
      void method() {
          class B { ... }
      }
  }
  ```

## 중첩 인터페이스

> 클래스 멤버로 선언된 인터페이스

- UI 컴포넌트 내부 이벤트 처리에 많이 활용

```
class ClassName {
    interface NestedInterfaceName { // 중첩 인터페이스
    }
}
class A {
	class B {
		B() {} // 생성자
		int n; // 인스턴스 필드
		void method() {} // 인스턴스 메소드
//		static int sn; // static 필드 선언 불가능
//		static void smethod() {}; // static 메소드 선언 불가능
	}
}

class C {
	// static inner class
	static class D {
		D() {}; // 생성자
		int n; // 인스턴스 필드
		void method() {}; // 인스턴스 메소드
		static int sn; // static 필드
		static void smethod() {}; // static 메소드
	}
}

public class InnerClassTest {
	
	public static void func() {
		class F {
			F() {}; // 생성자
			int n; // 인스턴스 필드
			void method() {}; // 인스턴스 메소드
//			static int sn; // static 필드 선언 불가능
//			static void smethod(); // static 메소드 선언 불가능
		}
		F f = new F();
		f.method();
	}
	
	public static void main(String[] args) {
		A a = new A();
		A.B b = a.new B();
		b.method();
		b.n = 10;
		
		C.D d = new C.D(); // D가 static이라 C를 생성하지 않고도 쓸 수 있음
		d.n = 10;
		C.D.sn = 20;
		C.D.smethod();
	}
}
```

## 익명 객체

> 이름이 없는 객체

- 단독 생성 불가 : 클래스 상속하거나 인터페이스 구현해야만 생성 가능
- 사용 위치
  - 필드의 초기값, 로컬 변수의 초기값, 매개변수의 매개값으로 주로 대입
  - UI 이벤트 처리 객체나 스레드 객체를 간편하게 생성할 목적으로 주로 활용

```
class A {
    Parent field = new Parent() {
        int childField;
        void childMethod() {}
        // Parent의 메소드를 오버라이딩
        @Override
        void parentMethod() {}
    }
}
interface IBase {
	void method();
}
public class AnonymousTest {

	public static void main(String[] args) {
		IBase b = new IBase() { // IBase를 상속 받아 익명 클래스를 정의하고 오버라이딩 후, 생성함
            @Override
            public void method() {
                System.out.println("구현 메소드");
            }
        };
        b.method();
	}
}
class LoginClickable implements Clickable {
	@Override
	public void iclick() {
		System.out.println("로그인 처리");
	}
}
...
Button libtn = new Button();
libtn.addClickListenr(new LoginClickable());
libtn.click();
Button libtn = new Button();
libtn.addClickListenr(new Button.Clickable() {
    @Override
    public void iclick() {
        System.out.println("로그인 처리");
    }
});
libtn.click();
```

# 10. 예외 처리

## 예외와 예외 클래스

### 오류 종류

- 에러(Error)
  - 하드웨어의 잘못된 동작 또는 고장으로 인한 오류
  - 에러가 발생되면 프로그램 종료
  - 정상 실행 상태로 돌아갈 수 없음
- 예외(Exception)
  - 사용자의 잘못된 조작 또는 **개발자의 잘못**된 코딩으로 인한 오류
  - 예외가 발생되면 프로그램 종료
  - 예외 처리 추가하면 정상 실행 상태로 돌아갈 수 있음

### 예외 종류

- 일반(컴파일 체크) 예외 (Exception)
  - 예외 처리 코드 없으면 컴파일 오류 발생
- 실행 예외 (RuntimeException)
  - 예외 처리 코드를 생략하더라도 컴파일이 되는 예외
  - 경험 따라 예외 처리 코드 작성 필요

## 9장 확인 문제 풀이

### 1. 중첩 멤버 클래스

- 인스턴스 멤버 클래스는 바깥 클래스의 객체가 있어야 사용 가능
  - 바깥 클래스가 생성되어 있으니 그 필드와 메소드를 사용할 수 있음
- 정적 멤버 클래스는 바깥 클래스 생성 없이 사용 가능
  - 만들어지지 않은 인스턴스 필드는 사용할 수 없음

### 2. 로컬 클래스

- 메소드 내부에 선언된 클래스
- 바깥 클래스 객체가 생성된 후에 사용할 수 있으므로 바깥 클래스의 모든 필드와 메소드 사용 가능
- static 키워드를 이용해서 정적 클래스로 만들 수 없음
  - 메소드는 호출되었다가 끝나면 사라지므로 안에서 static을 쓰지 않음
- **final 특성을 가진 매개 변수나 로컬 변수만 로컬 클래스 내부에서 사용할 수 있음**

### 3. 익명 객체

- 클래스를 상속하거나 인터페이스를 구현해야만 생성될 수 있음
- 필드, 매개 변수, 로컬 변수의 초기값으로 주로 사용됨
- 생성자 선언 불가
  - 부모의 생성자 호출
- 부모 클래스나 인터페이스에 선언된 필드와 메소드 이외의 다른 필드와 메소드를 선언할 수 있지만 익명 객체 내부에서만 사용 가능

### 6. 컴파일 에러 원인

```
String nickName = null;
nickName = chatId;
Chat chat = new Chat() {
    @Override
    public void start() {
        ...
        String message = ... + nickname + ...;
        ...
    }
}
```

- Chat 클래스의 자식을 부모 타입에 upcasting한 것

- 익명 객체를 생성하는 과정에서 nickName을 사용함

  - nickName은 final로 선언되지 않은 지역 변수이므로 사용할 수 없음

- 선언과 함께 초기화 하면 자동으로 final로 선언됨

  ```
  String nickName = chatId; // final
  ```

  - 자바 낮은 버전에서는 지원하지 않는 경우도 있으니 final을 쓰는 게 좋음

# 10. 예외 처리

```
public class ExceptionSample1 {

	public static void main(String[] args) {
		String str = "hi";
		int a=10, b=0;
		try {
			System.out.println(str.toString());
			System.out.println(a/b);
		} catch (NullPointerException e) {
			// 예외 상황이 발생했을 때 처리할 사항
			System.out.println(e.getMessage());
		} catch (ArithmeticException e) {
			System.out.println(e.getMessage());
		} catch (Exception e) {
			System.out.println(e.getMessage());
		}
		
		System.out.println("프로그램 종료");
	}
}
```

- `try` ~ `catch`를 이용하여 예외 처리

- 예외 처리도 순서대로 하므로 Exception(모든 예외 상황)은 제일 나중에 처리

- `getMessage()` : 에러 메시지

- try의 위치에 따라 달라짐

  - 한번 예외 발생하면 반복문 종료

    ```
    public class ExceptionSample2 {
    
    	public static void main(String[] args) {
    		int[] arr1 = {10,20,30,40};
    		int[] arr2 = {2,0,6};
    
    		try {
    			for (int i = 0; i < arr1.length; i++) {
    					System.out.println(arr1[i] / arr2[i]);
    			}
    		} catch (ArithmeticException e) {
    			System.out.println(e.getMessage());
    		} catch (ArrayIndexOutOfBoundsException e) {
    			System.out.println(e.getMessage());
    		}
    	}
    }
    
    // 출력
    // 5
    // / by zero
    ```

  - 하나하나씩 예외처리하므로 예외가 발생해도 다음 반복문 실행

    ```
    public class ExceptionSample2 {
    
    	public static void main(String[] args) {
    		int[] arr1 = {10,20,30,40 };
    		int[] arr2 = {2,0,4};
    
    		for (int i = 0; i < arr1.length; i++) {
    			try {
    				System.out.println(arr1[i] / arr2[i]);
    			} catch (ArithmeticException e) {
    				System.out.println(e.getMessage());
    			} catch (ArrayIndexOutOfBoundsException e) {
    				System.out.println(e.getMessage());
    			}
    		}
    	}
    }
    
    // 출력
    // 5
    // by zero
    // 5
    // Index 3 out of bounds for length 3
    ```

## try-catch-finally

- finally : 예외가 발생하든 안 하든 항상 실행
  - 중간에 예외가 발생하거나 return 등으로 try문이 종료되더라도 실행됨

## throw

- 예외를 직접 만들어서 던질 수 있음

  ```
  public class ExceptionSample6 {
  
  	public static void main(String[] args) {
  		try {
  			throw new Exception("내가 만든 예외");
  		} catch (Exception e) {
  			System.out.println(e.getMessage());
  		}
  	}
  }
  ```

- 원래는 던져야 하는데(throw), 원래 있는 함수에서는 예외 던지는 것까지 포함되어 있어서 아까 따로 throw하지 않아도 예외 처리가 된 것

- 함수 내에서 던져지는 예외가 있다면 함수 정의할 때`throws` 써야 함

  ```
  public class ExceptionSample7 {
  	public static void method1() throws Exception {
  		method2();
  	}
  	public static void method2() throws Exception {
  		String str = null;
  		try {
  			System.out.println(str.toString());
  		} catch (NullPointerException e) {
  			System.out.println(e.getMessage());
  			throw new Exception("다시 생성한 예외");
  		}
  	}
  	public static void main(String[] args) {
  		try {
  			method1();
  		} catch (Exception e) {
  			System.out.println(e.getMessage());
  		}
  	}
  }
  ```

## 사용자 정의 예외와 예외 발생

- 선언 방법

  ```
  public class XXXException extends [Exception | RuntimeException ] {
      public XXXException() {}
      public XXXException(String message) {
          super(message);
      }
  }
  ```

- 예외 발생 시키기

  ```
  throw new XXXException();
  throw new XXXException("메시지");
  ```

# 12. 멀티 스레드

## 프로세스(process)

> 실행 중인 하나의 프로그램

## 멀티 태스킹

> 두가지 이상의 작업을 동시에 처리하는 것

- 멀티 프로세스 : 독립적으로 프로그램들을 실행하고 여러 가지 작업 처리

- 멀티 스레드 : 한 개의 프로그램을 실행하고 내부적으로 여러 가지 작업 처리

  - 메인은 하나의 스레드! 우리는 여태까지 싱글 스레드로 작업하고 있었음

- Thread.currentThread() : 현재 실행 되고 있는 스레드

- Thread.currentThread().getName() : 현재 실행되고 있는 스레드의 이름

- 스레드 이름은 Thread-`N` (기본값)

  ```
  Thread thread1 = new Thread();
  System.out.println(thread1.getName()); // Thread-0
  ```

  - 이름 정해줄 수 있음

    ```
    Thread thread1 = new Thread("ThreadA");
    System.out.println(thread1.getName()); // ThreadA
    ```

## 스레드 우선 순위

- 동시성 : 멀티 작업을 위해 **하나의 코어**에서 **멀티 스레드**가 번갈아가며 실행하는 성질
- 병렬성 : 멀티 작업을 위해 **멀티 코어**에서 **개별 스레드**를 동시에 실행하는 성질

### 스레드 스케줄링

- 스레드의 개수가 코어의 수보다 많을 경우
  - 스레드를 어떤 순서로 동시성으로 실행할 것인가 결정
  - 스케줄링에 의해 스레드들은 번갈아가며 run() 메소드를 조금씩 실행
- 자바의 스레드 스케줄링 : 우선 순위 방식과 순환 할당 방식 사용

#### 우선 순위 (Priority) 방식

- 코드로 제어 가능
- 우선 순위가 높은 스레드가 실행 상태를 더 많이 가지도록 스케줄링
- 1~10의 값을 가지며, 기본은 5

#### 순환 할당 (Round-Robin) 방식

- 코드로 제어 불가능
- 시간 할당량(Time Slice)을 정해서 하나의 스레드를 정해진 시간만큼 실행

## 동기화 메소드와 동기화 블록

> 단 하나의 스레드만 실행할 수 있는 스레드나 블록

- `synchronized` : 하나의 스레드가 호출하면 다른 스레드는 이미 실행되고 있는 스레드가 끝날 때까지 대기함

- 동기화 메소드

  ```
  public synchronized void method() {
      ... // 단 하나의 스레드만 실행
  }
  ```

- 동기화 블록

  ```
  public void method() {
      ... // 여러 스레드가 실행 가능
      synchronized(공유객체) { // 공유 객체가 객체 자신이면 this를 넣을 수 있음
          ... // 단 하나의 스레드만 실행
      }
      ... // 여러 스레드가 실행 가능
  }
  ```

## 스레드 상태

- 스레드의 일반적인 상태
  - 스레드 객체 생성 -> `실행 대기 <-> 실행 (반복)` -> 종료

## 스레드 상태 제어

> 실행 중인 스레드의 상태를 변경하는 것

## 10장 확인 문제 풀이

### 1. 예외

- 사용자가 만든 예외도 처리할 수 있음

### 2. try-catch-finally

- try {} 블록에서 return문을 사용해도 finally {} 블록은 실행됨

### 3. throws

- 새로운 예외를 발생시키기 위해 사용 => `throw`

### 4. throw

- 예외를 호출한 곳으로 떠넘기기 위해 메소드 선언부에 작성됨 => `throws`

### 5. 예외 처리

- try {method1();} catch(Exception e) {} catch(ClassNotFoundException e) {}
  - 컴파일 에러
  - 상위 예외를 먼저 적으면 안 됨

### 6.

- 변수에 값을 저장할 때, 그 값에서 예외가 발생하면 그 이전값이 유지됨
- 예외 처리를 해도, finally는 실행함

### 7.

- 에러 메시지에 특정 메시지를 저장

  ```
  public XXXException(String message) {
      super(message);
  }
  ```

- 에러 발생 시키기

  ```
  throw new NotExistIDException("아이디가 존재하지 않습니다.");
  ```

- 메시지 호출

  ```
  e.getMessage() // 아이디가 존재하지 않습니다.
  ```

# 11. 멀티 스레드

- start() : 스레드를 생성하여 동시에 실행(스레드의 run함수 실행)

- run() : 스레드로 실행할 내용을 넣음

  - run으로 호출할 경우, 해당 명령어들이 다 실행된 후 다음 코드 실행됨

- 매개변수로 runnable 객체를 넣어주면, runnable의 run을 실행함

  ```
  Thread thread = new BeepThread(new BeepTask());
  ```

  - 다른 클래스의 기능을 갖다 쓰고 싶을 때 사용

    - runnable은 다른 걸 상속받지 않고, runnable은 인터페이스이므로, 다른 걸 더 상속받을 수 있음

      ```
      public class BeepTask implements Runnable {
          @Override
      	public void run() { ... }
      }
      ```

    - 일반 thread는 이미 Thread를 상속받고 있어서 다른 클래스를 상속받을 수 없음

- synchronized(동기화)

  - 하나의 스레드만 접근할 수 있도록 함

## 스레드 상태

### 일시 정지 상태

- CPU 할당 시간을 갖지 않음

## 스레드 상태 제어

- sleep(), join(), wait() => 일시 정지
- interrupt(), notify(), notifyAll() => 실행 대기
- wait으로 일시 정지되면 notify/notifyAll로 깨워줌

### sleep()

> 주어진 시간 동안 일시 정지

- 얼마 동안 일시 정지 상태로 있을 것인지 밀리세컨드 단위로 지정
- interrupt() 호출하여 예외 처리

### yield()

> 다른 스레드에게 실행 양보

### join()

> 다른 스레드의 종료를 기다림

### 스레드간 협업

- wait(), notify(), notifyAll()
- 동기화 메소드 또는 블록에서만 호출 가능한 Object의 메소드
- 두 개의 스레드가 교대로 번갈아가며 실행해야 할 경우 주로 사용
- 데이터를 소비자가 사용하고, 생산자 스레드(데이터를 채워넣음)를 깨워야 함 -> 다시 소비자에게 데이터를 쓰라고 깨움

## 데몬(daemon) 스레드

> 주 스레드의 작업을 돕는 보조적인 역할을 수행하는 스레드

- 주 스레드가 종료되면 데몬 스레드는 강제 자동 종료

- ```
  setDaemon(true)
  ```

  - start() 하기 전에 호출, 그렇지 않으면 IllegatThreadStateException 발생

## 스레드 그룹

> 관련된 스레드를 묶어 관리할 목적으로 이용

- 스레드 그룹은 계층적으로 하위 스레드 그룹을 가질 수 있음

- 스레드는 반드시 하나의 스레드 그룹에 포함

- `getName()` : 스레드 그룹 이름 얻기

- 생성

  ```
  ThreadGroup tg = new ThreadGroup(String name);
  ThreadGroup tg = new ThreadGroup(ThreadGroup parent, String name); // 부모를 지정
  ```

# 15. 컬렉션 프레임워크

> 객체들을 효율적으로 추가, 삭제, 검색할 수 있도록 제공되는 컬렉션 라이브러리

- 배열의 문제점
  - 저장할 수 있는 객체 수가 배열을 생성할 때 결정됨
    - 불특정 다수를 객체를 저장하기에는 문제
  - 객체를 삭제했을 때 해당 인덱스가 비게 됨
    - 객체를 저장하려면 어디가 비어있는지 확인해야 함
- java.util 패키지에 포함
- 인터페이스를 통해서 정형화된 방법으로 다양한 컬렉션 클래스 이용

| 인터페이스 분류 | 특징 ⭐                                           | 구현클래스                              |
| --------------- | ------------------------------------------------ | --------------------------------------- |
| List            | - **순서**를 유지하고 저장 - **중복 저장** 가능  | ArrayList, Vector, LinkedList           |
| Set             | - 순서를 유지하지 않고 저장 - 중복 저장 안 됨    | HashSet, TreeSet                        |
| Map             | - `키`와 값의 쌍으로 저장 - 키는 중복 저장 안 됨 | HashMap, Hashtable, TreeMap, Properties |

## List

- 인덱스로 관리
- 중복해서 객체 저장 가능

```
// 객체 추가
boolean add(E e) // 주어진 객체를 맨끝에 추가
void add(int index, E element) // 주어진 인덱스에 객체를 추가
set(int index, E element) // 주어진 인덱스에 저장된 객체를 주어진 객체로 바꿈

// 객체 검색
boolean contains(Object o) // 주어진 객체가 저장되어 있는지 여부
E get(int index) // 주어진 인덱스에 저장된 객체를 리턴
isEmpty() // 컬렉션이 비어있는지 조사
int size() // 저장되어 있는 전체 객체 수를 리턴

// 객체 삭제
void clear() // 저장된 모든 객체를 삭제
E remove(int index) // 주어진 인덱스에 저장된 객체를 삭제
boolean remove(Object o) // 주어진 객체를 삭제
```

### ArrayList

```
ArrayList list = new ArrayList();		
ArrayList<String> list = new ArrayList<String>(); // 제너릭
```

- 저장 용량(capacity)
  - 초기 용량 : 10 (따로 지정 가능)
  - 저장 용량을 초과한 객체들이 들어오면 자동으로 늘어나며, 고정도 가능
  - 실행속도가 빨라야 하면, 용량을 크게 초기화하고 시작
- 객체 제거 : 바로 뒤 인덱스부터 마지막 인덱스까지 모두 앞으로 1씩 당겨짐

### Vector

```
List<E> list = new Vector<E>();
```

- 스레드 동기화(synchronization) : 복수의 스레드가 동시에 Vector에 접근해 객체를 추가, 삭제하더라도 스레드에 안전(thread safe)

### LinkedList

```
List<E> list = new LinkedList<E>();
```

- 인접 참조를 링크해서 체인처럼 관리
- 특정 인덱스에서 객체를 제거하거나 추가하게 되면 바로 앞뒤 링크만 변경
- **빈번한 객체 삭제와 삽입이 일어나는 곳에서는 ArrayList보다 좋은 성능**

## Set

- 저장 순서가 유지되지 않음
- 객체 중복 저장 불가
- 하나의 null만 저장 가능

```
// 객체 추가
boolean add(E e) // 주어진 객체를 저장, 객체가 성공적으로 저장되면 true 리턴, 중복이면 false 리턴

// 객체 검색
boolean contains(Object o) // 주어진 객체가 저장되어 있는지 여부
isEmpty() // 컬렉션이 비어있는지 조사
Iterator<E> iterator // 저장된 객체를 한번씩 가져오는 반복자 리턴
int size() // 저장되어 있는 전체 객체 수를 리턴

// 객체 삭제
void clear() // 저장된 모든 객체를 삭제
boolean remove(Object o) // 주어진 객체를 삭제
```

### HashSet

```
set<E> set = new HashSet<E>();
```

- 동일 객체 및 동등 객체는 중복 저장하지 않음
- hashCode(), equals()를 이용해 같은 객체인지 판단

### TreeSet

- 데이터가 정렬됨

## Map

- 키(key)와 값(value)으로 구성됨 Map.Entry 객체를 저장하는 구조
  - Entry는 Map의 이너 클래스
- 키와 값은 모두 객체
- 키는 중복 불가, 값은 중복 가능

```
// 객체 추가
V put(K key, V value) // 주어진 키와 값을 추가, 저장이 되면 값을 리턴

// 객체 검색
boolean containsKey(Object key) // 주어진 키가 있는지 여부
boolean containsValue(Object value) // 주어진 값이 있는지 여부
Set<Map.Entry<K,V>> entrySet() // 키와 값의 쌍으로 구성된 모든 Map.Entry 객체를 Set에 담아서 리턴
V get(Object key) // 주어진 키의 값을 리턴
boolean isEmpty() // 컬렉션이 비어있는지 여부
Set<K> keySet() // 모든 키를 Set 객체에 담아서 리턴
int size() // 저장된 키의 총 수를 리턴
Collection<V> values() // 저장된 모든 값을 Collection에 담아서 리턴

// 객체 삭제
void clear() // 저장된 모든 Map.Entry(키와 값)를 삭제
V remove(Object key) // 주어진 키와 일치하는 Map.Entry를 삭제하고 값을 리턴
```

### HashMap

- 키 객체는 `hashCode()`와 `equals()`를 재정의해 동등 객체가 될 조건을 정해야 함
- 키 타입은 String 많이 사용
  - String은 문자열이 같을 경우 동등 객체가 될 수 있도록 hashCode()와 equals() 메소드가 재정의되어 있기 때문

### HashTable

- 키 객체 만드는 법은 HashMap과 동일
- 스레드 동기화가 된 상태
  - 복수의 스레드가 동시에 hashtable에 접근해서 객체를 추가, 삭제하더라도 스레드에 안전

### Properties

- 키와 값을 String 타입으로 제한

- 프로퍼티(~.properties) 파일을 읽어들일 때 주로 사용

- 프로퍼티/XML 파일 만들기

  ```
  import java.io.FileOutputStream;
  import java.io.IOException;
  import java.util.Properties;
  
  public class PropertiesExample {
  
  	public static void main(String[] args) throws IOException {
  		Properties prop = new Properties();
  		prop.setProperty("driver", "oracle.jdbc.OracleDriver");
  		prop.setProperty("url", "jdbc:oracle:thin:@localhost:1521:xe");
  		prop.setProperty("username", "hr");
  		prop.setProperty("password", "hr");
  		
          // properties 파일 만들기
  		FileOutputStream out1 = new FileOutputStream("db.properties");
  		prop.store(out1, "database set");
  		
          // XML 파일 만들기
  		FileOutputStream out2 = new FileOutputStream("db.xml");
  		prop.storeToXML(out2, "database set", "utf-8");
  	}
  }
  ```

  - 코드 실행한 뒤 해당 프로젝트에서 `F11` 누르면 properties/XML 파일 생성됨

## 검색 기능을 강화시킨 컬렉션

- 계층 구조 활용 : `이진 트리(binary tree)`를 사용하기 때문에 검색 속도 향상

### TreeSet

- 이진 트리 기반의 Set 컬렉션
- 왼쪽, 오른쪽 자식 노드를 참조하기 위한 두 개의 변수로 구성

### TreeMap

- 이진 트리 기반의 Map 컬렉션
- 키와 값이 저장된 Map.Entry를 저장
- 왼쪽, 오른쪽 자식 노드를 참조하기 위한 두 개의 변수로 구성

### 

## 동기화된(synchronized) 컬렉션

- List, Map, Set을 `synchronizedXXX()` 메소드로 동기화

## Singleton

> 단 하나만 생성될 수 있는 객체

```
class SingleTon {
	private static SingleTon instance = new SingleTon(); // static 함수에선 static 변수만 접근 할 수 있으므로 static으로 선언
	public static SingleTon getInstance() { // 다른 패키지에서도, 객체 생성 없이 쓰려면 public
		return instance;
	}
	private SingleTon() {}; // private로 외부에서 객체 생성 불가
}

public class SingleTonTest {
	public static void main(String[] args) {
//		SingleTon t = new SingleTon(); // 객체 생성 불가 (생성자가 private이므로)
		SingleTon t1 = SingleTon.getInstance();
		SingleTon t2 = SingleTon.getInstance(); // t1, t2는 동일 객체 참조
	}
}
```

- 전체 프로그램에서 단 하나의 객체만 만들도록 보장해야 하는 경우 => `Singleton`
- 외부에서 생성자 호출할 수 없도록, 생성자 앞에 `private` 붙임
- `private static` 필드로 자신의 객체 생성
- 외부에서 호출할 수 있도록 `public static getInstance()` 선언, 자신의 객체 리턴

## 상속관계

- 클래스는 다중 상속 불가능 => 단일 상속 ⭐

## 포함관계(composite)

- 한 클래스의 멤버 변수로 다른 클래스를 선언하는 것
- 작은 단위의 클래스를 먼저 만들고, 이들을 조합해서 하나의 커다란 클래스를 만듦

## 오버라이딩(overriding)

> 조상 클래스로부터 **상속받은 메서드**의 내용을 상속받는 클래스에 맞게 **변경**하는 것

- 선언부가 같아야 함
  - 이름, 매개 변수, 리턴 타입
- 접근제어자를 좁은 범위로 변경할 수 없음
- 조상 클래스의 메서드보다 많은 수의 예외를 선언할 수 없음

### 오버로딩 vs 오버라이딩

- 오버로딩 : 기존에 없는 새로운 메서드를 정의하는 것
- 오버라이딩 : 상속 받은 메서드의 내용을 변경하는 것

## 제어자(modifier)

- 접근 제어자 : public, protected, default, private

- 그 외 제어자 : static,

   

  final

  , abstract, native, transient, synchronized, volatile, strictfp

  - final

     

    ⭐

    - 클래스 : 다른 클래스의 조상이 될 수 없음
    - 메서드 : 오버라이딩을 통해 재정의될 수 없음
    - 멤버 변수, 지역 변수 : 값을 변경할 수 없는 상수가 됨

## 캡슐화

> 변수를 숨김

- `private` => getter, setter 이용
- 외부로부터 데이터를 보호
- 외부에는 불필요한, 내부적으로만 사용되는 부분을 감추기 위함

## 다형성

> 하나의 참조 변수로 여러 타입의 객체를 참조할 수 있는 것

- 상속과 오버라이딩이 이뤄져야 함

- 조상 타입의 참조 변수로 자손 타입의 인스턴스를 참조할 수 있지만, 반대로 자손 타입의 참조 변수로 조상 타입의 인스턴스를 참조할 수는 없음

- Up-casting : 자손 타입 -> 조상 타입 (형변환 생략 가능) Down-casting : 조상 타입 -> 자손 타입 (형변환 생략 불가능)

  ```
  Car car = null;
  FireEngine fe1 = new FireEngine();
  FireEngine fe2 = null;
  car = fe1; // 자손 -> 조상
  // car.water(); // 자손에만 있는 메소드 불가능
  fe2 = (FireEngine)car; // 조상 -> 자손
  fe2.water();
  ```

- `instanceof` : 참조 변수가 참조하는 인스턴스의 실제 타입을 체크하는 데 사용

- 참조형 매개변수는 메서드 호출 시, **자신과 같은 타입 또는 자손 타입**의 인스턴스를 넘겨줄 수 있음

## 추상 클래스 (abstract class)

- `추상 메서드`(함수의 선언부만 있고 구현부가 없는 메서드)를 포함하고 있는 클래스

  ```
  abstract void method();
  ```

- 일반 메서드가 추상 메서드를 호출할 수 있음

## 인터페이스(interface)

> 실제 구현된 것이 전혀 없는, 추상화 정도가 높은 추상 클래스

- 추상 메서드와 상수만을 멤버로 가질 수 있음
- 인스턴스를 생성할 수 없고, 클래스 작성에 도움을 줄 목적으로 사용됨
- `implements`를 이용해 상속받을 수 있으며, 다중 상속 가능

# 13. 제네릭

> 제네릭 타입 : 타입을 파라미터로 가지는 클래스와 인터페이스

- 선언 시 클래스/인터페이스 이름 뒤에 `<타입 파라미터>` 붙임

- `컴파일 단계`에서 **잘못된 타입이 사용될 수 있는 문제** 제거 가능

- 컬렉션, 람다식, 스트림, NIO에서 널리 사용

- 컴파일 시 강한 타입 체크 가능

- 타입 변환 제거 가능 ⭐

  ```
  List list = new ArrayList();
  list.add("hello");
  String str = (String) list.get(0);
  ```

  ```
  List<String> list = new ArrayList<String>();
  list.add("hello");
  String str = list.get(0);
  ```

- 7.0 이상부터는 생성할 때 `<>` 안에 타입 안 써도 됨

  ```
  List<String> list = new ArrayList<>();
  ```

- upcasting이 아닌 것으로 바뀜

  ```
  List<String> list = new ArrayList<String>(); // ArrayList var1 = new ArrayList();
  Object[] arr = new Character[10]; // Character[] var2 = new Character[10];
  ```

## 멀티 타입 파라미터

- 제너릭 타입은 두 개 이상의 타입 파라미터 사용 가능

## 제네릭 메소드

> 매개 변수 타입과 리턴 타입으로 타입 파라미터를 갖는 메소드

```
public <T> Box<T> boxing(T t) { ... }
```

## 제한된 타입 파라미터

> 타입 파라미터에 지정되는 구체적인 타입 제한

```
public <T extends Number> int compare(T t1, T t2) { ... }
```

## 와일드카드 타입

- 제네릭 타입<?> : Unbounded Wildcards (제한 없음)
- 제네릭 타입<? extends 상위 타입> : Upper Bounded Wildcards (상위 클래스 제한)
- 제네릭 타입<? super 하위 타입> : Lower Bounded Wildcards (하위 클래스 제한)

## 제네릭 타입의 상속과 구현

- 제네릭 타입을 부모 클래스로 사용할 경우

  - 타입 파라미터는 자식 클래스에도 기술해야 함

    ```
    public class ChildProduct<T, M> extends Product<T, M> { ... }
    ```

# 14. 람다식

> 익명 함수를 생성하기 위한 식

```
(타입 매개변수, ...) -> { 실행문; ... }
(int a) -> { System.out.println(a); }
```

- 코드가 간결해짐
- 컬렉션 요소(대용량 데이터)를 필터링 또는 매핑해 쉽게 집계
- 매개 타입 생략 가능 (런타임 시 대입값 따라 자동 인식)
- 하나의 매개변수만 있을 경우 `()` 생략 가능 하나의 실행문만 있을 경우 `{}` 생략 가능
- 실행문에 return만 있을 경우 `{}` 생략 가능

## 타겟 타입과 함수적 인터페이스

- 타겟 타입

  ```
  인터페이스 변수 = 람다식;
  ```

  - 람다식이 대입되는 인터페이스
  - 익명 구현 객체를 만들 때 사용할 인터 페이스

- 함수적 인터페이스

  - ```
    @FunctionalInterface
    ```

     

    어노테이션

     

    ⭐

    - 하나의 추상 메소드만을 가지는지 컴파일러가 체크
    - 두 개 이상의 추상 메소드가 선언되면 컴파일 오류

## 클래스 멤버와 로컬 변수 사용

- 람다식은 함수적 인터페이스의 익명 구현 객체 생성
- 람다식에서 사용하는 외부 로컬 변수는 `final` 특성
  - 지역 변수를 이너클래스 안에서 변경하면 컴파일 오류 ⭐
- 람다식 실행 블록에는 클래스의 멤버인 필드와 메소드를 제약 없이 사용
- 람다식 실행 블록 내에서 `this`는 **람다식을 실행한 객체**

## 표준 API의 함수적 인터페이스

### Consumer

- 매개값만 있고 리턴값이 없는 추상 메소드 `accept()`를 가짐

### Supplier

- 매개값은 없고 리턴값만 있는 추상 메소드 `getXXX()`를 가짐

### Function

- 매개값과 리턴값이 모두 있는 추상 메소드(`applyXXX()`)를 가짐
- 주로 매개값을 리턴값으로 매핑(타입 변환)할 때 사용

### Operator

- 매개값과 리턴값이 모두 있는 추상 메소드(`applyXXX()`)를 가짐
- 주로 매개값을 연산하고 동일한 타입의 리턴값 제공

### Predicate

- 매개값 조사해 true/false 리턴

```
new Thread(new Runnable() {
    @Override
    public void run() {
        System.out.println("스레드 실행");
    }
}).start();

// 위와 같은 코드
new Thread(()->{System.out.println("스레드 실행");}).start();
```

# 18. IO 기반 입출력 및 네트워킹

## 입출력(I/O)

- 입출력 : 입력+출력; 두 대상 간의 데이터를 주고 받는 것
- 스트림(stream) : 입출력하는 데 사용되는 연결 통로
  - 하나의 스트림으로 입출력을 동시에 수행할 수 없음 (단방향 통신)
    - 입출력을 동시에 수행하려면, 2개의 스트림 필요

## 바이트기반 스트림

> 데이터를 바이트 단위로 주고 받음

```
abstract int read()
int read(byte[] b)
int read(byte[] b, int off, int len)

abstract void write(int b)
void write(byte[] b)
void write(byte[] b, int off, int len)
```

- InputStream, OutputStream
- ByteArrayInputStream, ByteArrayOutputStream
- FileInputStream, FileOutputStream

## 바이트기반 보조스트림

- FilterInputStream, FilterOutputStream
- BufferedInputStream, BufferedOutputStream
- DataInputStream, DataOutputStream
  - 기본형 단위로 읽고 쓰는 보조스트림
  - 각 자료형의 크기가 다르므로 출력할 때와 입력할 때 순서에 주의
- SequenceInputStream
  - 여러 입력스트림을 연결해서 하나의 스트림처럼 다룰 수 있게 해줌
  - 여러 파일을 합쳐서 하나의 파일로 만들 때 사용하기 좋음
- PrintStream
  - 데이터를 다양한 형식의 문자로 출력

## 문자기반 스트림

- Reader, Writer
  - Reader : 문자기반 입력스트림의 최고 조상
  - Writer : 문자기반 출력스트림의 최고 조상
- FileReader, FileWriter
- PipedReader, PipedWriter
  - 프로세스(스레드) 간의 통신(데이터를 주고 받음)에 사용
- StringReader, StringWriter
  - CharArrayReader, CharArrayWriter처럼 메모리의 입출력에 사용
  - StringWriter에 출력되는 데이터는 내부의 StringBuffer에 저장됨

## 문자기반 보조스트림

- BufferdReader, BufferdWriter
  - 입출력 효율을 높이기 위해 버퍼(char[])를 사용
  - 라인 단위의 입출력이 편리
- InputStreamReader, OutputStreamWriter
  - 바이트기반 스트림을 문자기반 스트림처럼 쓸 수 있게 함
  - 인코딩(encoding)을 변환하여 입출력할 수 있음

## 표준 입출력과 File

- 표준 입출력
  - 콘솔을 통한 데이터의 입출력
- RandomAccessFile
  - 하나의 스트림으로 파일에 **입력과 출력을 모두 수행**할 수 있는 스트림
  - 다른 스트림과 달리 Object의 자손
- File
  - 파일과 디렉토리를 다루는 데 사용되는 클래스

## 직렬화(serialization)

> 객체를 **연속적인 데이터**로 변환하는 것 객체의 인스턴스 변수들의 값을 일렬로 나열하는 것

- 객체를 저장하기 위해서는 객체를 직렬화해야 함
- 객체 저장 = 객체의 모든 인스터스 변수의 값 저장
- ObjectInputStream, ObjectOutputStream
  - 객체를 직렬화하여 입출력할 수 있게 함