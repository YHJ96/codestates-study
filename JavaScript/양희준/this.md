# this

## ๐ this๋?
- ์์ ์ด ์ํ ๊ฐ์ฒด, ์์ฑ๋ ์ธ์คํด์ค๋ฑ์ ๊ฐ๋ฆฌํค๋ ์ฐธ์กฐ๋ณ์์ด๋ค.
- this๋ ํจ์ํธ์ถ ๋ฐฉ์์ ๋ฐ๋ผ์ ๋์ ์ผ๋ก ๊ฒฐ์ ๋๋ค.
- this์ ๊ฐ๋ฆฌํค๋ ์ฐธ์กฐ๋ณ์๋ ํจ์ ํธ์ถ ์์ ์ ๊ฒฐ์ ๋๋ค.

## ๐ 5-2 this ๋ฐ์ธ๋ฉ ๋ฐฉ์
- ํจ์ํธ์ถ์ด๋ ๋ช์์ ์ผ๋ก this๋ฅผ ์ง์ ํ์ฌ this๊ฐ ๊ฐ๋ฆฌํค๋ ์ฐธ์กฐ๋ณ์๋ฅผ ๊ฒฐ์ ํ๋ค. ์ด๊ฒ์ this ๋ฐ์ธ๋ฉ์ด๋ผ๊ณ  ํ๋ค.
- ์ผ๋ฐํจ์๋ก์ ํธ์ถ ๋ฐฉ์ => window ๊ฐ์ฒด
- ๊ฐ์ฒด์ ๋ฉ์๋๋ก์์ ํธ์ถ => ๋ฉ์๋๋ก์ ํธ์ถํ ๊ฐ์ฒด
- ์์ฑ์ํจ์๋ก ์์ฑํ ์ธ์คํด์ค ํธ์ถ => ์ธ์คํด์ค ๊ฐ์ฒด
- ๋ช์์  ํธ์ถ => function.prototype.[apply, call, bind]
- Doc์์ Node๋ฅผ ํธ์ถํ๊ฑฐ๋ ์ด๋ฒคํธ๋ฅผ ์ฌ์ฉํ ๋ this๋ ํด๋น Node๋ฅผ ๊ฐ๋ฅดํจ๋ค.

## ๐ ์ผ๋ฐํจ์๋ก์์ this ํธ์ถ
> 
```javascript
function functionThis() {
    return this;
}
// ๊ฒฐ๊ณผ : window
console.log(functionThis());
```
์ด์ ๊ฐ์ด ์ผ๋ฐํจ์๋ก์์ ํธ์ถ์ this๋ ์ ์ญ๊ฐ์ฒด window๋ฅผ ๊ฐ๋ฆฌํจ๋ค.
```javascript
// ์ ์ญ๋ณ์ a ์ ์ธ
var a = 10;
function functionThis() {
    return this.a;
}
// ๊ฒฐ๊ณผ : 10
console.log(functionThis());
```
var๋ฅผ ์ฌ์ฉํ๋ฉด window๊ฐ์ฒด์์ a๋ฅผ ์ ์ธ๋์ด ์ฌ์ฉํ  ์ ์๋ค.

## ๐ ๋ฉ์๋๋ก์์ this ํธ์ถ
> 
```javascript
const obj = {
    objThis : function() {
        return this;
    }
}
// ๊ฒฐ๊ณผ : obj
console.log(obj.objThis());
```
๊ฐ์ฒด์ ๋ฉ์๋๋ก์์ ํธ์ถ์ ํธ์ถํ ๊ฐ์ฒด๋ฅผ ๊ฐ๋ฆฌํจ๋ค.
```javascript
const obj = {
    num : 10,
    objThis : function() {
        return this.num;
    }
}
// ๊ฒฐ๊ณผ : 10
console.log(obj.objThis());
```
๊ฐ์ฒด์ ์ธ์๋ฅผ ์ฌ์ฉํ  ์ ์๋ค.

## ๐ ์์ฑ์ํจ์๋ก์์ this ํธ์ถ
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
// instance1 ์ถ๋ ฅ
console.log(instance1.createFunctionThis());
 // instance2 ์ถ๋ ฅ
