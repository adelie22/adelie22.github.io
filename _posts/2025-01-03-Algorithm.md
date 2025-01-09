---
layout : single
title : Algorithm
categories : Algorithm
tag : Algorithm
toc : true
toc_sticky: true 
author_profile : false
sidebar:
    nav : "counts"
---

- 작성언어
    1. 파이썬
        1. 동적언어로 코딩이 빠르지만 디버깅 까다롭고 타입 제약이 없어 코드가 복잡해지면 이해 어려움
    2. 자바
        1. 문자열 조작 등 일부 문법이 모호하고 일부 패키지 유형도 마찬가지
    3. C++
        1. 대부분 작업에 편리, 일부 문법은 혼란을 줄 수 있다.

위의 언어를 상황에 맞게 사용하여 공부한다.

- 알고리즘 작성에 사용할 데이터 구조
    - array
    - list C
    - map
    - stack
    - queue

---

## 0.1 C++

- c++은 함수의 매개변수는 기본적으로 **“값”**을 전달.
- reference형식을 전달할 때 &를 사용해야 데이터가 복사되지 않고 **원래 데이터 직접 조작** 가능.
- 배열은 함수 매개변수로 Pointer을 넘겨주므로 별도 &필요없음

### 0.1.1 동적 배열 유형 Vector

- 표준 라이브러리로 캡슐화된 배열, 자동 확장 축소 가능
- malloc과 같은 함수보다 캡슐화된 배열을 사용해서 알고리즘 사고 자체에 집중하기

```cpp
//초기화 방법

int n = 7, m = 8;
vector<int> nums; 
// int 타입 빈 배열 nums 초기화

vector<int> nums(n); 
// 크기 n인 nums배열 요소의 기본값을 0으로 초기화

vector<int> nums{1, 3, 5}; 
// nums 배열 요소를 1, 3, 5로 초기화

vector<int> nums(n, 2); 
// 크기가 n인 nums 배열 요소의 기본값을 2로 초기화

vector<vector<int>> dp; 
// 2차원 int배열 dp 초기화

vector<vector<bool>> dp(m, vector<bool>(n, true)); 
//크기 m행,n열인 Bool배열 dp 값 모두 true초기화 

//사용하는 method

bool empty();
//배열 null 여부 반환

size_type size();
//배열 요소 수 반환

reference back()
//배열 마지막 요소 참조 반환

void push_back(const vlaue_type& val);
//배열 끝에 val 요소 삽입

void pop_back();
//배열 끝 요소 제거
```

- 샘플 코드

```cpp
int n = 10;
vector<int> nums(n);
//배열 크기 10, 기본 값 0 초기화

cout << nums.empty(); // 배열에 요소가 존재하므로 false
cout << nums.size(); // 배열 크기인 10 출력

int a = nums[4]; // int a에 nums 배열 5번째 값을 할당
nums[0] = 11; // 배열 요소 값 초기화

nums.push_back(20); // 배열 끝에 정수 20 삽입
cout << nums.size() // 배열 크기 1개 늘었으므로 11 출력

int b = nums.back(); // 배열 마지막 요소의 참조 가져오기
cout << b; // 20 출력

nums.pop_back(); // 마지막 요소 값 삭제(값 return 하지 않음)
cout << nums.size(); // 10

swap(nums[0], nums[1]); //배열 요소 값 교환
```

- 배열의 중간이나 앞부분 요소를 삭제하면 삭제된 부분을 채우기 위해 데이터를 앞으로 옮기는 작업이 필요하여 효율이 떨어지므로 이를 피해야 한다.

### 0.1.2 문자열 string

```cpp
string s; //빈 문자열 s 생성
string s = "abc"; // abc로 초기화
size_t size(); // 문자열 길이 반환
bool empty(); // 문자열 null여부 판단
void push_back(char c); // 문자열 가장 뒤에 'c' 삽입
void pop_back(); // 문자열 끝 문자 제거
string substr (size_t pos, size_t len); // pos에서 시작, 길이자 len인 문자열 반환
```

- 샘플코드

```cpp
string s;
s = "abcd";
cout << s[2];
s.push_back('e');
cout << s;
cout << s.substr(2,3); // c 부터 길이 3개 출력 = "cde"출력
s += "xyz"; // 출력 abcdexyz // string과 문자열 단순 연산 가능
cout << s;
```

### 0.1.3 해시 테이블 unordered_map

- 해시 테이블 data는 어떤 type도 상관없지만 해시 테이블의 key는 int, string을 주로 사용하도록 한다.

