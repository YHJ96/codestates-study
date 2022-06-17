# this

---

- 대부분의 경우 this의 값은 함수를 호출한 방법이 결정합니다. 실행하는 중 할당으로 설정할 수 없고 함수를 호출할 때 마다 다를 수 있습니다. 즉 this의 값이 내가 어디에서 어떻게 호출하느냐에 따라 변한다는 것!
- this는 일반적으로 메소드를 호출한 객체가 저장되어 있는 속성이다.
- 자바스크립트에서 this가 참조하는 것은 함수가 호출되는 방식에 따라 결정되는데, 이것을 **“this binding”** 이라고 한다.
- this는 함수 내에서 함수 호출 맥락(context)를 의미한다. 맥락이라는 것은 상황에 따라서 달라진다는 의미인데 즉 함수를 어떻게 호출하느냐에 따라서 this가 가리키는 대상이 달라진다는 뜻이다.

## 📌 this의 값이 달라질 수 있는 경우들

### 🧩 전역범위

```javascript
// 1. 전역 범위에서 호출
console.log(this); // window {}
```

`this`를 호출하면 `window`라는 전역 객체를 가리킨다. window 객체라는 것은 현재 실행되고 있는 JS의 모든 변수, 함수, 객체, DOM 등을 포함하고 있는 객체로, 근원적인 객체이다

### 🧩 단순 함수 호출

```javascript
// 1. 일반 함수 범위에서 호출
function 바깥쪽() {
  console.log(this); // this는 window

  // 2. 함수 안에 함수가 선언된 내부 함수 호출
  function 안쪽() {
    console.log(this); // this는 window
  }
  안쪽();
}
바깥쪽();
```

- 일반적인 함수로 선언한 후 호출하는 경우, `this`는 `window` 객체이다.
- 함수 안에서 또 함수를 선언하더라도, `this`는 여전히 `window` 객체입니다.

### 🧩 객체의 메소드

```javascript
// 1. 객체 또는 클래스 안에서 메소드를 실행한다면 this는 Object 자기 자신
var man = {
  name: "Robert",
  hello: function () {
    // 2. 객체이므로 this는 man을 가리킴
    console.log("Hello " + this.name);
  },
};
man.hello(); // 3. Hello Robert
```

이제부터 `this`가 바뀌기 시작합니다. 그 첫 번째 시작은 객체나 클래스 내부에 선언된 메소드 함수입니다.

함수를 어떤 객체의 메소드로 호출하면 `this`의 값은 그 객체를 사용한다.

함수를 객체 외부에서 선언하고, 객체 안에서 호출하는 경우도 `this`는 해당 객체의 `this`를 참조합니다.

```javascript
// 3. 일반 함수 welcome을 선언
function welcome() {
  // 4. 여기서 this는 전역 객체 Window이므로, 만약 실행시키면 undefined가 뜸
  console.log("welcome " + this.name);
}

// 5. man 객체의 welcome 속성에 일반 함수 welcome을 추가
man.welcome = welcome;

// 6. welcome이 man 객체에서 호출되었으므로 welcome Robert가 출력됨
man.welcome();
```

이와는 반대로, 객체의 함수를 외부에서 호출할 때 `this`는 `Window`가 됩니다.

```javascript
// 7. man 객체의 thanks 속성에 함수를 선언
man.thanks = function () {
  // 8. man.thanks()를 호출하면 thanks Robert가 출력
  console.log("thanks " + this.name);
};

// 8. 이 함수를 객체 외부에서 참조
let thankYou = man.thanks;

// 9. 객체 외부이므로 this가 Window 객체가 되어서 thanks (undefined)가 출력
thankYou();

// 10. 그럼 또 다른 객체에서 이 함수를 호출하면 어떻게 될까?
women = {
  name: "Matilda",
  thanks: man.thanks, // 11. man.thanks 함수를 women.thanks에 참조
};

// 12. this가 포함된 함수가 호출된 객체가 women이므로 thanks Matilda가 출력
women.thanks();
```

메소드에서 내부 함수를 선언하는 경우는 `this`가 어떻게 되는지 보자

```javascript
let man = {
  name: "Robert",
  // 1. 이것은 객체의 메소드
  hello: function () {
    // 2. 객체의 메소드 안에서 함수를 선언하는 것이니까 내부 함수
    function getName() {
      // 3. 여기서 this가 무엇을 가리키고 있을까?
      return this.name;
    }
    console.log("hello " + getName()); // 4. 내부 함수를 출력시키고
  },
};
man.hello(); // 메소드를 실행시키면 undefined가 뜬다! this는 Window였던 것
```

객체의 메소드에서 `this` 가 객체를 가리키고 있던 것과는 다르게, 내부 함수에서 this는 `window` 객체를 가리킨다. 내부 함수는 메소드가 아니기 때문에, 단순 함수 호출 규칙에 따라서 `window`를 가리키고 있다.

## 📌 call(), apply()

### 🧩 call()

call() 메소드는 다른 객체 대신 메소드를 호출하는데 사용됩니다. 이 메서드를 사용하여 함수의 this 객체를 원래 컨텍스트에서 thisObj로 지정된 새로운 객체로 변경할 수 있습니다.

call() 함수를 사용하면, call에 인자로 this를 넘겨줌으로, this에 값에 따라 getType 함수 안에서 출력되는 this.type의 값이 달라지는 것을 확인 할 수 있습니다.

```javascript
type = "zero";
let type1 = { type: "one" };
let type2 = { type: "two" };

function getType() {
  console.log(this.type);
}

getType();
getType.call(this);
getType.call(type1);
getType.call(type2);

// zero
// zero
// one
// two
```

getType()으로 window.type이 출력되고, getType.call(this)도 마찬가지로 window.type이 출력된다. getType.call(type1)의 경우는 type1.type이 출력되고, getType.call(type2)의 경우는 type2.type이 출력된다.

### 🧩 apply

apply() 메소드는 call() 메소드와 동일 하나, call() 메소드는 인자 하나 하나를, apply()는 인자 리스트를 전달한다.

```javascript
function sum(arg1, arg2) {
  return arg1 + arg2;
}
alert(sum.apply(null, [1, 2]));

// 3
```