console.log(instance2.createFunctionThis());
// ์์ฑ์ ํจ์๋ก ์ธํด์ ๋ง๋ค์ด์ง ์๋ก์ด ๊ฐ์ฒด์ด๊ธฐ ๋๋ฌธ์ ๋ค๋ฅธ this๋ฅผ ๊ฐ์ง๋ค.
// ๊ฒฐ๊ณผ : fasle
console.log(instance1 === instance2);
```

์์ฑ์ํจ์๋ก ๋ง๋  ์ธ์คํด์ค๋ก์์ this๋ ์ธ์คํด์ค๋ ๊ฐ๋ฆฌํจ๋ค.

```javascript
function createFunction(num) {
    this.num = num;
    this.createFunctionThis = function() {
        return this.num;
    }
}
const instance1 = new createFunction(10);
const instance2 = new createFunction(20);
// ๊ฒฐ๊ณผ : 10
console.log(instance1.createFunctionThis());
// ๊ฒฐ๊ณผ : 20
console.log(instance2.createFunctionThis());
```
์ธ์คํด์ค์ ์ธ์๋ฅผ ์ฌ์ฉํ  ์ ์๋ค.

## ๐ this์ ๋ช์์  ํธ์ถ

### ๐ function.prototype.apply(์ฌ์ฉํ  this ๊ฐ์ฒด, [ํจ์์ธ์])

```javascript
const obj = {
    num : 10
}
function applyThis() {
    return this;
}
// ๊ฒฐ๊ณผ :  { num : 10 }
console.log(applyThis.apply(obj));
```
this๊ฐ obj๋ฅผ ๊ฐ๋ฆฌํค๋๋ก ๋ฐ์ธ๋ฉ ๋์๋ค.
```javascript
const obj = {
    num1 : 10
}
function applyThis(a, b) {
    const num2 = a;
    const num3 = b;
    return this.num1 + num2 + num3;
}
// ๊ฒฐ๊ณผ : 40
console.log(applyThis.apply(obj, [10, 20]));
```
์ด์ฒ๋ผ ์๋๋ window๊ฐ์ฒด๋ฅผ ๊ฐ๋ฆฌํค๋ this๋ฅผ ๋ช์์ ์ผ๋ก obj๋ฅผ ๊ฐ๋ฆฌํค๋๋ก ๋ฐ์ธ๋ฉ๋์๋ค. 

### ๐ function.prototype.call(์ฌ์ฉํ  this ๊ฐ์ฒด, ํจ์์ธ์)
```javascript
const obj = {
    num : 10
}
function callThis() {
    return this;
}
// ๊ฒฐ๊ณผ : { num : 10 }
console.log(callThis.call(obj));
```
this๊ฐ obj๋ฅผ ๊ฐ๋ฆฌํค๋๋ก ๋ฐ์ธ๋ฉ ๋์๋ค.
```javascript
const obj = {
    num1 : 10
}
function callThis(a, b) {
    const num2 = a;
    const num3 = b;
    return this.num1 + num2 + num3;
}
// ๊ฒฐ๊ณผ : 15
console.log(callThis.call(obj, 10, -5));
```
apply์ ๋๊ฐ์ด ์๋๋ window๊ฐ์ฒด๋ฅผ ๊ฐ๋ฆฌํค๋ this๋ฅผ ๋ช์์ ์ผ๋ก obj๋ฅผ ๊ฐ๋ฆฌํค๋๋ก ๋ฐ์ธ๋ฉ๋์๋ค.

> 
### ๐ function.prototype.bind(์ฌ์ฉํ  this ๊ฐ์ฒด, ํจ์์ธ์)

```javascript
const obj = {
    num : 10
}
function bindThis() {
    return this;
}
// bindthis ์ถ๋ ฅ
console.log(bindThis.bind(obj));
```
apply์ call๊ณผ๋ ๋ค๋ฅด๊ฒ bindThis ํจ์๊ฐ ์ถ๋ ฅ๋๋ค. ํจ์๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํด์ ๋ณ์์ ๋ฃ์ด์ค์ ์คํ์ ํด์ผํ๋ค.
```javascript
const obj = {
    num : 10
}
function bindThis() {
    return this;
}
const bindStart = bindThis.bind(obj);
// ๊ฒฐ๊ณผ : { num : 10 }
console.log(bindStart());
```
์ด์ ๊ฐ์ด ํจ์๋ฅผ ์คํํด์ค์ผ ํ๋ค.
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
// ๊ฒฐ๊ณผ : 40 ์ถ๋ ฅ
console.log(bindStart());
```
call๊ณผ apply๋ ํจ์์ ์ธ์๋ฅผ ๋ฃ๋ ๋ถ๋ถ์ด ๋ค๋ฅด์ง๋ง this๋ฅผ ํน์ ๊ฐ์ผ๋ก ์ง์ ํ๋ ๊ฒ์ด๋ค. ํ์ง๋ง bind๋ ํจ์์ this์ ๊ฐ์ ์๊ตฌ์ ์ผ๋ก ๋ฐ๊ฟ์ ์ฌ์ฉํ  ์ ์๋ค.