```cpp
unordered_map<int, int> mapping; 
// key, value가 int인 해시 테이블 초기화
unordered_map<string, vector<int>> mapping;
// key는 string, value는 int배열인 해시 테이블 초기화

-------------------------------------------------
// 시각적 표현
unordered_map<int, int> mapping;
mapping[1] = 100;
mapping[2] = 200;
mapping[3] = 300;

Key   | Value
------+-------
  1   |  100
  2   |  200
  3   |  300

unordered_map<string, vector<int>> mapping;
mapping["A"] = {1, 2, 3};
mapping["B"] = {4, 5, 6};
mapping["C"] = {7, 8, 9};

Key   | Value (vector<int>)
------+---------------------
 "A"  | [1, 2, 3]
 "B"  | [4, 5, 6]
 "C"  | [7, 8, 9]
 
 -------------------------------------------------
 
//method

size_type size(); // hash table key-value set 갯수 반환
bool empty(); // null여부 판단
size_type count (const key_type& key);
//hash table key 나타나는 횟수 반환
//hash table은 중복 key 값이 발생하지 않으므로 함수는 1또는 0 반환
//hash table에 키 값 존재여부 확인

size_type erase (const key_type& key);
//key를 통해 hash table key-value set 제거
```

- 샘플 코드

```cpp
vector<int> nums{1, 1, 3, 4, 5, 3, 6};
unordered_map<int, int> counter;
for (int num : nums) { // int num 정의 후 counter[num]이라고 작성함으로써
counter[num]++; // counter 해시테이블의 key = num이 된다.
}

for(auto& it : counter) {
// auto& 변수명 : 컨테이너로 해당 컨테이너의 키값쌍에 접근 // 자동으로 자료형을 인식해줌
int key = it.first; // 변수명.first = key
int val = it.second; // 변수명.second = value
cout << key << ": " << val << endl;
}

Key   | Value
------+-------
  1   |  2
  2   |  3
  5   |  7
  // vecter nums 배열을 순회하면서 해당 숫자가 몇번 나왔는지 해시테이블로 저장하는 프로그램
  
   -------------------------------------------------
// 대괄호[]를 사용해 key에 직접 접근하는 경우 key값이 없으면 자동으로 생성하고 해당 값이 타입의 기본값을 결정
// 예시

unordered_map<int, int> counter;
//현재 빈 해시테이블
counter[5];
//[]를 이용하여 5라는 key값에 접근
Key   | Value
------+-------
  5   |   0
//5라는 key를 생성하고 자동으로 value = 0으로 초기화 
//자료형에 따라 int = 0, string = ""으로 초기화

// 아래의 위의 과정을 직접 구현하는 코드
for (int num : nums) {
if(!counter.count(num)) { 
// !counter.해시테이블(key) -> 해시테이블에 num이라는 키가 없으면 true
counter[num] = 0; // 없다면 0으로 초기화
}
coutner[num]++; // 있다면 ++ 
}
```

### 0.1.4 해시 세트 unordered_set

- `unordered_set`은 **유일한 키(key)를 저장**하며, 키의 순서는 해시 함수에 의해 결정. 이는 **중복되지 않는 데이터를 빠르게 저장하고 검색**할 때 사용

```cpp
unordered_set<int> visited;
//int를 저장하는 해시 세트 초기화
unordered_set<string> visited;
//stringd을 저장하는 해시세트 초기화

-------------------------------------------------

//method

size_type size(); // 해시테이블 key-value 세트 수 반환
bool empty(); // 해시테이블 Null 여부
size_type count (const key_type& key); // 해시 테이블과 유사하게 키 존재여부로 1, 0 반환
pair<iterator,bool> insert (const key_tpye& key); // pair에 key 삽입

// 해시 세트 키 제거
// 제거 성공 시 1, 존재하지 않으면 0 반환
size_type eraser (const key_type& key);
```

### 0.1.5 큐 queue

```cpp
queue<int> q; // int 저장할 queue 초기화
queue<string> q; // string 저장할 queue 초기화

-------------------------------------------------
//method
bool empty()
size_type size();
void push (const value_type& val); // queue 끝에 요소 추가
value)type& front(); // queue 첫 번째 요소 반환
void pop(); // queue 첫 번째 요소 제거
// queue 구조는 단순하므로 주의 필요 C++에서 queue의 pop()은 보통 void type이며, 
// 삭제된 요소 반환하지 않는다
// 아래와 같이 사용
int e = q.front;  
q.pop() 

```

### 0.1.6 스택 stack

```cpp
stack<int> stk;
stack<string> stk;

-------------------------------------------------
//method
bool empty();
size_type size();
void push (const value_type& val);
value_type& top(); // 스택 가장 위의 요소 참조 반환
void pop(); // 가장 위 요소 제거
```

## 0.2 JAVA

### 0.2.1 배열 Array

```cpp
데이터타입[] 배열이름;   // 권장 방식
배열이름 = new 데이터타입[크기];  // 크기를 지정하여 배열 생성
numbers = new int[5];     // 크기가 5인 int형 배열 생성
names = new String[3];    // 크기가 3인 String형 배열 생성

int m = 5, n = 10;
int[] nums = new int[n] //선언과 생성 동시에
int[] numbers = new int[5];     // 크기가 5인 int형 배열 생성
boolean[][] visited = new boolean[m][n]; // m by n bool 배열 선언과 데이터 크기 동시 생성

// 일부 문제는 함수를 파라미터 형식으로 전달하며, 보통 함수 시작부분에 null 검사를 하고 인덱스를 사용해 요소에 접근

if(nums.length == 0)
return;
for(int i = 0; i < nums.length; i++) {
// nums[i] 엑세스
}
```

