---
layout : single
title : C++
categories : Language
tag : C++
toc : true
toc_sticky: true 
author_profile : false
sidebar:
    nav : "counts"
---


```cpp
#include <iostream>  // C++ 입출력 헤더

using namespace std;
// std 네임스페이스 사용
// 사용 이유 : C++ 표준 라이브러리에서 제공하는 모든 클래스와 함수는 std 네임스페이스에 속해 있다. 
// 이를 명시적으로 사용하려면 std::cout, std::endl처럼 std::를 반복적으로 작성해야 한다. 
// 하지만 using namespace std;를 선언하면 std::를 생략할 수 있어 코드가 더 간결하고 
// 가독성이 좋아지게 된다.

int main() {
    cout << "Hello, World!" << endl;
    return 0; // 프로그램이 정상 종료되면 0 반환
}

```

- **헤더**: C++에서 입출력 기능을 쓰기 위해 `<iostream>`을 include.
- **네임스페이스**: `using namespace std;`를 통해 `std::cout`, `std::endl` 대신 `cout`, `endl` 로 사용 가능.
- **main 함수**: C++ 프로그램이 시작되는 함수. `int main()`은 관례적으로 0을 반환하면 정상 종료.

```cpp
#include <iostream>
using namespace std;

int main() {
    int x;
    cout << "정수를 입력하세요: ";
    cin >> x;  // 표준 입력(키보드)에서 정수를 입력받음

    cout << "입력한 정수는 " << x << "입니다." << endl;
    return 0;
}
```

- **출력**: `cout << 표현식`
- **입력**: `cin >> 변수`
- **줄바꿈**:
    - `endl`: 줄바꿈 + 출력 버퍼(flush) 비움
    - `"\n"`: 줄바꿈만

## 2. 기본 자료형 & 변수

### 2.1. 자료형

| 자료형 | 예시 | 범위/특징 |
| --- | --- | --- |
| `int` | `int x = 10;` | 정수(32비트 기준 약 ±21억 범위) |
| `long` | `long x = 10L;` | (플랫폼마다 다름) 좀 더 큰 정수 |
| `float` | `float f = 3.14f;` | 단정도 부동소수점 4byte |
| `double`  | `double d = 3.14;` | 배정도 부동소수점 8byte |
| `bool` | `bool b = true;` | 논리형 (true/false) |
| `char` | `char c = 'A';` | 문자형(1바이트) |
| `wchar_t` | `wchar_t w = L'가';` | 유니코드 문자(플랫폼마다 크기 다름) |
- `auto` 키워드: 형 추론(컴파일러가 자료형을 추론).

```cpp
auto num_1 = 10; // 컴파일러가 int로 추론
auto num_2 = 10.0; // 컴파일러가 float으로 추론
cout << " " << sizeof(num_1) << endl; // 4
cout << " " << sizeof(num_2) << endl; // 8
----------------------------------------------------------------------
# bool 자료형
bool t = true;
bool f = false;

cout << t << endl; // 1
cout << f << endl; // 0
cout << boolalpha << t << endl; // true (blloalpha는 글자 그대로 출력해줌)

# bool 연산 (소괄호 사용해야함)
cout << boolalpha << (true || false) << endl; // true
cout << boolalpha << (true && false) << endl; // false

```

### 2.2. 변수 및 상수

```cpp
int x = 10;   // 변수
const int y = 20; // 상수(값 변경 불가)
extern int a; // 변수 선언 (정의는 아님)
int a; // 변수 선언이자 정의 (메모리 할당)
int a = 10; // 변수 선언, 정의, 초기화
```

- **상수(const)**: 선언 시에만 초기화 가능, 이후 재할당 불가.
- **변수 선언** : 컴파일러에 변수의 **이름**과 **자료형**을 알려주는 작업(정의 없이 선언 당하는 경우는 주로 extern 키워드를 사용할 때 발생)
- **변수 정의** : 메모리를 할당하는 작업

### 2.3. 형 변환

```cpp
int i = 987.65;
cout << "int from double = " << i << endl; 
// int from double = 987 (float, double을 int에 저장하면 반올림 없음)
```