## ๐ this์ ํจ์ํธ์ถ ์์ ์ด๋?

```javascript
// window ๊ฐ์ฒด name ์ ์ธ
var name = 'KIM';
const obj = {
    name : 'LEE',
    info : function(callback) {
      // callback ํจ์์ ์คํ๊ฐ์ ๋ฐํ
        return callback();
    }
}
// callback function
function callback() {
    return `${this.name}์ ๋์ด๋ 20์ด ์๋๋ค.`;
}
// obj์์ ์๋ info ๋ฉ์๋์์ ์ฝ๋ฐฑํจ์๋ฅผ ์คํํ๋ค.
// ๊ฒฐ๊ณผ : KIM์ ๋์ด๋ 20์ด ์๋๋ค.
console.log(obj.info(callback));
```

์ด์ ๊ฐ์ด ์๋ํ๋ฉด window ๊ฐ์ฒด์ ์ ๊ทผํ์ฌ name์ ์ฝ์ด์๋ค. ์๋ํ๋ฉด info๋ ๋ฉ์๋๋ก์์ ํธ์ถ์ด ๋์ด info์ this๋ obj๋ฅผ ๊ฐ๋ฆฌํค์ง๋ง callback์ info์์์ ์ผ๋ฐํจ์๋ก ํธ์ถ์ด ๋์ด์๋ค. ๊ทธ๋ฌ๋ฏ๋ก this๋ ์ผ๋ฐํจ์์ ์คํ์ฒ๋ผ window๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ๋๋ค.

```javascript
var name = 'KIM';
const obj = {
    name : 'LEE',
    info : function(callback) {
      // callback ํจ์์ bind this๋ฅผ ํด์ค๋ค.
        const bindObj = callback.bind(this);
      // ๋ช์์ ์ผ๋ก ๋ณํ๋ bindObj๊ฐ ์ถ๋ ฅ
        return bindObj();
    }
}
function callback() {
    return `${this.name}์ ๋์ด๋ 20์ด ์๋๋ค.`;
}
// ๊ฒฐ๊ณผ : LEE์ ๋์ด๋ 20์ด ์๋๋ค.
console.log(obj.info(callback));
```
**๐ฅ bind์ this๋ง ๋ฃ์ด์ค ์ด์ ๋ info๋ ๊ฐ์ฒด์ ๋ฉ์๋๋ก์์ ํธ์ถ์ด ๋์ด์๊ธฐ ๋๋ฌธ์ this๊ฐ obj๋ฅผ ๊ฐ๋ฆฌํค๊ณ  ์๋ ์ํ์ด๋ค. ๊ทธ ๊ฐ๋ฆฌํค๋ this๋ฅผ ๋ช์์ ์ผ๋ก ๋ฐ์ธ๋ฉ ํด์ฃผ๋ฉด window ๊ฐ์ฒด๋ฅผ ๊ฐ๋ฆฌํค๋ callback ํจ์์ ๋ฐ์ธ๋ฉ ํ์ฌ bindObj ํจ์์ this๋ obj๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ๋๋ค. ์ด์ฒ๋ผ this๋ ํจ์ํธ์ถ ๋ฐฉ์๊ณผ ํธ์ถ์์ ์์ ๋์ ์ผ๋ก ๋ณํํ๊ฒ ๋๋ค.**