### 0.2.2 문자열 string

- 자바에서 string은 []를 사용해 직접 문자에 엑세스할 수 없으므로 문자열 처리가 불편함. 또한 직접 수정이 불가하여 char[] 유형으로 변환 후 수정 가능하다

```cpp
String s1 = "hello world";
// s1[2] 문자 가져오기
char c = s1.charAt(2); 

char[] chars = s1.toCharArray()
// toCharArray()는 문자열을 문자 배열로 변환하여 반환하여 s1 배열에 저장
chars[1] = 'a';
String s2 = new String(chars); // string에 char배열의 내용을 복사하여 새로운 문자열 객체생성
// print : hallo world
System.out.println(s2); //출력 명령문

//문자열 동일 여부 판단은 반드시 equals() 사용
if(s1.equals(s2)) {
 // s1, s2 같으면 true로 해당 블록 실행
 } else { // 다르면 false로 해당블록 실행 }
 
 //문자열은 + 기호로 연산 가능
 String s3 = s1 + "!";
 System.out.println(s3); // hello world!
 
 //문자열 병합에 + 사용 가능하지만 비효율적이며 for 루프에서는 사용하지 않는 걸 권장. 
 //문자열 병합을 자주 하게 된다면 StringBuilder사용을 권장
 
 StringBuilder sb = new StringBuilder()
 
 for (char c = 'a'; c <= 'f'; c++) {
 sb.append(c);
 }
 
 //append 메서드는 문자, 문자열, 숫자 등 유형 지원
 sb.append('g').append("hij").append(123);
 
 String res = sb.toString();
 System.out.println(res)
 System.out.println(sb.toString()); // 따로 변수 저장안하고 바로 출력하려면
 // 자바는 항상 출력할 때 String으로 출력해야함
```

  **- 참고 -**

- `StringBuilder`는 **문자열을 효율적으로 수정하거나 추가**할 수 있도록 설계된 자바 클래스
- **패키지 위치:** `java.lang.StringBuilder`
- **주요 특징:**
    - 문자열을 **mutable(수정 가능)**하게 다룰 수 있습니다.
    - 새로운 문자열 객체를 생성하지 않고 기존 문자열을 수정하여 성능이 좋습니다.
    - 주로 문자열을 **반복적으로 추가, 삭제, 수정**해야 할 때 사용합니다.

### 0.2.3 동적 배열 ArrayList

- C++의 vector와 유사하게 ArrayList는 자바에 내장된 배열 타입을 캡슐화한 것과 같으며, 초기화방법은 다음과 같다.

```cpp
// String 타입의 데이터를 저장하는 동적 배열 초기화
ArrayList<String> nums = new ArrayList<>();

// int 타입의 데이터를 저장하는 동적 배열 초기화
ArrayList<Inteher> strings = new ArrayList<>()

-----------------------------------------------
//method

// 배열 null 여부 판단
boolean isEmpty()
// 배열 요소 개수 반환
int size()
// index 요소 반환
E get(int index)
// 배열 끝에 요소 e 추가
boolean add(E e)
```

- 샘플코드

```cpp
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        // String 타입의 데이터를 저장하는 동적 배열 초기화
        ArrayList<String> nums = new ArrayList<>();

        // int 타입의 데이터를 저장하는 동적 배열 초기화
        ArrayList<Integer> strings = new ArrayList<>();

        // 1. isEmpty() - 배열이 비어 있는지 확인
        System.out.println("nums is empty: " + nums.isEmpty()); // true
        System.out.println("strings is empty: " + strings.isEmpty()); // true

        // 2. add(E e) - 배열 끝에 요소 추가
        nums.add("Hello");
        nums.add("World");
        strings.add(10);
        strings.add(20);

        System.out.println("\nAfter adding elements:");
        System.out.println("nums: " + nums); // [Hello, World]
        System.out.println("strings: " + strings); // [10, 20]

        // 3. size() - 배열 요소 개수 반환
        System.out.println("\nnums size: " + nums.size()); // 2
        System.out.println("strings size: " + strings.size()); // 2

        // 4. get(int index) - 특정 인덱스의 요소 반환
        System.out.println("\nnums[0]: " + nums.get(0)); // Hello
        System.out.println("strings[1]: " + strings.get(1)); // 20
    }
}

nums is empty: true
strings is empty: true

After adding elements:
nums: [Hello, World]
strings: [10, 20]

nums size: 2
strings size: 2

nums[0]: Hello
strings[1]: 20

```

### 0.2.4 이중 연결 리스트 LinkedList