### 2.4. Scope

```cpp
int main()
{
 {
 }
}
// 영역 안에 영역이 또 포함되어 있을 경우 바깥 영역의 int i = 3 일 때
// 안쪽 영역에서 int i = 4라고 선언 시 안쪽 영역에서는 i를 4 바깥영역은 3으로 인식
// 안쪽영역에서 자료형 없이 바깥영역과 동일한 변수명으로 i = 5라고 정의하면 모두 바깥, 안 모두 5로 바뀜
```

- **상수(const)**: 선언 시에만 초기화 가능, 이후 재할당 불가.

### 2.5. 입, 출력

```cpp
    char input[10];
    cin >> input; // cin으로 이전에 선언한 배열에 입력을 받음 // cin은 공백 전까지만 입력받음
    cout << input << endl;
    
    --------------------------------------------------------------------------
    
    # 띄어쓰기 포함 전체를 출력하는 법
    char input[10];
    cin.getline(input, sizeof(input)); //cin.getline()으로 전체 입력을 출력 가능
    cout << input << endl;
    
    --------------------------------------------------------------------------
    
    # 여러개를 입력받는 법
    int num1, num2;

    // 여러 개 입력받기
    cout << "Enter two numbers: \n";
    cin >> num1 >> num2;

    cout << "First number: " << num1 << endl;
    cout << "Second number: " << num2 << endl;
    
     --------------------------------------------------------------------------
     
    # ignore()
    
    #include <iostream>
		using namespace std;

int main() {
    int num;
    cout << "Enter a number: ";
    cin >> num; // 정수를 입력받음

    // 입력 버퍼에서 최대 100개의 문자 또는 개행 문자('\n')까지 무시
    cin.ignore(100, '\n');

    string name;
    cout << "Enter your name: ";
    getline(cin, name); // 남아 있는 버퍼를 무시했으므로 새 입력을 받을 수 있음

    cout << "Number: " << num << endl;
    cout << "Name: " << name << endl;

    return 0;
}

// 입력 : 123abcd\nAlice
// num에는 123만 저장되고 버퍼엔 abcd\n이 남아있음
// cin.ignore(100, '\n')에서 최대 100개의 무시할 수 있으며 \n까지 무시함
// 이후 새로운 cin을 받을 수 있게 함

 --------------------------------------------------------------------------
```

- **상수(const)**: 선언 시에만 초기화 가능, 이후 재할당 불가.

## 3. 연산자

### 3.1. 산술 연산자

| 연산자 | 설명 | 예시 |
| --- | --- | --- |
| `+` | 덧셈 | `a + b` |
| `-` | 뺄셈 | `a - b` |
| `*` | 곱셈 | `a * b` |
| `/` | 나눗셈 | `a / b` |
| `%` | 나머지 | `a % b` |
- 정수 나눗셈은 소수점 이하는 버려집니다(몫만 구함).

### 3.2. 증감 연산자

| 연산자 | 설명 | 예시 |
| --- | --- | --- |
| `++a` | 전위 증가 | `++a;` |
| `a++` | 후위 증가 | `a++;` |
| `--a` | 전위 감소 | `--a;` |
| `a--` | 후위 감소 | `a--;` |

### 3.3. 대입 연산자

```cpp
a = b;    // b를 a에 대입
a += b;   // a = a + b
a -= b;   // a = a - b
a *= b;   // a = a * b
a /= b;   // a = a / b
```

### 3.4. 비교 연산자 & 논리 연산자

| 연산자 | 설명 | 예시 |
| --- | --- | --- |
| `==` | 같음 | `a == b` |
| `!=` | 다름 | `a != b` |
| `>` | 큼 | `a > b` |
| `<` | 작음 | `a < b` |
| `>=` | 크거나 같음 | `a >= b` |
| `<=` | 작거나 같음 | `a <= b` |

