# 코드스테이츠 - 1 day

## ✉️ 학습목표

> ### Chapter1. 변수
> - 변수 사용은 데이터를 편리하게 저장하고 꺼내 쓰는 것임을 이해한다.
> - JavaScript에서 변수의 선언과 값의 할당에 대해서 설명할 수 있다.
> - =가 "같다"라는 의미가 아니라 할당 연산자임을 이해할 수 있다.
> - 크롬 개발자 도구의 console 탭을 이용하여 원하는 값을 출력할 수 있다.
> - 변수를 사용하여 보다 효과적으로 구구단을 출력할 수 있다.

> ### Chapter2. 타입
> - 원시 자료형 string, number, boolean, undefined의 의미를 이해할 수 있다.
> - 타입마다 다른 속성과 메서드가 있다는 것을 이해할 수 있다.
> - typeof 를 활용하여 특정 값의 타입을 확인할 수 있다.
> - 비교 시 엄밀한 비교( === 과 !== )의 필요성을 이해할 수 있다.

> ### Chapter3. 함수
> - 함수가 "작은 기능의 단위"라는 것을 이해할 수 있다.
> - 함수 선언을 위해 필요한 keyword, name, parameter, body에 대해 이해할 수 있다.
> - 함수의 호출과 리턴에 대해서 이해하고, 실제 코드로 작성하여 활용할 수 있다.
> - 함수 그 자체(func)와, 함수의 호출(func())를 구분하여 사용할 수 있다.
> - 매개변수(parameter)와 전달인자(argument)를 구분하여 사용할 수 있다.
> - 같은 기능을 하는 함수를 선언식, 표현식, 화살표 함수로 바꾸어 표현할 수 있다.

## 변수
변수란 메모리에 저장되어 있는 값을 사용할 수 있게 해주는 식별자 역할을 한다.

### 🧩 변수의 선언
- 변수의 선언은 `let` 문법을 사용하여 선언한다.

```javascript
// varible 이라는 이름을 가진 변수를 선언한다.
let varible;
```

### 🧩 변수의 할당
- 변수의 할당은 할당연산자 `=`를 사용하여 할당한다.
- 변수는 선언과 할당을 동시에 할 수 있다.

```javascript
// 변수 선언
let varible;
// 변수 할당
varible = "변수";
// 변수의 선언과 할당을 동시에 한다.
let v = "선언과 동시에 할당";
```

### 🧩 변수의 재할당
- 변수의 재할당이란 변수의 값을 바꾸는 행위를 뜻한다.

```javascript
// 변수의 선언과 할당
let varible = "초기값";
// 변수의 값 재할당
varible = "재할당";
```

### 💻 변수를 활용한 구구단

```javascript
// 변수만 바꿔주면 원하는 구구단을 출력이 가능하다.
let num = 2;
// 콘솔창으로 구구단 출력
console.log(num, '*', 1, '=', num * 1);
console.log(num, '*', 2, '=', num * 2);
console.log(num, '*', 3, '=', num * 3);
console.log(num, '*', 4, '=', num * 4);
console.log(num, '*', 5, '=', num * 5);
console.log(num, '*', 6, '=', num * 6);
console.log(num, '*', 7, '=', num * 7);
console.log(num, '*', 8, '=', num * 8);
console.log(num, '*', 9, '=', num * 9);
```

## 타입
데이터 (값)의 형식이다.

### 🧩 자바스크립트 자료형

- string : '', "", 안에 있는 모든 값을 총칭하며 문자들의 집합이다. 
- number : 실수, 정수 등등 수의 집합이다.
- boolean : true / false (참, 거짓)으로 나타낼 수 있는 값이다.
- undefined : 자바스크립트 엔진이 제공하는 값으로 값이 할당되지 않고 초기화 되어있을 때의 값이다.
- null : 개발자가 의도적으로 값이 없다라고 입력하는 값이다.

### 🧩 `typeof` 연산자
- 값의 형식을 알 수 있다.
```javascript
// 결과 : string
console.log(typeof "문자");
```

### 🧩  `===`, `==` 차이점

- `===`는 값과 타입을 동시에 비교한다.
- `==`는 값만 비교한다.

```javascript
const typeChecker1 = '1' == 1;
const typeChecker2 = '1' === 1;
// 결과 : true
console.log(typeChecker1);
// 결과 : false
console.log(typeChecker2);
```

### 🧩 데이터 타입의 변환

- number로 치환

```javascript
// Number() 함수를 이용한다.
let str = "1";
// 결과 : number
console.log(typeof Number(str));
```

- string으로 치환

```javascript
// String() 함수를 이용한다.
let num = 1;
// 결과 : string
console.log(typeof String(num));
```

## 함수
기능의 최소 단위

### 🧩 함수의 생성 방법
- 함수선언문
```javascript
function func(num1, num2) {
    return num1 + num2;
}
```
- 함수표현식
```javascript
const func = function(num1, num2) {
    return num1 + num2;
}
```
- 화살표함수
```javascript
const func = (num1, num2) => {
    return num1 + num2
}
```

### 🧩 함수의 형태

함수는 매개변수, 전달인자, 결과값으로 구성되어 있다.

- 매개변수 (parameter) : 함수에서 정한 입력값 / 정적이다.
- 전달인자 (arguments) : 함수를 실행할 때 넣어준 값 / 동적이다.
- 결과값 (return value) : 함수를 실행하고 연산이 완료되어 나온 값

```javascript
// num1과 num2의 함수의 매개변수이다.
const func = (num1, num2) => {
    /* {... 실행문} */
    // 결과값
    return num1 + num2;
}
// 1과 2는 전달인자이다.
console.log(func(1, 2));
```

🏆  Pair : 홍석민님