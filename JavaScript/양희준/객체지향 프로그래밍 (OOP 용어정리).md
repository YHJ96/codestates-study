# 객체지향 프로그래밍 (OOP 용어정리)

## 📌 객체지향 프로그래밍이란?

시간의 흐름에 따라서 코드를 작성하는 절차적 프로그래밍이랑 반대되는 개념으로 모든 사물들을 객체로 표현하여 독립된 객체간의 소통으로 이루어진 프로그래밍이다.

## 📌 객체지향 프래그래밍의 특징 4가지

1. 추상화
- 사용자가 쉽게 사용할 수 있도록 프로그램에서 필요한 속성만 표현하는 것 즉 내부의 복잡한 내용들은 숨기고 필요한 내용만 보여주는 것이며 인터페이스가 간단해진다.

```javascript
class Person {
    constructor(name, age) {
        this.info = { name, age };
    }
    getInfo() {
        return this.info;
    }
    addInfo(key, value) {
        this.info[key] = value;
    }
}

const person = new Person("홍길동", 22);
// 사람의 정보를 추가하는 행위 이와 같이 안의 코드는 몰라도 어떤 동작을 하는 함수인지 알 수 있다.
person.addInfo("address", "seoul");
// 사람의 정보를 가져오는 함수
console.log(person.getInfo());
```

**🔥 복잡한 코드 없이 함수의 이름으로 어떤 동작을 하는 함수인지 알아볼 수 있는 방법이 추상화이다.**

2. 캡슐화
- 연관된 변수와 함수들을 하나의 그룹으로 묶어 하나의 단위 즉 객체로 만드는 것이며 변수는 프로퍼티 함수는 메소드라고 생각하면 된다. 코드의 재사용성을 증가시킨다. 
- 은닉성이라는 성질을 가지고 있기 때문에 접근하지 못하는 프로퍼티는 클래스내에서만 참조해야한다.

```javascript
class Person {
    // private 필드 선언
    #name;
    #age;
    constructor(name, age) {
        this.#name = name;
        this.#age = age;
    }
    log() {
        console.log(`이름은 ${this.#name} 입니다.`);
        console.log(`나이는 ${this.#age}살 입니다.`);
    }
}

const person = new Person("홍길동", 22);
/*
결과 : 
이름은 홍길동 입니다.
나이는 22살 입니다.
*/
person.log();
// undefined
console.log(person.name);
// 오류 발생
console.log(person.#name);
```

3. 상속
- 부모의 특징을 자식이 사용할 수 있으며 불필요한 코드사용을 줄일 수 있게 해준다.
```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
}
// Person 클래스를 Student 클래스에 상속한다.
class Student extends Person{
    constructor(name, age, grade) {
        super(name, age)
        this.grade = grade;
    }
}

const student = new Student("YHJ", 20, 4);
// 결과 : YHJ
console.log(student.name);
// 결과 : 4
console.log(student.grade);
```
4. 다형성
- 하나의 객체가 여러가지 타입을 가지는 특성으로 오버라이딩이 대표적이다.
```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    log() {
        console.log(`당신의 이름은 ${this.name}입니다.`)
    }
}

class Student extends Person{
    constructor(name, age, grade) {
        super(name, age)
        this.grade = grade;
    }
    // 오버라이딩
    log(value) {
        // value에 결과에 따라 부모의 메소드나 현재 클래스의 메소드 사용여부를 결정한다.
        if (value === "grade") console.log(`당신의 학년은 ${this.grade}학년 입니다.`);
        else if (value === "name") super.log();
    }
}