| 연산자 | 설명 | 예시 |
| --- | --- | --- |
| `&&` | 논리 AND(둘 다 참이면 참) | `a && b` |
| `||` | 논리 OR(둘 중 하나라도 참이면 참) | `a |
| `!` | 논리 NOT(참 ↔ 거짓) | `!a` |

---

## 4. 조건문 & 반복문

### 4.1. if문

```cpp

if (조건식) {
    // 조건식이 참이면 실행
} else if (다른조건식) {
    // 첫 조건 실패 & 다른조건이 참이면 실행
} else {
    // 모두 거짓이면 실행
}

int main() {
    int num;
    cin >> num;
    if (num % 2 == 0)
        cout << "even";
    else
        cout << "not even";
        
    cout << (num % 2 == 0 ? "짝수" : "홀수") << endl;
    //3항연산자 표
    return 0;
}
```

### 4.2. switch문

```cpp
int num;
    cin >> num;
    switch (num)
        {
    case 0:
	    cout << "0입니다" << endl;
	    break;
    case 1:
	    cout << "1입니다" << endl;
	    break;
    case 2:
	    cout << "2입니다" << endl;
	    break;
	   default:
		   cout << "그 이외의 숫자" << endl;
}
//case에 break을 하지 않으면 해당 case부터 이후 모두 출력된다.
```

- `break`로 분기 구문을 빠져나오지 않으면 아래 case가 연속 실행됩니다.

### 4.3. 반복문

- **for문**:

```cpp

for (int i = 0; i < 5; i++) {
    cout << i << endl;
}

char c = "Hello\0 word";
for (int i = 0; c[i] != '\n'; i++) //개행 전까지 출력
for (int i = 0; c[i] != '\0'; i++) //null 전까지 출력
```

- **while문**:

```cpp
int i = 0;
while (i < 5) {
    cout << i << endl;
    i++;
}
```

- **do-while문**: 최소 1번은 실행

```cpp
int i = 0;
do {
    cout << i << endl;
    i++;
} while (i < 5);
```

---

## 5. 배열과 포인터

### 5.1. 배열

```cpp
int arr[5] = {1, 2, 3, 4, 5};
cout << arr[0] << endl; // 1
```

- 고정된 크기를 갖는 연속된 메모리 공간.
- 선언 시 크기 지정이 필요.

### 5.2. 포인터

```cpp
int x = 10;
int* p = &x;   // x의 주소를 p에 저장
cout << *p << endl; // 포인터 해제(dereference), 10 출력
```

- `&` : 주소 연산자
- : 포인터 변수 선언 시에는 “포인터”를 의미하고, 사용 시에는 해당 주소에 저장된 값을 의미(역참조)

---

## 6. 함수

```cpp
#include <iostream>
using namespace std;

// 함수 선언
int add(int a, int b);

int main() {
    int result = add(3, 4);
    cout << "결과: " << result << endl;
    return 0;
}

// 함수 정의
int add(int a, int b) {
    return a + b;
}
```

- **함수 선언(프로토타입)**: 함수 이름, 매개변수 형, 반환형 미리 명시.
- **함수 정의**: 실제 함수 로직.
- **매개변수 전달 방식**: 값에 의한 호출(call by value), 참조에 의한 호출(call by reference) 등.

---

## 7. 참조(Reference)

```cpp
int a = 5;
int& ref = a;   // a를 참조하는 ref
ref = 10;       // a의 값도 10으로 변경
cout << a << endl;  // 10
```

- 참조(reference)는 대상 변수를 ‘별칭’으로 삼아 동일한 메모리 공간을 가리킵니다.

---

## 8. 구조체(Struct)

| **특징** | **C 구조체** | **C++ 구조체** |
| --- | --- | --- |
| **`struct` 키워드** | 항상 필요 | 생략 가능 |
| **멤버 접근 제어** | 모든 멤버가 `public` | `public`, `private`, `protected` 지원 |
| **멤버 함수** | 지원하지 않음 | 지원 (클래스와 동일) |
| **상속** | 지원하지 않음 | 지원 |
| **생성자/소멸자** | 없음 | 지원 |
| **템플릿** | 지원하지 않음 | 지원 |

### 8.1. 구조체 선언과 사용, 포인터

```cpp
#include <iostream>
#include <string> // std::string 사용을 위한 헤더

