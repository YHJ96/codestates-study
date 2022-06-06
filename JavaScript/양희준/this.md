# this

## 📌 this란?
- 자신이 속한 객체, 생성된 인스턴스등을 가리키는 참조변수이다.
- this는 함수호출 방식에 따라서 동적으로 결정된다.
- this의 가리키는 참조변수는 함수 호출 시점에 결정된다.

## 📌 5-2 this 바인딩 방식
- 함수호출이나 명시적으로 this를 지정하여 this가 가리키는 참조변수를 결정한다. 이것을 this 바인딩이라고 한다.
- 일반함수로서 호출 방식 => window 객체
- 객체의 메서드로서의 호출 => 메서드로서 호출한 객체
- 생성자함수로 생성한 인스턴스 호출 => 인스턴스 객체
- 명시적 호출 => function.prototype.[apply, call, bind]
- Doc에서 Node를 호출하거나 이벤트를 사용할때 this는 해당 Node를 가르킨다.

## 📌 일반함수로서의 this 호출
> 
```javascript
function functionThis() {
    return this;
}
// 결과 : window
console.log(functionThis());
```
이와 같이 일반함수로서의 호출의 this는 전역객체 window를 가리킨다.
```javascript
// 전역변수 a 선언
var a = 10;
function functionThis() {
    return this.a;
}
// 결과 : 10
console.log(functionThis());
```
var를 사용하면 window객체안에 a를 선언되어 사용할 수 있다.

## 📌 메서드로서의 this 호출
> 
```javascript
const obj = {
    objThis : function() {
        return this;
    }
}
// 결과 : obj
console.log(obj.objThis());
```
객체의 메서드로서의 호출은 호출한 객체를 가리킨다.
```javascript
const obj = {
    num : 10,
    objThis : function() {
        return this.num;
    }
}
// 결과 : 10
console.log(obj.objThis());
```
객체의 인자를 사용할 수 있다.

## 📌 생성자함수로서의 this 호출
> 
```javascript
function createFunction(num) {
    this.num = num;
    this.createFunctionThis = function() {
        return this;
    }
}
const instance1 = new createFunction(10);
const instance2 = new createFunction(20);
// instance1 출력
console.log(instance1.createFunctionThis());
 // instance2 출력
console.log(instance2.createFunctionThis());
// 생성자 함수로 인해서 만들어진 새로운 객체이기 때문에 다른 this를 가진다.
// 결과 : fasle
console.log(instance1 === instance2);
```

생성자함수로 만든 인스턴스로서의 this는 인스턴스는 가리킨다.

```javascript
function createFunction(num) {
    this.num = num;
    this.createFunctionThis = function() {
        return this.num;
    }
}
const instance1 = new createFunction(10);
const instance2 = new createFunction(20);
// 결과 : 10
console.log(instance1.createFunctionThis());
// 결과 : 20
console.log(instance2.createFunctionThis());
```
인스턴스의 인자를 사용할 수 있다.

## 📌 this의 명시적 호출

### 📋 function.prototype.apply(사용할 this 객체, [함수인자])

```javascript
const obj = {
    num : 10
}
function applyThis() {
    return this;
}
// 결과 :  { num : 10 }
console.log(applyThis.apply(obj));
```
this가 obj를 가리키도록 바인딩 되었다.
```javascript
const obj = {
    num1 : 10
}
function applyThis(a, b) {
    const num2 = a;
    const num3 = b;
    return this.num1 + num2 + num3;
}
// 결과 : 40
console.log(applyThis.apply(obj, [10, 20]));
```
이처럼 원래는 window객체를 가리키는 this를 명시적으로 obj를 가리키도록 바인딩되었다. 

### 📋 function.prototype.call(사용할 this 객체, 함수인자)
```javascript
const obj = {
    num : 10
}
function callThis() {
    return this;
}
// 결과 : { num : 10 }
console.log(callThis.call(obj));
```
this가 obj를 가리키도록 바인딩 되었다.
```javascript
const obj = {
    num1 : 10
}
function callThis(a, b) {
    const num2 = a;
    const num3 = b;
    return this.num1 + num2 + num3;
}
// 결과 : 15
console.log(callThis.call(obj, 10, -5));
```
apply와 똑같이 원래는 window객체를 가리키는 this를 명시적으로 obj를 가리키도록 바인딩되었다.

> 
### 📋 function.prototype.bind(사용할 this 객체, 함수인자)

```javascript
const obj = {
    num : 10
}
function bindThis() {
    return this;
}
// bindthis 출력
console.log(bindThis.bind(obj));
```
apply와 call과는 다르게 bindThis 함수가 출력된다. 함수를 사용하기 위해서 변수에 넣어줘서 실행을 해야한다.
```javascript
const obj = {
    num : 10
}
function bindThis() {
    return this;
}
const bindStart = bindThis.bind(obj);
// 결과 : { num : 10 }
console.log(bindStart());
```
이와 같이 함수를 실행해줘야 한다.
```javascript
const obj = {
    num1 : 10
}
function bindThis(a, b) {
    const num2 = 10;
    const num3 = 20;
    return this.num1 + num2 + num3;
}
const bindStart = bindThis.bind(obj);
// 결과 : 40 출력
console.log(bindStart());
```
call과 apply는 함수의 인자를 넣는 부분이 다르지만 this를 특정값으로 지정하는 것이다. 하지만 bind는 함수의 this의 값을 영구적으로 바꿔서 사용할 수 있다.

## 📌 this의 함수호출 시점이란?

```javascript
// window 객체 name 선언
var name = 'KIM';
const obj = {
    name : 'LEE',
    info : function(callback) {
      // callback 함수의 실행값을 반환
        return callback();
    }
}
// callback function
function callback() {
    return `${this.name}의 나이는 20살 입니다.`;
}
// obj안에 있는 info 메서드에서 콜백함수를 실행한다.
// 결과 : KIM의 나이는 20살 입니다.
console.log(obj.info(callback));
```

이와 같이 작동하면 window 객체에 접근하여 name을 읽어왔다. 왜냐하면 info는 메서드로서의 호출이 되어 info의 this는 obj를 가리키지만 callback은 info안에서 일반함수로 호출이 되어있다. 그러므로 this는 일반함수의 실행처럼 window를 가리키게 된다.

```javascript
var name = 'KIM';
const obj = {
    name : 'LEE',
    info : function(callback) {
      // callback 함수에 bind this를 해준다.
        const bindObj = callback.bind(this);
      // 명시적으로 변환된 bindObj값 출력
        return bindObj();
    }
}
function callback() {
    return `${this.name}의 나이는 20살 입니다.`;
}
// 결과 : LEE의 나이는 20살 입니다.
console.log(obj.info(callback));
```
**🔥 bind에 this만 넣어준 이유는 info는 객체의 메서드로서의 호출이 되어있기 때문에 this가 obj를 가리키고 있는 상태이다. 그 가리키는 this를 명시적으로 바인딩 해주면 window 객체를 가리키는 callback 함수에 바인딩 하여 bindObj 함수의 this도 obj를 가리키게 된다. 이처럼 this는 함수호출 방식과 호출시점에서 동적으로 변화하게 된다.**