const student = new Student("YHJ", 20, 4);
// 결과 : 당신의 이름은 YHJ입니다.
student.log("name");
// 결과 : 당신의 학년은 4학년 입니다.
student.log("grade");
```

## 📌 프로퍼티와 메소드
- 프로퍼티 : 의미로는 속성으로 객체의 특징이다.
- 메소드 : 의미로는 행동으로 JavaScript에서는 함수로 된 프로퍼티이다.

```javascript
const Object = {
    // 프로퍼티는 객체의 각각의 요소라고 생각해도 된다.
    property: "property",
    // 메소드는 프로퍼티이며 함수로된 프로퍼티를 메소드라고 한다.
    method: function() {
        console.log("method");
    }
}
```

## 📌 인스턴스와 객체의 차이점

객체 : 키와 값으로 구성되어있는 자료구조이다.
인스턴스 : 자바스크립트에서는 생성자함수 함수에 new 연산자를 사용하여 생성한 객체이다.   

```javascript
// 객체
const object = {
    a: 1,
    b: 2
}
// 생성자 함수
function Instance(value) {
    this.value = value;
    this.log = function() {
        console.log(this.value);
    }
}
// 생성자 함수에 값을 다르게 줘서 2개의 인스턴스를 생성하였다.
const instance1 = new Instance(1);
const instance2 = new Instance(2);
// 1 출력
instance1.log();
// 2 출력
instance2.log();
```

인스턴스는 생성자 함수가 만들어낸 객체이다. 객체의 프로퍼티를 동적으로 변경 시켜주고 싶을 때 생성자함수를 만들고 인스턴스를 생성한다. 즉 구조를 생성하고 그 구조에 값만 바꿔줘서 사용하는 것이 인스턴스이다.

## 📌 정적 메소드와 프로토타입 메소드

- 정적 메소드: 인스턴스를 생성하지 않고 직접 함수를 호출할 수 있다.
- 프로토타입 메소드: 인스턴스를 생성해서 호출할 수 있다.

```javascript
// copyArr 생성
function CopyArray(arr) {
    this.arr = [];
    
    for(let i = 0; i < arguments.length; i++) {
        this.arr[i] = arguments[i];
    }
    // 예제는 이해를 돕기 위해 프로토타입 메소드가 아닌 인스턴스 메소드로 구현
    this.push = function(value) {
        const lastIndex = this.arr.length - 1;
        this.arr[lastIndex + 1] = value;
        return this.arr.length;
    }
    return this.arr;
}
// 정적 메소드
CopyArray.isArray = function(value) {
    return Array.isArray(value);
}
// 실제 배열의 push 메소드처럼 작동한다.
const copyArr = new CopyArray(1,2,3,4);
// 결과 : [1, 2, 3, 4]
console.log(copyArr);
// push 5
copyArr.push(5);
// 결과 : [1, 2 ,3, 4, 5]
console.log(copyArr);
/* 배열의 실제 선언 방법 */
const arr = new Array(1,2,3,4);
```

- 배열을 일반적으로 const arr = [1,2,3,4]으로 사용하면 자바스크립트 엔진은 const arr = new Array(1,2,3,4)의 과정으로 만듬 (Wrapper 객체).
- 사실 배열 const arr = [1,2,3,4]라고 선언한 것이 풀어서 말하면 Array 생성자 함수의 요소가 1,2,3,4인 인스턴스를 만든 과정이므로 내부 생성자 함수에 이미 만들어진 메소드들인 push, pop, 등등의 메소드를 사용할 수 있다.
- 정적 메소드는 Array 자체에 걸려 있는 메소드이기 때문에 인스턴스를 생성할 필요가 없어서 Array. --- 의 형태로 바로 호출할 수 있다.

### 🧩 [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)에서 배열의 내장 객체를 확인 할 때 방법

- 생성자함수.prototype.메소드 형태인 것은 인스턴스를 생성해서 만들 결과물에 직접 함수를 사용한다.
- 생성자함수.메소드 형태인 것은 직접 그 생성자함수에 .을 붙혀서 사용한다.

```javascript
// 인스턴스 생성
const arr = [1,2,3,4]
/*
이 과정을 자동적으로 해준다고 생각하면 편함.
const arr = new Array(1,2,3,4);
*/
// 인스턴스가 담겨있는 변수에서 함수를 호출
arr.indexOf(1);
// 결과 : true
Array.isArray(arr);
```