using namespace std;

struct Student { // 구조체 선언시 sturct 붙여야 하지만 이후 구조체 변수 선언시 struct 필요 X
    string name;  // 문자열 타입
    int age;      // 정수형 나이
    double score; // 실수형 점수
};

int main() {
    // Student 배열 초기화
    Student class1[2] = { // struct 없이 C의 typedef처럼 바로 선언 가능
        {"Alice", 20, 4.3}, // 학생 1
        {"Bob", 21, 3.8}    // 학생 2
    };
    
    cout << class[0].name << class[0].age << class[0].score << endl;
    //포인터 없이 직접 배열요소 출력시 인덱싱필요

    // 배열 출력
    for (int i = 0; i < 2; i++) {
        cout << class1[i].name << ", " << class1[i].age
             << ", " << class1[i].score << endl;
    }

    return 0;
}

    Student s3 = {"Charlie", 22, 4.0};
		Student* pS3 = &s3; // pS3에 s3구조체 주소 할당
		cout << pS3->name << endl;  // 포인터->멤버
		cout << (*pS3).age << endl; // *pS3는 pS3포인터가 가르키는 s3그 자체 *pS3 == s3

프로그램 출력
Alice, 20, 4.3
Bob, 21, 3.8
Charlie
22
```

- **구조체(Struct)**: 서로 관련된 여러 변수를 하나의 타입으로 묶어서 사용.
- 멤버 변수는 `.`(도트 연산자)로 접근.
- 포인터가 가리키는 구조체 멤버에 접근할 땐 `>`(화살표 연산자) 사용.
- `(*pS3).name` 과 `pS3->name` 은 같은 의미.

### 8.2. 구조체 배열

```cpp
Student class1[2] = {  // [2]는 두개의 Student구조체를 저장할수 있다는 의미임
    {"Alice", 20, 4.3},
    {"Bob", 21, 3.8}
};

for (int i = 0; i < 2; i++) {
    cout << class1[i].name << ", " << class1[i].age
         << ", " << class1[i].score << endl;
}
```

- 배열 요소 각각이 구조체 변수.

### 8.3. 생성자 소멸자

```cpp
struct Point {
    int x, y;

    // 생성자
    Point(int a, int b) {
        x = a;
        y = b;
    }

    // 멤버 함수
    void display() {
        cout << "Point: (" << x << ", " << y << ")" << endl;
    }

    // 소멸자
    ~Point() {
        cout << "Point destroyed" << endl;
    }
};

int main() {
    Point p1(10, 20); // 생성자 호출
    p1.display();     // 멤버 함수 호출
    return 0;
}

```

- C++ 구조체는 생성자와 소멸자를 가질 수 있다.
- 이를 통해 구조체 객체 초기화와 정리 작업을 자동화할 수 있다.

### 8.4. 접근 제어 (`public`, `private`, `protected`)

```cpp
struct Point {
private:
    int x, y; // private 멤버

public:
    void setPoint(int a, int b) { // public 멤버 함수
        x = a;
        y = b;
    }

    void display() {
        cout << "Point: (" << x << ", " << y << ")" << endl;
    }
};

int main() {
    Point p1;
    p1.setPoint(10, 20); // public 함수로 설정
    p1.display();        // public 함수로 출력
    return 0;
}

```

- C++ 구조체 멤버는 기본적으로 **`public`**이며, 접근 제어자를 명시적으로 추가할 수 있다.

## 9. 클래스(Class)

- **클래스(Class)**는 객체지향 프로그래밍(OOP)의 핵심 요소로, 데이터와 메서드를 하나의 단위로 캡슐화함.

### 9.1. 기본 구조

- 클래스는 **`class` 키워드**로 정의하며, 데이터 멤버와 멤버 함수를 포함합니다.
- 기본 접근 제어는 **`private`*입니다.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Person {
private:
    string name; // 이름
    int age;     // 나이

public:
    // 이름 설정
    void setName(string n) {
        name = n;
    }
    // 나이 설정
    void setAge(int a) {
        age = a;
    }
    // 정보 출력
    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Person p1, p2; // Person 객체 생성
    p1.name("Alice") // 이와같이 private멤버의 데이터를 Class외부에서 직접 접근 불가

    // 첫 번째 객체
    p1.setName("Alice");
    p1.setAge(25);
    p1.display(); // 출력: Name: Alice, Age: 25

    // 두 번째 객체
    p2.setName("Bob");
    p2.setAge(30);
    p2.display(); // 출력: Name: Bob, Age: 30

    return 0;
}

```

