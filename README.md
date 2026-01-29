### 📚 정수
**🏷️ 보통 int를 사용한다**
- byte : -128 ~ 127
- short : -32,768 ~ 32,767
- int : -2,147,483,648 ~ 2,147,483,647
- long : -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807
```java
int a = 2147483648; // X
long a = 2147483648 // O
int a = 2147483648L; // O
```
--- 
### 📚 실수
**🏷️ 보통 double을 사용한다**
- float : ±(1.40129846432481707e-45 ~ 3.40282346638528860e+38)
- double : ±(4.94065645841246544e-324d ~ 1.79769313486231570e+308d)
```java
float a = 2.2; // X
double a = 2.2; // O
float a = 2.2F; // O
```
---
### 📚 문자
**🏷️ 문자는 char**
- char a = '문';
---
### 📚 형 변환
**🏷️ 자동 형 변환**
- 표현범위가 좁은 데이터를 표현범위가 넓은 데이터 타입으로 자동 변환 해준다.
- byte → short / char → int → long → float → double
```java
// float타입의 3.0이 자동으로 double형으로 형 변환
double a = 3.0F;
int x = 10;
int y = 3; 
double z = 3.0
System.out.println(x/y) // 3
System.out.println(x/z) // 3.333..
``` 
**🏷️ 명시적 형 변환**
- (데이터 타입)데이터 값
```java
float a = 100.0 // X, 100.0은 double이기 때문에 float로 변환되지 않음
float a = (float)100.0; // O, 100.0은 double이지만 (float)로 인해 명시적 형 변환처리
```
---
### 📚 연산자
**🏷️ 산술 연산자**
- +, -, *, /, %

**🏷️ 단항 연산자**
- +, -, ++, --

**🏷️ 비교 연산자**
- ==, !=, >, <, >=, .equals()
```java
// .equals 예시
String a = "Hi";
String b = new String("Hi");
System.out.println(a == b); // false
System.out.println(a.equals(b)); // true
```
**🏷️ 논리 연산자**
- &&, ||, !
```java
true && true // true
true && false // false
false && true // false
false && false // false
true || true // true
true || false // true
false || true // false
false || false // false
!true // false
!false // true
```
---
### 📚 조건문
**🏷️ if else문**
```java
int a = 2;
if (a = 1) {
  System.out.println("a = 1");
} else if (a = 2) {
  System.out.println("a = 2");
} else {
  System.out.println("a = 3");
}
```
**🏷️ switch문**
```java
int a = 2
switch (a) {
  case 1:
    System.out.println("a = 1");
    break;
  case 2:
    System.out.println("a = 2");
    break;
  default:
    System.out.println("a = 0");
}
```
---
### 📚 반복문
**🏷️ while문**
- while문은 몇 번 반복할지 미리 알 수 없을때
```java
int a = 1;
while (a <= 5) {
  System.out.println(a++);
}
// 1, 2, 3, 4, 5
```
**🏷️ for문**
- for문은 몇 번 반복할지 미리 알 때
```java
int a;
for ( a = 1; a <= 5; a++ ) {
  System.out.println(a);
}
// 1, 2, 3, 4, 5
```
**🏷️ break 걸기**
- 반복문 내에서 break 거는 방법
```java
int a;
for ( a = 1; a <= 5; a++ ) {
  if( a == 3) break;
  System.out.println(a);
}
// 1, 2
```
**🏷️ continue 걸기**
- 반복문 내에서 특정 조건을 skip하고 다음 조건으로 넘어가는 방법
```java
int a;
for ( a = 1; a <= 5; a++ ) {
  if( a == 3) continue;
  System.out.println(a);
}
// 1, 2, 4, 5  (3은 continue에서 skip)
```
---
### 📚 배열 (★★★)
**🏷️ 배열을 생성하는 2가지 방법**
- String[] people = new String[2];
- String[] animals = {"dog","cat","mouse","bird"};
```java
String[] people = new String[2]; // ["",""]
people[0] = "kim"; people[1] = "lee"; // ["kim","lee"]
people.length; // 2
for (int a = 0; a < people.length ; a++) {
  System.out.println(people[a]);
}
// kim, lee

String[] animals = {"dog","cat","mouse","bird"}; // ["dog","cat","mouse","bird"]
System.out.println(animals[0]); // dog
System.out.println(animals[1]); // cat
System.out.println(animals[2]); // mouse 
System.out.println(animals[3]); // bird
animals.length; // 4

// forEach문
for (String animal : animals) {
  System.out.println(animal);
}
// "dog","cat","mouse","bird" 
```
---
### 📚 메소드 (★★★)
**🏷️ 메소드 = 함수**
- 메소드를 사용하면 코드의 재활용이 용이해지면서 코드량이 줄어들고, 유지보수에도 유리하다.
1. public static void 메소드
```java
public class Hello {
  public static void sayHello(String name) {
    System.out.println(name + "님 안녕하세요." );
  }
}

public class Main {
  public static void main(String[] args) {
    // Hello 메소드는 public static void이다.
    // 1. public이라서 Main class에서 호출이 가능하다.
    // 2. static이라서 `Hello hello = new Hello()` 처럼 객체를 만들 필요가 없음
    // 3. void라서 리턴값이 없다.
    Hello.sayHello("지용");
    // "지용님 안녕하세요."
  }
}
```
2. public static int(String) 메소드
```java
public class Add {
  public static int add(int a, int b) {
    int output = a + b;
    return output;
    // return a+b;
  }
}

public class Main {
  public static void main(String[] args) {
    // Add 메소드는 int 값을 반환하는 public static int이다.
    // 1. public이라서 Main class에서 호출이 가능하다.
    // 2. static이라서 `Add add = new Add()` 처럼 객체를 만들 필요가 없음
    // 3. void가 아닌 int라서 리턴값이 int이다.
    int result = Add.add(3,5);
    System.out.println(result) // 8 
  }
}
```
3. ㄴ
```java
public class People {
  public static void peopleList(String[] people) {
    System.out.println(people.length);
  }
}

public class Main {
  public static void main(String[] args) {
    People.peopleList("kim","lee","park","jeon");
  }
}
```
