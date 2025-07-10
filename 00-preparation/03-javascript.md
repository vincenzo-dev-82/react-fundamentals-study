# 0.3 자바스크립트

## 자바스크립트란?

자바스크립트(JavaScript)는 웹 브라우저에서 동작하는 프로그래밍 언어로, 웹 페이지를 동적이고 상호작용적으로 만들어줍니다. React를 사용하기 위해서는 자바스크립트에 대한 기본적인 이해가 필요합니다.

## 변수와 상수

### let과 const

```javascript
// 변수 선언 (값 변경 가능)
let age = 25;
age = 26;  // OK

// 상수 선언 (값 변경 불가)
const name = "홍길동";
// name = "김철수";  // Error!

// 객체와 배열의 경우
const person = { name: "홍길동" };
person.name = "김철수";  // OK (내용 변경 가능)
// person = { name: "이영희" };  // Error! (재할당 불가)
```

### var (사용 지양)

```javascript
// var는 함수 스코프를 가지며, 호이스팅 문제가 있음
var oldWay = "옛날 방식";
```

## 데이터 타입

### 기본 타입

```javascript
// 숫자 (Number)
const age = 25;
const price = 19.99;

// 문자열 (String)
const name = "홍길동";
const message = '안녕하세요';
const template = `나이는 ${age}살입니다`;  // 템플릿 리터럴

// 불린 (Boolean)
const isActive = true;
const isComplete = false;

// undefined와 null
let notDefined;  // undefined
const empty = null;

// 심볼 (Symbol)
const sym = Symbol('id');
```

### 참조 타입

```javascript
// 객체 (Object)
const person = {
    name: "홍길동",
    age: 25,
    greet: function() {
        console.log("안녕하세요!");
    }
};

// 배열 (Array)
const numbers = [1, 2, 3, 4, 5];
const mixed = [1, "문자열", true, { id: 1 }];

// 함수 (Function)
function add(a, b) {
    return a + b;
}
```

## 함수

### 함수 선언식

```javascript
function greet(name) {
    return `안녕하세요, ${name}님!`;
}
```

### 함수 표현식

```javascript
const greet = function(name) {
    return `안녕하세요, ${name}님!`;
};
```

### 화살표 함수

```javascript
// 기본 형태
const add = (a, b) => {
    return a + b;
};

// 간단한 형태
const multiply = (a, b) => a * b;

// 매개변수가 하나일 때
const double = x => x * 2;

// 매개변수가 없을 때
const sayHello = () => console.log("Hello!");
```

## 조건문

### if...else

```javascript
const age = 18;

if (age >= 18) {
    console.log("성인입니다");
} else if (age >= 13) {
    console.log("청소년입니다");
} else {
    console.log("어린이입니다");
}
```

### 삼항 연산자

```javascript
const status = age >= 18 ? "성인" : "미성년자";
```

### switch

```javascript
const day = "월요일";

switch(day) {
    case "월요일":
        console.log("월요일입니다");
        break;
    case "금요일":
        console.log("불금!");
        break;
    default:
        console.log("평일입니다");
}
```

## 반복문

### for 루프

```javascript
// 기본 for 루프
for (let i = 0; i < 5; i++) {
    console.log(i);
}

// for...of (배열)
const fruits = ["사과", "바나나", "오렌지"];
for (const fruit of fruits) {
    console.log(fruit);
}

// for...in (객체)
const person = { name: "홍길동", age: 25 };
for (const key in person) {
    console.log(`${key}: ${person[key]}`);
}
```

### while 루프

```javascript
let count = 0;
while (count < 5) {
    console.log(count);
    count++;
}
```

## 배열 메서드

```javascript
const numbers = [1, 2, 3, 4, 5];

// map: 각 요소를 변환
const doubled = numbers.map(n => n * 2);
// [2, 4, 6, 8, 10]

// filter: 조건에 맞는 요소만 선택
const evens = numbers.filter(n => n % 2 === 0);
// [2, 4]

// reduce: 하나의 값으로 축약
const sum = numbers.reduce((acc, n) => acc + n, 0);
// 15

// find: 조건에 맞는 첫 번째 요소
const found = numbers.find(n => n > 3);
// 4

// some/every: 조건 검사
const hasEven = numbers.some(n => n % 2 === 0);  // true
const allPositive = numbers.every(n => n > 0);   // true
```

## 객체 다루기

### 객체 생성과 접근

```javascript
// 객체 리터럴
const person = {
    name: "홍길동",
    age: 25,
    greet() {
        console.log(`안녕하세요, ${this.name}입니다`);
    }
};

// 속성 접근
console.log(person.name);      // 점 표기법
console.log(person["age"]);    // 대괄호 표기법

// 속성 추가/수정
person.email = "hong@example.com";
person.age = 26;
```

### 구조 분해 할당

```javascript
// 객체 구조 분해
const { name, age } = person;
console.log(name);  // "홍길동"

// 배열 구조 분해
const [first, second, ...rest] = [1, 2, 3, 4, 5];
console.log(first);  // 1
console.log(rest);   // [3, 4, 5]
```

### 스프레드 연산자

```javascript
// 배열 스프레드
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];  // [1, 2, 3, 4, 5]

// 객체 스프레드
const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, c: 3 };  // { a: 1, b: 2, c: 3 }
```

## 클래스

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        console.log(`안녕하세요, ${this.name}입니다`);
    }
    
    get birthYear() {
        return new Date().getFullYear() - this.age;
    }
}

const person = new Person("홍길동", 25);
person.greet();
```

## 비동기 프로그래밍

### Promise

```javascript
const fetchData = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("데이터 가져오기 완료");
        }, 1000);
    });
};

fetchData()
    .then(data => console.log(data))
    .catch(error => console.error(error));
```

### async/await

```javascript
const getData = async () => {
    try {
        const response = await fetch('/api/data');
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('에러 발생:', error);
    }
};
```

## 모듈

### 내보내기 (export)

```javascript
// named export
export const PI = 3.14159;
export function add(a, b) {
    return a + b;
}

// default export
export default class Calculator {
    // ...
}
```

### 가져오기 (import)

```javascript
// named import
import { PI, add } from './math.js';

// default import
import Calculator from './Calculator.js';

// 모두 가져오기
import * as math from './math.js';
```

## React에서 자주 사용하는 자바스크립트 패턴

```javascript
// 조건부 렌더링
const element = isLoggedIn ? <UserGreeting /> : <GuestGreeting />;

// 배열 렌더링
const items = data.map(item => (
    <li key={item.id}>{item.name}</li>
));

// 이벤트 핸들러
const handleClick = (e) => {
    e.preventDefault();
    console.log('클릭됨');
};

// 상태 업데이트
setState(prevState => ({
    ...prevState,
    count: prevState.count + 1
}));
```

## 요약

- 자바스크립트는 웹 개발의 핵심 언어
- 변수, 함수, 조건문, 반복문 등 기본 문법 숙지 필요
- ES6+ 문법(화살표 함수, 구조 분해, 스프레드 등) 이해 중요
- 비동기 프로그래밍과 모듈 시스템 이해 필요
- React 개발을 위해 자바스크립트 기초는 필수

다음 장에서는 React 개발을 위한 개발 환경 설정에 대해 알아보겠습니다.