### 9.2. 객체생성

- 클래스 객체를 선언하여 멤버에 접근
- 멤버 변수는 **`.`** 연산자로, 멤버 함수는 **객체를 통해 호출**

### 예제:

```cpp
int main() {
    Person p1; // 객체 생성
    p1.setName("Alice");
    p1.setAge(25);
    p1.display(); // 출력: Name: Alice, Age: 25
    return 0;
}
```

---

### **9.3. 접근 제어자**

| **제어자** | **설명** |
| --- | --- |
| **`private`** | 클래스 내부에서만 접근 가능 (기본값). |
| **`protected`** | 클래스 내부 및 파생 클래스에서만 접근 가능. |
| **`public`** | 클래스 외부에서도 접근 가능. |

### 예제: protect, 파생 Class

```cpp
#include <iostream>
using namespace std;

class Base {
protected: // protected 멤버
    int protectedVar;

public:
    void setProtectedVar(int val) {
        protectedVar = val;
    }
};

class Derived : public Base { // class 파생클래스이름 : 접근제어자 부모클래스이름으로 선언
public:
    void show() {
        cout << "Protected Var: " << protectedVar << endl; // 파생 클래스에서 접근 가능
    }
};

int main() {
    Base base;
    Derived derived;

    // base.protectedVar = 10; // 오류: protected 멤버에 직접 접근 불가
    derived.setProtectedVar(10); // public 함수를 통해 값 설정
    derived.show(); // 출력: Protected Var: 10

    return 0;
}

```

---

### **9.4. 생성자와 소멸자**

### **생성자 (Constructor)**

- 클래스 이름과 동일한 함수로, 객체 생성 시 자동 호출.
- 반환값 없음.
- 오버로딩 가능.

### 기본 생성자:

```cpp
class Person {
public:
    Person() { // 기본 생성자
        cout << "Object created!" << endl;
    }
};
```

### 매개변수 생성자:

```cpp
class Person {
private:
    string name;

public:
    Person(string n) { // 매개변수 생성자(매개변수가 있는 생성자)
        name = n;
    }
    void display() {
        cout << "Name: " << name << endl;
    }
};

```

### 초기화 리스트:

```cpp
class Person {
private:
    string name;
    int age;

public:
    Person(string n, int a) : name(n), age(a) {} // 초기화 리스트
};

```

### **소멸자 (Destructor)**

- 객체가 소멸될 때 호출되는 함수.
- 클래스 이름 앞에 **`~`*를 붙여 정의.
- 반환값 없음, 매개변수 없음.

### 예제:

```cpp
class Person {
public:
    ~Person() { // 소멸자
        cout << "Object destroyed!" << endl;
    }
};
```

---

### **9.5. 멤버 함수**

### **정의 방법**

### 클래스 내부 정의:

```cpp
class Person {
public:
    void greet() {
        cout << "Hello!" << endl;
    }
}
```

### 클래스 외부 정의:

```cpp
class Person {
public:
    void greet(); // 함수 선언
};

void Person::greet() { // 클래스 외부에서 정의
    cout << "Hello!" << endl;

```

---

### **9.6. 정적 멤버 (Static Members)**

### **정적 멤버 변수**

- 모든 객체가 공유하는 변수.
- 클래스 외부에서 반드시 초기화.

### 예제:

```cpp
class Person {
public:
    static int count; // 정적 멤버 변수 선언
};

int Person::count = 0; // 정적 멤버 변수 정의 및 초기화
```

