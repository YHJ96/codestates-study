# DOM μ‘°μ

## π 1. Element μμ±νκΈ°

`document.creatElement()` λ©μλλ₯Ό μ΄μ©ν΄ μλ‘μ΄ μμλ₯Ό λ§λ€ μ μμ΅λλ€. μ΄λ κ² λ§λ€μ΄μ§ μμλ DOMμ μΆκ°νλ λ©μλλ₯Ό μ¬μ©ν΄ μΆκ°νκΈ° μ κΉμ§λ DOMμ μΆκ°λμ§ μκ³  λ©λͺ¨λ¦¬μλ§ μ‘΄μ¬ν©λλ€.

```javascript
const tweetDiv = document.createElement("div");
```

μ½λλ₯Ό μμ±νκ³  htmlμ½λλ₯Ό λ΄λ divκ° μΆκ°λ νμ μ΄ μλ€. `tweetDiv` λΌλ μμλ νμ¬ κ³΅μ€λΆμ μνμ΄λ€. μλ¬΄κ²λ μ°κ²°μ΄ λμ΄μμ§ μμ νλμ λΈλκ° λ°©κΈ μμ±ν `tweetDiv` μ΄λ€.
![Alt text](https://s3.ap-northeast-2.amazonaws.com/urclass-images/zzQEJU2F0-1597040532407.gif)

## π 2. Element μΆκ°

κ³΅μ€μ λ μλ μλ¦¬λ¨ΌνΈλ₯Ό `append`ν΄μ μ€μ  μΉνμ΄μ§ μμ λ³΄μ¬μ§λ€.  
div μμμ μλ¬΄λ° λ΄μ©μ μλ ₯νμ§ μμμ λ³΄μ΄λ λ΄μ©μ΄ μμ§λ§ divμμκ° μμ±λκ²μ λ³Ό μ μλ€.

```javascript
document.body.append(tweetDiv);
```

![Alt text](https://s3.ap-northeast-2.amazonaws.com/urclass-images/80LDLyQyZ-1597040631488.gif)

## π§© append vs appendChild μ°¨μ΄

appendμ appendChild λ©μλλ λͺ¨λ λΆλͺ¨ λΈλμ μμ λΈλλ₯Ό μΆκ°νλ λ©μλ, νμ§λ§ λ©μλμμλ λͺκ°μ§ μ°¨μ΄μ μ΄ μ‘΄μ¬νλ€.

### π append()

append λ©μλλ₯Ό νμ©νλ©΄ λΈλ κ°μ²΄(node object)λ DOMString(text)λ₯Ό μ¬μ©ν  μ μμ΅λλ€. λ νλ²μ μ¬λ¬ κ°μ μμ μμλ₯Ό μ€μ ν  μ μμ΅λλ€.

- λΈνΈ κ°μ²΄ μ¬μ© μμ

```javascript
// λΈλ κ°μ²΄ μ½μ
const parent = document.createElement("div");
const child = document.createElement("p");

parent.append(child);

// κ²°κ³Ό
// <div> <p> </p> </div>
```

- λ¬Έμμ΄(DOMString) μ¬μ© μμ

```javascript
// DOMString μ½μ
const parent = createElement("div");
parent.append("μμ΄μ€ν¬λ¦Ό");

// κ²°κ³Ό
// <div>μμ΄μ€ν¬λ¦Ό</div>
```

- μ¬λ¬ κ°μ μμ μμλ₯Ό μ€μ νλ μμ

```javascript
const div = document.createElement("div");
const span = document.createElement("span");
const p = document.createElement("p");

document.body.append(div, "Hello", span, p);

// κ²°κ³Ό
<body>
  <div></div>
  Hello
  <span></span>
  <p></p>
</body>;
```

- append λ©μλλ return κ°μ λ°ννμ§ μμ΅λλ€.

```javascript
const div = document.createElement("div");
const span = document.createElement("span");
const p = document.createElement("p");

console.log(document.body.append(div, "Hello", span, p)); // undefined
```

### appendChild()

- λΈλ κ°μ²΄ μ¬μ© μμ
  appendChild λ©μλλ append λ©μλμλ λ€λ₯΄κ² μ€μ§ node κ°μ²΄λ§ λ°μ μ μλ€. appendλ μ¬λ¬ κ°μ λΈλμ λ¬Έμλ₯Ό μΆκ°ν  μ μλ λ°λ©΄μ appendChild λ©μλλ νλ²μ μ€μ§ νλμ λΈλλ§μ μΆκ°ν  μ μλ€.

```javascript
const parent = document.createElemnet("div");
const child = document.createElement("p");

parent.appendChild(child);

// κ²°κ³Ό
// <div><p></p></div>
```

- λ¬Έμμ΄ (DOMString) μ¬μ© μμ
  appendChild λ©μλλ DOMStringμ λ£μ κ²½μ° μλ¬κ° λ°μνλ€.

```javascript
// DOMString μ½μ
const parent = document.createElement("div");

parent.appendChild("μμ΄μ€ν¬λ¦Ό");
// Uncaught TypeError: Faild to execute 'appendChild' on 'Node':parameter 1 is not of type 'Node'
```

- appendChild λ©μλλ return κ°μ λ°νν©λλ€.

```javascript
const div = document.createElement("div");
const span = document.createElement("span");

console.log(document.body.appendChild(div)); // div(Node object)
```

## π 3. Element μ‘°ν

**querySelector()** λ νΉμ  name,id,classλ₯Ό μ ννμ§ μκ³  cssμ νμλ₯Ό μ¬μ©νμ¬ μμλ₯Ό μ°Ύμ΅λλ€.

κ°μ id λλ class μΌ κ²½μ° μ€ν¬λ¦½νΈμ μ΅μλ¨ μμλ§ λ‘μ§μ ν¬ν¨ν©λλ€.

- querySelector(#id) => id κ° idλ₯Ό κ°μ§ μμλ₯Ό μ°Ύμ΅λλ€.
- querySelector(.class) => class κ° classλ₯Ό κ°μ§ μμλ₯Ό μ°Ύμ΅λλ€.

`querySelector` μ `.tweet` μ μ²« λ²μ§Έ μΈμλ‘ λ£μΌλ©΄, ν΄λμ€ μ΄λ¦μ΄ tweet μΈ HTML μλ¦¬λ¨ΌνΈ μ€ μ²« λ²μ§Έ μλ¦¬λ¨ΌνΈλ₯Ό μ‘°νν  μ μμ΅λλ€.

```javascript
const oneTweet = document.querySelector(".tweet");
```

ν΄λμ€ μ΄λ¦μ΄ tweetμΈ μμκ° μ¬λ¬κ° μλ€. λ³μ onetweet μ ν λΉλ μμλ νλλΏμ΄λ€. μ¬λ¬κ°μ μμλ₯Ό κ°μ Έμ€κΈ° μν΄ querySelectorAll μ μ¬μ©νλ€.

```javascript
const tweets = document.querySelectorAll(".tweet");
```

CREATEμμ μμ±ν div μμλ₯Ό containerμ λ£μ μ€λΉλ₯Ό λ§μ³€μ΅λλ€. λ€μ μ½λλ₯Ό μλ ₯νλ©΄, containerμ λ§¨ λ§μ§λ§ μμ μμλ‘ tweetDivλ₯Ό μΆκ°ν©λλ€.

```javascript
const container = document.querySelector("#container");
const tweetDiv = document.createElement("div");
container.append(tweetDiv);
// tweetDivλ₯Ό containerμ λ§μ§λ§ μμ μμλ‘ μΆκ°ν©λλ€.
```

![Alt text](https://s3.ap-northeast-2.amazonaws.com/urclass-images/VnqXiZ-_4-1618885682009.gif)

- tweetDivλ₯Ό containerμ λ§μ§λ§ μμ μμλ‘ μΆκ°ν λͺ¨μ΅

![Alt text](https://s3.ap-northeast-2.amazonaws.com/urclass-images/PHmvd-SCC-1597040922206.gif)

- idκ° containerμΈ μλ¦¬λ¨ΌνΈμ λ§μ§λ§ μμ μμλ‘ tweetDivλ₯Ό μΆκ°ν©λλ€.

---

- getElementById()

  => Elementμ idλ‘ μ κ·Όν  μ μλ€.

- getElementByClassName() / getElementsByClassName()

  => Elementμ class μ΄λ¦μΌλ‘ μ κ·Όν  μ μλ€.

## π 4.Element update

**_ClassList.add()_**  
Elementμ class nameμ μΆκ°ν  μ μλ€.

```javascript
let aElement = document.createElement("a");

aElement.classList.add("name");
```

**_textContent_**

- Element λ° Nodeμ νμ€νΈλ₯Ό μΆκ°ν  μ μλ λ©μλμ΄λ€.
  λ°νκ°μ λ¬Έμμ΄ λλ nullμ΄λ€.
- μ νν μμμμ HTML μμλ₯Ό μ κ±°ν μμν νμ€νΈ λ°μ΄ν°μ κ°

```javascript
aElement.textContent = "awesome";
```

**_innerHTML_**

```javascript
aElement.innerHTML = "awesome";
```

- innerHTMLλ μ΄λ¦ κ·Έλλ‘ HTMLμ λ°ννλ€. HTML tagλ₯Ό μ§μ  μ½μνμ¬ μ€ννλ ννμ λ©μλλ λ μ΄λ° μνμ κ°μ§κ³  μλ€.
- μ νν μμμ HTML νκ·Έλ₯Ό κ·Έλλ‘ μ κ³΅νμ¬ λ³΄μμ μ·¨μ½(μ¬μ©μλ‘λΆν° μ λ¬λ°μ μ½νμΈ λ₯Ό μΆκ°ν  λλ μ¬μ©νμ§ μλ κ²μ΄ μ’μ)

## π 5. Element μ κ±°

**_removeChild() VS remove()_**  
μμ λΈλλ₯Ό μ­μ νλ λ©μλμ΄λ€.  
remove()λ λΈλλ₯Ό λ©λͺ¨λ¦¬μμ μ­μ νκ³  μ’λ£νλ€.
λ°λ©΄μ removeChild()λ λ©λͺ¨λ¦¬μ ν΄λΉ λΈλλ κ·Έλλ‘ μ‘΄μ¬νλ©°, λΆλͺ¨ λΈλμμ λΆλͺ¨-μμκ΄κ³λ₯Ό λμ΄ DOM νΈλ¦¬μμ μ κ±°νλ€. μ΅μ’μ μΌλ‘λ κ΄κ³λ₯Ό λμ ν΄λΉ λΈλμ μ°Έμ‘°λ₯Ό λ°ννλ€.

![Alt text](https://velog.velcdn.com/images%2Fbining%2Fpost%2F4ff9355a-14dd-42bd-b6ae-0fd1168b5147%2Fimage.png)

```javascript
const container = document.querySelector("#container");
const tweetDiv = document.createElement("div");
container.append(tweetDiv);
```

```javascript
tweetDiv.remove(); // append νλ μλ¦¬λ¨ΌνΈλ₯Ό μ­μ ν  μ μλ€.
```