### **정적 멤버 함수**

- 객체 없이 클래스 이름으로 호출 가능.

### 예제:

```cpp
class Person {
public:
    static void showCount() {
        cout << "Count: " << count << endl;
```

---

### **9.7. 상속**

### **기본 문법**

```cpp
class Base {
protected:
    int baseVar;
};

class Derived : public Base { // public 상속
public:
    void setBaseVar(int v) {
        baseVar = v;
    }
};
```

| **상속 방식** | **Base 멤버의 접근 수준** |
| --- | --- |
| **`public`** | public → public, protected → protected |
| **`protected`** | public → protected, protected → protected |
| **`private`** | public, protected → private |

---

### **9.8. 다형성**

### **가상 함수**

- 부모 클래스에서 정의된 함수를 자식 클래스에서 재정의 가능.
- **`virtual`** 키워드 사용.

### 예제:

```cpp
class Base {
public:
    virtual void show() {
        cout << "Base class" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {
        cout << "Derived class" << endl;
    }
};
```

### **순수 가상 함수**

- 인터페이스를 정의할 때 사용.
- *`= 0`*으로 정의.

### 예제:

```cpp
class Shape {
public:
    virtual void draw() = 0; // 순수 가상 함수
};
```

---

### **9.9. 연산자 오버로딩**

### **기본 문법**

- `operator` 키워드 사용.

### 예제:

```cpp

class Point {
private:
    int x, y;

public:
    Point(int a, int b) : x(a), y(b) {}

    Point operator+(const Point& p) { // + 연산자 오버로딩
        return Point(x + p.x, y + p.y);
    }
};
```

---

### **9.10. 템플릿 클래스**

### **기본 문법**

```cpp
template <typename T>
class Box {
private:
    T data;

public:
    Box(T d) : data(d) {}
    void show() {
        cout << "Data: " << data << endl;
    }
};
```

---

### **9.11. 캡슐화, 상속, 다형성 (3대 특성)**

| **특성** | **설명** |
| --- | --- |
| **캡슐화** | 데이터와 메서드를 하나의 단위로 묶고, 외부에 대한 접근을 제한. |
| **상속** | 기존 클래스(부모)를 기반으로 새로운 클래스(자식)를 생성. |
| **다형성** | 같은 인터페이스로 다른 동작을 구현(함수 오버라이딩, 가상 함수 등). |

---

## **요약**

| **기능** | **설명** |
| --- | --- |
| **클래스 정의** | `class` 키워드를 사용해 데이터와 메서드를 포함하는 사용자 정의 자료형. |
| **멤버 접근 제어** | `public`, `private`, `protected` 키워드를 통해 멤버 접근 수준을 제어. |
| **생성자/소멸자** | 객체 생성 및 소멸 시 자동 호출되는 함수. |
| **정적 멤버** | 객체와 독립적으로 클래스 자체에 속하는 멤버 변수 및 함수. |
| **상속** | 기존 클래스를 기반으로 새로운 클래스 생성. |
| **다형성** | 함수 오버로딩, 가상 함수 등을 통해 같은 이름으로 다른 동작 구현. |
| **템플릿** | 다양한 자료형에 대해 일반화된 코드를 작성. |
| **연산자 오버로딩** | 클래스 객체에 대해 기본 연산자를 재정의. |

```cpp
// Class 예제

#include <iostream>
#include <cstring>

using namespace std;

// public, private 접근 권한 안내

class MyString
{
public:
    MyString()
    {
        // 호출 시점 확인
        cout << "MyString()" << endl;

        size_ = 1;
        str_ = new char[size_];
    }

    MyString(const char *init_str) // init_str이 유효한 메모리라고 가정
    {
        cout << "MyString(const char *init_str)" << endl;

        // 1. 글자 수 먼저 확인
        size_ = 0;
        while (init_str[size_] != '\0')
        {
            size_++; // null전까지 글자 갯수를 센다
        }

        // 2. 글자 수가 0이 아니면 메모리 할당
        if (size_ > 0)
        {
            str_ = new char[size_];
        }

        // 3. 복사
        for (int i = 0; i < size_; i++)
        {
            str_[i] = init_str[i];
        }
        // memcpy() 사용 가능
    }

    ~MyString()
    {
        // 호출 시점 확인
        cout << "Destructor" << endl;

        size_ = 0;
        if (str_)
            delete[] str_;
    }

    void Resize(int new_size)
    {
        char *new_str = new char[new_size];

        // memcpy() 사용 가능
        for (int i = 0; i < (new_size < size_ ? new_size : size_); i++)
        {
            new_str[i] = str_[i];
        }

        delete[] str_;
        str_ = new_str;
        size_ = new_size;

        // new_str 지우면 안되요!
    }

    void Print()
    {
        for (int i = 0; i < size_; i++)
        {
            cout << str_[i];
        }
        cout << endl;
    }

    void Append(MyString *app_str) // 같은 타입을 매개변수로 사용 가능
    {
        int old_size = size_;

        // 다른 멤버 함수 호출 가능
        Resize(size_ + app_str->size_);

        // 중요한 개념
        for (int i = old_size; i < size_; i++)
        {
            str_[i] = app_str->str_[i - old_size];
        }
    }

private:
    int size_ = 0;        // m_size
    char *str_ = nullptr; // m_str 구글 스타일 변수 = 변수 뒤에 _ 붙이면 멤버변수
};

int main()
{
    // 클래스 기본 문법 안내

    MyString str1("ABCDE");
    // 설명 -> str1은 MyString이라는 Class의 레시피를 가지고 이미 만들어진 요리(객체)이다.
    // 이 코드를 실행하면 객체 str1이 생성 -> 매개변수 있는 MyString 생성자 호출.
    // 문자열 "ABCDE"의 길이(5)를 계산하여 size_에 저장.
    // 동적으로 size_ 크기의 메모리를 할당하고, 문자열을 str_에 복사.
    MyString str2("123");

    str1.Append(&str2);
    // str1이라는 객체에 대해 Append 함수를 적용함

    str1.Print();

    return 0;
}
```

## 10. 동적 할당

### 10.1. 정적(Stack) 동적(Heap)

```cpp
#include <iostream>
#include <cstring> // memcpy를 사용하기 위해 필요
using namespace std;

const int kMaxStr = 50; // 문자열 크기를 정의

int main() {
    // 문자열 복사
    char str1[] = "Hello, World!"; // 원본 문자열
    char str2[kMaxStr];           // 복사할 문자열 배열

    str2 = str1; // 배열 간 복사는 이렇게 직접 할 수 없음 (오류 발생)

    // dest, src, 크기 정보를 정확히 지정해야 함
    memcpy(str2, str1, min(sizeof(str1), sizeof(str2))); 
    // str1을 str2로 복사하는데 min()을 사용하여 str1, 2중 더 작은 메모리크기만큼만 복사하라는 의미임, str1이 "apple"인데 str2가 3글자만 받을 수 있다면 "app"만 복사되어 저장됨
    cout << str2 << endl; // 복사된 문자열 출력: Hello, World!

    // 동적 할당 메모리 사용
    char *dynamic_array = new char[kMaxStr]; // new(메모리크기)를 사용하여 동적 배열 생성

    // 주의: 동적 할당된 메모리 크기를 제대로 관리해야 함
    memcpy(dynamic_array, str1, kMaxStr); // str1의 내용을 동적 배열로 복사
    cout << dynamic_array << endl; // 동적 배열에 저장된 문자열 출력: Hello, World!

    // 디버깅용 정보 출력: 포인터와 배열의 크기 비교
    cout << str1 << " " << str2 << " " << dynamic_array << endl;
    cout << sizeof(str1) << " " << sizeof(str2) << " " << sizeof(dynamic_array) << endl;

    // 동적 할당 메모리 해제
    delete[] dynamic_array;

    return 0;
}

```

- 주의사항
    - new(크기)로 할당한 메모리는 반드시 delete[] 배열명; 으로 해제야한다.