# DOM ์กฐ์๋ฐฉ๋ฒ

## ๐ ์์ ๋ธ๋ ์ฝ๋ ๋ฐฉ๋ฒ (READ)

### ๐งฉ id๋ฅผ ์ด์ฉํด์ ์์ ๋ธ๋ ์ฝ๋ ๋ฐฉ๋ฒ   
**๐ Doucument.prototype.getElementById("id ์ด๋ฆ")**
```HTML
<!DOCTYPE html>
<!--id๋ ๊ณ ์ ํ ๊ฐ์ผ๋ก ํ๋์ ๋ธ๋๋ง ํ์ํ๋ค.-->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul>
            <li id="red">Red</li>
            <li id="orange">Orange</li>
            <li id="yellow">Yellow</li>
        </ul>
    </body>
    <script>
        // id๋ฅผ ์ด์ฉํ์ฌ ์์ ๋ธ๋๋ฅผ ํ๋
        const $red = document.getElementById("red");
        console.log($red);
    </script>
</html>
```
### ๐งฉ ํ๊ทธ ์ด๋ฆ์ผ๋ก ์์ ๋ธ๋ ์ฝ๋ ๋ฐฉ๋ฒ   
**๐ Document.prototype.getElementsByTagNames("ํ๊ทธ ์ด๋ฆ")**   
**๐ Element.prototype.getElementsByTagNames("ํ๊ทธ ์ด๋ฆ")**

```HTML
<!DOCTYPE html>
<!--ํด๋น ๋ธ๋์ ๋ถํฐ ์์ํ์ฌ ํ์ ๋ธ๋๋ง ๋ชจ๋ ํ์ํ์ฌ ์กฐ๊ฑด์ ๋ง๊ฒ ๋ฐํํ๋ค.-->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="color">
            <li id="red">Red</li>
            <li id="orange">Orange</li>
            <li id="yellow">Yellow</li>
        </ul>
        <ul id="animals">
            <li id="dog">Dog</li>
            <li id="cat">Cat</li>
        </ul>
    </body>
    <script>
        // document๋ DOM ํธ๋ฆฌ์ ๋ฃจํธ ๋ธ๋๋ก์จ DOM์ ์ฒด์์ ํ์ํ๋ค.
        const $li = document.getElementsByTagName("li");
        const $animals = document.getElementById("animals");
        // id๊ฐ animals์ธ ์์ ๋ธ๋๋ถํฐ ํ์ํ๋ค.
        const $animalsli = $animals.getElementsByTagName("li");
        // ๊ฒฐ๊ณผ: HTMLCollection(5)ย [li#red, li#orange, li#yellow, li#dog ...]
        console.log($li);
        // ๊ฒฐ๊ณผ: HTMLCollection(2)ย [li#dog, li#cat, dog: li#dog, cat: li#cat]
        console.log($animalsli);
    </script>
</html>
```

### ๐งฉ class๋ฅผ ์ด์ฉํด์ ์์ ๋ธ๋ ์ฝ๋ ๋ฐฉ๋ฒ   
**๐ Document.prototype.getElementsByClassName("ํด๋์ค ๊ฐ")**   
**๐ Element.prototype.getElementsByClassName("ํด๋์ค ๊ฐ")**

```HTML
<!DOCTYPE html>
<!--ํด๋น ๋ธ๋์ ๋ถํฐ ์์ํ์ฌ ํ์ ๋ธ๋๋ง ๋ชจ๋ ํ์ํ์ฌ ์กฐ๊ฑด์ ๋ง๊ฒ ๋ฐํํ๋ค.-->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul class="color">
            <li class="color red">Red</li>
            <li class="color orange">Orange</li>
            <li class="color yellow">Yellow</li>
        </ul>
        <ul id="animals">
            <li class="animals dog">Dog</li>
            <li class="animals cat">Cat</li>
        </ul>
    </body>
    <script>
        // class ์ด๋ฆ์ค color๊ฐ ๋ค์ด๊ฐ์๋ ๋ชจ๋  ์์ ๋ธ๋ ํ์
        const $color = document.getElementsByClassName("color");
        // class ์ด๋ฆ์ค color์ red๊ฐ ๋ค์ด๊ฐ์๋ ๋ชจ๋  ์์ ๋ธ๋ ํ์
        const $red = document.getElementsByClassName("color red");
        // id๊ฐ animals์ธ ์์ ๋ธ๋ ํ์
        const $animals = document.getElementById("animals");
        /* id๊ฐ animals์ธ ์์ ๋ธ๋์ ์์์ค 
           class ์ด๋ฆ์ animals๊ฐ ๋ค์ด๊ฐ์๋ ์์ ๋ธ๋ ํ์ */
        const $animalsli = $animals.getElementsByClassName("animals");
        // ๊ฒฐ๊ณผ : HTMLCollection(4)ย [ul.color, li.color.red, li.color.orange ...]
        console.log($color);
        // ๊ฒฐ๊ณผ : HTMLCollectionย [li.color.red]
        console.log($red);
        // ๊ฒฐ๊ณผ : HTMLCollection(2)ย [li.animals.dog, li.animals.cat]
        console.log($animalsli);
    </script>
</html>
```

### ๐งฉ CSS Selector๋ฅผ ์ด์ฉํ ์์ ๋ธ๋ ์ฝ๋ ๋ฐฉ๋ฒ   
**๐ Document.querySelector("CSS ์ ํ์ ๋ฌธ๋ฒ")**   
**๐ Element.querySelector("CSS ์ ํ์ ๋ฌธ๋ฒ")**   
**๐ Document.querySelectorAll("CSS ์ ํ์ ๋ฌธ๋ฒ")**   
**๐ Element.querySelectorAll("CSS ์ ํ์ ๋ฌธ๋ฒ")**   </br> </br>
**๐ฅ ์ ์ผ ๋ง์ด ์ฌ์ฉํ๋ ์์ ๋ธ๋ ์ ๊ทผ ๋ฐฉ๋ฒ**   
**querySelector๋ ์กฐ๊ฑด์ ๋ง๋ ์ฒซ๋ฒ์งธ ๋ธ๋๋ง ๋ฐํํ์ง๋ง querySelectorAll์ ์กฐ๊ฑด์ ๋ง๋ ๋ชจ๋  ๋ธ๋๋ฅผ NodeList์ ๋ด์์ ๋ฐํํ๋ค.**

```CSS
/* ์ ์ฒด ์ ํ์: ๋ชจ๋  ์์๋ฅผ ์ ํ */
*

/* ํ๊ทธ ์ ํ์: ๋ชจ๋  ํ๊ทธ๋ฅผ ์ ํ */
li

/* id ์ ํ์: id ๊ฐ์ด color์ธ ์์ ๋ชจ๋ ์ ํ */
#color

/* class ์ ํ์: class ๊ฐ์ด color์ธ ์์ ๋ชจ๋ ์ ํ */
.color

/* ์์ฑ ์ ํ์: input ์์ ์ค type ์์ฑ์ด text์ธ ์์ ๋ชจ๋ ์ ํ */
input[type=text]

/* ํ์ ์ ํ์: ul ์์์ ํ์์ค li ํ๊ทธ์ธ ์์ ๋ชจ๋ ์ ํ */
ul li

/* ์์ ์ ํ์: ul ์์์ ์์์ค li ํ๊ทธ์ธ ์์ ๋ชจ๋ ์ ํ */
ul > li

/* ์ธ์  ํ์  ์ ํ์: div ์์์ ํ์  ์์ ์ค์ span ์ด๋ฉฐ ๋ฐ๋ก ๋ค์ ์์ ๋ฐํ */
div + span

/* ์ผ๋ฐ ํ์  ์ ํ์: div ์์์ ํ์  ์์ ์ค์ span ๋ชจ๋ ์ ํ */
div ~ span

/* ๊ฐ์ ํด๋์ค ์ ํ์: ๋์ค์ ์ฌ์ฉํ  ๋ ์ฐพ์๋ณด๊ธฐ */
a:hover

/* ๊ฐ์ ์์ ์ ํ์: ๋์ค์ ์ฌ์ฉํ  ๋ ์ฐพ์๋ณด๊ธฐ */
a::before
```

```HTML
<!DOCTYPE html>
<!--ํด๋น ๋ธ๋์ ๋ถํฐ ์์ํ์ฌ ์์ ๋ธ๋๋ง ๋ชจ๋ ํ์ํ์ฌ CSS ์ ํ์์ ๋ง๊ฒ ๋ฐํํ๋ค.-->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="nav-container1">
            <li class="nav1">nav1</li>
            <li class="nav2">nav2</li>
            <ul id="nav-container2">
                <li class="nav3">nav3</li>
                <li class="nav4">nav4</li>
            </ul>
        </ul>
        <input type="number" placeholder="number">
        <input type="text" placeholder="text">
        <input type="text" placeholder="text">
        <div class="form">
            <div></div>
            <span class="text1">Hello</span>
            <span class="text2">World</span>
        </div>
    </body>
    <!--
        querySelectorAll์ ์กฐ๊ฑด์ ๋ง๋ ๋ธ๋๋ฅผ ์ ๋ถ NodeList์ ๋ด์์ ๋ชจ์ ๋ฐํํ๋ค.
        querySelector๋ ์กฐ๊ฑด์ ๋ง๋ ๋ธ๋์ค ์ฒซ ๋ฒ์งธ ์์๋ง ๋ฐํํ๋ค.
    -->
    <script>
        // ๋ชจ๋  ์์ ๋ธ๋ ํ์
        const $all = document.querySelectorAll("*");
        // ๋ชจ๋  li ํ๊ทธ ์์๋ง ํ์
        const $liTag = document.querySelectorAll("li");
        // id๊ฐ #nav-container1์ธ ๋ชจ๋  ์์ ํ์
        const $navContaniner1 = document.querySelectorAll("#nav-container1");
        // class ๊ฐ์ด .nav1์ธ ๋ชจ๋  ์์ ํ์
        const $nav1 = document.querySelectorAll(".nav1");
        // input ํ๊ทธ์ด๋ฉด์ type ์์ฑ์ ๊ฐ์ด text์ธ ๋ชจ๋  ์์ ํ์
        const $input_text = document.querySelectorAll("input[type=text]");
        // ๋ชจ๋  ul ์์์ ํ์์ค์ ๋ชจ๋  li ์์ ํ์
        const $liAll = document.querySelectorAll("ul li");
        // id๊ฐ #nav-container2 ์ฒซ๋ฒ์งธ ์์ ํ์
        const $navContaniner2 = document.querySelector("#nav-container2");
        // $navContaniner2์ ul ํ๊ทธ์์ ์์๋ธ๋์ธ ๋ชจ๋  li ์์ ํ์
        const $li = $navContaniner2.querySelectorAll("ul > li");
        // class ๊ฐ์ด .form ์ฒซ๋ฒ์งธ ์์ ํ์
        const $form = document.querySelector(".form");
        // $form์ ํ์์ค์์ div์ ํ์ ์ธ ๋ธ๋์ค ์ฒซ๋ฒ์งธ span ์์ ํ์
        const $span = $form.querySelectorAll("div + span");
        // $form์ ํ์์ค์์ div์ ํ์ ์ธ ๋ธ๋์ค ๋ชจ๋  span ์์ ํ์
        const $spanAll = $form.querySelectorAll("div ~ span");

        // ๊ฒฐ๊ณผ : NodeList(19)ย [html, head, meta, body, ...]
        console.log($all);
        // ๊ฒฐ๊ณผ : NodeList(4)ย [li.nav1, li.nav2, li.nav3, li.nav4]
        console.log($liTag);
        // ๊ฒฐ๊ณผ : NodeListย [ul#nav-container1]
        console.log($navContaniner1);
        // ๊ฒฐ๊ณผ : NodeListย [li.nav1]
        console.log($nav1);
        // ๊ฒฐ๊ณผ : NodeList(2)ย [input, input]
        console.log($input_text);
        // ๊ฒฐ๊ณผ : NodeList(4)ย [li.nav1, li.nav2, li.nav3, li.nav4]
        console.log($liAll);
        // ๊ฒฐ๊ณผ : NodeList(2)ย [li.nav3, li.nav4]
        console.log($li);
        // ๊ฒฐ๊ณผ : <div class="form>...</div>
        console.log($form);
        // ๊ฒฐ๊ณผ : NodeListย [span.text1]
        console.log($span);
        // ๊ฒฐ๊ณผ : NodeList(2)ย [span.text1, span.text2]
        console.log($spanAll);
    </script>
</html>
```

## ๐ HTMLCollection๊ณผ NodeList์ ์ฐจ์ด์ 

์์๋ฅผ ์ทจ๋ํ๋ ๋ฐฉ๋ฒ์ค์ NodeList๋ก ๋ฐํํ๋ ๋ฉ์๋๋ querySelectorAll ๋ฐ์ ์์ผ๋ฉฐ ์ฐจ์ด์ ์ HTMLCollection์ ์์ ๋ธ๋์ id, name ์์ฑ๊ฐ์ผ๋ก ์ ๊ทผ์ด ๊ฐ๋ฅํ๋ฉฐ Live ๊ฐ์ฒด๋ก ์ฌ์ฉ๋๋ค. ํ์ง๋ง NodeList์ ๋ธ๋๋ ๊ณผ๊ฑฐ์ ์ํ๋ฅผ ์ ์งํ๋ฉฐ Non-Live ๊ฐ์ฒด์ด๋ค. ํ์ง๋ง Node.prototype.childNodes๊ฐ ๋ฐํํ๋ NodeList ๊ฐ์ฒด๋ง์ Live ๊ฐ์ฒด๋ก ์ฌ์ฉ๋๋ค.

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="container">
            <li id="li1" name="nav1">nav1</li>
            <li id="li2" name="nav2">nav2</li>
            <li id="li3" name="nav3">nav3</li>
        </ul>
    </body>
    <script>
        // HTMLCollection์ผ๋ก ๋ถ๋ฌ์ค๊ธฐ
        const $HTML = document.getElementsByTagName("li");
        // NodeList๋ก ๋ถ๋ฌ์ค๊ธฐ
        const $node = document.querySelectorAll("li");
        // ๊ฒฐ๊ณผ : HTMLCollection(3)ย [li#li1, li#li2, li#li3,ย โฆ]
        console.log($HTML);
        // ๊ฒฐ๊ณผ : NodeList(3)ย [li#li1, li#li2, li#li3]
        console.log($node);
        // ๊ฒฐ๊ณผ : <li id="li1" name="nav1">...</li>
        console.log($HTML.nav1);
        // ๊ฒฐ๊ณผ : <li id="li2" name="nav2">...</li>
        console.log($HTML.li2);
        // ๊ฒฐ๊ณผ : ์๋ฌ ์ถ๋ ฅ
        console.log(node.nav1);
    </script>
</html>
```

```HTML
<!DOCTYPE html>
<!--Live ๊ฐ์ฒด ์๋ฏธ ํด์-->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .red {
            color: red;
        }
        .blue {
            color: blue;
        }
    </style>
    <body>
        <ul id="container">
            <li class="red">nav1</li>
            <li class="red">nav2</li>
            <li class="red">nav3</li>
        </ul>
    </body>
    <script>
        const $HTML = document.getElementsByClassName("red");
        // ์ฝ๋๋ฅผ ์ํํ๋ฉด nav2๋ ๋ฐ๋์ง ์๋๋ค. ์ด์ ๋ ์ด์์๋ ๊ฐ์ฒด์ด๊ธฐ ๋๋ฌธ์ด๋ค.
        // ์ด์์๋ ๊ฐ์ฒด๋ ์๋ฃ๊ตฌ์กฐ Stack์์ for๋ฌธ์ ์ฌ์ฉ ๋ชปํ๋ ์ด์ ์ ๊ฐ๋ค. 
        // ๋ฐฐ์ด์ ๊ธธ์ด๊ฐ ๋ณํ๊ธฐ ๋๋ฌธ์ด๋ค.
        for(let i = 0; i < $HTML.length; i++) $HTML[i].className = "blue";
    </script>
</html>
```

**๐ฅ ํด๊ฒฐ๋ฒ์ while๋ฌธ์ ์ฌ์ฉํ๊ฑฐ๋ HTMLCollection์ด ์ดํฐ๋ฌ๋ธ ํ๋กํ ์ฝ์ ์ค์ํ์ฌ ๋ฐฐ์ด๋ก ์นํํ ์ฌ์ฉํ๋ค.**

## ๐ ๋ธ๋ ํ์

### ๐งฉ ์์ ๋ธ๋ ํ์   
**๐ Node.prototype.childNodes (๋ฉ์๋๊ฐ ์๋๋ผ ํ๋กํผํฐ)**   
**๐ Element.prototype.children (๋ฉ์๋๊ฐ ์๋๋ผ ํ๋กํผํฐ)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="animals">
            <li id="dog">Dog</li>
            <li id="cat">Cat</li>
        </ul>
    </body>
    <script>
        const $animals = document.querySelector("#animals");
        // node๋ ํ์คํธ ๋ธ๋๋ ํฌํจ๋๊ธฐ ๋๋ฌธ์ ํ์คํธ ๋ธ๋๋ ํฌํจ๋์ด ์๋ค.
        const $nodeList = $animals.childNodes;
        // Element ํ๋กํผํฐ๋ผ์ ์์ ๋ธ๋๋ง ํฌํจ๋๋ค.
        const $HTMLCollection = $animals.children;
        // ๊ฒฐ๊ณผ : NodeList(5)ย [text, li#dog, text, li#cat, ...]
        console.log($nodeList);
        // ๊ฒฐ๊ณผ : HTMLCollection(2)ย [li#dog, li#cat, ...]
        console.log($HTMLCollection);
    </script>
</html>
```

### ๐งฉ ๋ถ๋ชจ ๋ธ๋ ํ์
**๐ Node.protype.parentNode (๋ฉ์๋๊ฐ ์๋๋ผ ํ๋กํผํฐ)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="animals">
            <li id="dog">Dog</li>
            <li id="cat">Cat</li>
        </ul>
    </body>
    <script>
        const $dog = document.querySelector("#dog");
        const $parent = $dog.parentNode;
        // ๊ฒฐ๊ณผ : <ul id="animals">...</ul>
        console.log($parent);
    </script>
</html>
```

### ๐งฉ ํ์  ๋ธ๋ ํ์   
**๐ Element.prototype.previousElementSibling (๋ฉ์๋๊ฐ ์๋๋ผ ํ๋กํผํฐ)**   
**๐ Element.prototype.nextiousElementSibling (๋ฉ์๋๊ฐ ์๋๋ผ ํ๋กํผํฐ)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="animals">
            <li id="pig">Pig</li>
            <li id="dog">Dog</li>
            <li id="cat">Cat</li>
        </ul>
    </body>
    <script>
        const $dog = document.querySelector("#dog");
        const $Sibling1 = $dog.previousElementSibling;
        const $Sibling2 = $dog.nextElementSibling;
        // ๊ฒฐ๊ณผ : <li id="pig>...</li>
        console.log($Sibling1);
        // ๊ฒฐ๊ณผ : <li id="cat>...</li>
        console.log($Sibling2);
    </script>
</html>
```

## ๐ ์์ ๋ธ๋์ ํ์คํธ ์กฐ์๋ฐฉ๋ฒ (UPDATE)

**๐ HTMLElement.prototpe.innerText (๋ฉ์๋๊ฐ ์๋๋ผ ํ๋กํผํฐ)**   
**๐ Node.prototype.textContent (๋ฉ์๋๊ฐ ์๋๋ผ ํ๋กํผํฐ)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title">Hello
            <span id="sub-title">World!</span>
        </div>
    </body>
    <script>
        const $div = document.querySelector("#title");
        // ๊ฒฐ๊ณผ : HEY๋ก ๋ฌธ์์ด ๋ฐ๋
        $div.textContent = "HEY";
        // ๊ฒฐ๊ณผ : HEY -> Hello๋ก ๋ฐ๋
        $div.innerText = "Hello";
    </script>
</html>
```

**๐ฅ ์ฐจ์ด์ ์ innerText๋ CSS์ ์ข์์ ์ CSS๋ฅผ ๊ณ ๋ คํด์ผํจ์ผ๋ก ์ฑ๋ฅ์ด textContent๋ณด๋ค ๋๋ฆฌ์ง๋ง ๋ง์ ์ฝ๋์์ innerText๋ฅผ ์ฌ์ฉํจ์ผ๋ก ์ฌ์ฉ์ ๋ฌด๋ ๊ฐ๋ฐ์ ํ๋จ์ด๋ผ๊ณ  ์๊ฐํจ**

## ๐ DOM HTML ์กฐ์ (UPDATE)

**๐ Element.prototype.innerHTML (๋ฉ์๋๊ฐ ์๋๋ผ ํ๋กํผํฐ)**   
์ฅ์  : ๊ตฌํ์ด ๊ฐ๋จํ๊ณ  ์ฝ๋๊ฐ ์ง๊ด์ ์ด๋ค.   
๋จ์  : HTML์ ๋ฐ์ดํฐ๋ฅผ ๋ฌธ์์ด๋ก ์ง์  ์๋ ฅํ๊ธฐ ๋๋ฌธ์ XSS์ ์ทจ์ฝํ๋ค. (๋ณด์)   

**๐ฅ ๋๋๋ก์ด๋ฉด ๋ธ๋๋ฅผ ์์ฑํด์ ์์๋ธ๋๋ก ์ถ๊ฐํ์ฌ ์ฌ์ฉ**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title"></div>
    </body>
    <script>
        const $div = document.querySelector("#title");
        // ์์๋ธ๋๋ก ์ถ๊ฐ๋๋ค. ์ง์  ์ฝ๋๋ฅผ ์์ฑํด์ ์ง๊ด์ 
        $div.innerHTML = `<h2>Hello</h2>`
        // ๊ฒฐ๊ณผ <div id="title> <h2>Hello</h2> </div>
        console.log($div);
    </script>
</html>
```

**๐ Element.prototype.insertAdjacentHTML("์ถ๊ฐํ  ์์น", "HTML ์ฝ๋")**   
์ฅ์  : ๊ตฌํ์ด ๊ฐ๋จํ๊ณ  ํ์ ๋ธ๋๋ก๋ ์ถ๊ฐ๊ฐ ๊ฐ๋ฅํ๋ฉฐ ์ฝ๋๊ฐ ์ง๊ด์ ์ด๋ค.   
๋จ์  : HTML์ ๋ฐ์ดํฐ๋ฅผ ๋ฌธ์์ด๋ก ์ง์  ์๋ ฅํ๊ธฐ ๋๋ฌธ์ XSS์ ์ทจ์ฝํ๋ค. (๋ณด์)  

<p align="center">
  <img src="./img/insertAdjacentHTML.PNG" alt="html" width="500px" height="200px"/>
</p>

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title"></div>
    </body>
    <script>
        const $div = document.querySelector("#title");
        // ์์๋ธ๋๋ก ์ถ๊ฐ
        $div.insertAdjacentHTML("afterbegin", `<h2>Title</h2>`);
        // ํ์ ๋ธ๋๋ก ์ถ๊ฐ
        $div.insertAdjacentHTML("afterend", `<div id="subtitle">Subtitle<div>`);
        // body ํ๊ทธ ๊ฒฐ๊ณผํ์ธ
        console.log(document.body);
    </script>
</html>
```

## DOM ์กฐ์ (CREATE, UPDATE, DELETE)

### ๐งฉ ๋ธ๋ ์์ฑ   
**๐ Document.prototype.createElement("์์ฑํ  ํ๊ทธ์ด๋ฆ")**   
**๐ Document.prototype.createTextNode("์์ฑํ  ๋ฌธ์์ด")**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <!--DOM ์กฐ์-->
    </body>
    <script>
        // div ํ๊ทธ ์์ฑ
        const $div = document.createElement("div");
        // ํ์คํธ ๋ธ๋ ์์ฑ
        const $divText = document.createTextNode("Hello");
        // ํ์คํธ ๋ธ๋๋ ๋ฌด์กฐ๊ฑด ์์ ๋ธ๋์ ์์์ด๋ฏ๋ก ์์๋ธ๋๋ก ๋๊ฒจ์ค
        $div.appendChild($divText);
        // body ํ๊ทธ์ ์ง์  ์์์ผ๋ก ์์
        document.body.appendChild($div);
        // ๊ฒฐ๊ณผ : <body>...</body>
        console.log(document.body);

        /* ์์ ์ฝ๋์ ๋์ผํ๊ฒ ๋์ ์ํ๋ ๋ฐฉ๋ฒ์ผ๋ก ์ฌ์ฉํ๋ฉด ๋จ
        const $div = document.createElement("div");
        // $div.textContent = "Hello";
        $div.innerText = "Hello";
        document.body.appendChild($div);
        console.log(document.body);
        */
    </script>
</html>
```

### ๐งฉ ๋ธ๋ ์ฝ์   
**๐ Node.prototype.appendChild(์ถ๊ฐํ  ๋ธ๋)**   
**๐ Node.prototype.insertBefore(์ถ๊ฐํ  ๋ธ๋, ๊ธฐ์ค์  ๋ธ๋)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title"></div>
        <div id="content"></div>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $content = document.querySelector("#content");
        const $span = document.createElement("span");
        $span.innerText = "Top";
        // appendChild๋ ๋ฌด์กฐ๊ฑด ๋ง์ง๋ง ์์๋ธ๋๋ก ์์นํ๊ฒ ๋๋ค.
        $title.appendChild($span);
        const $div = document.createElement("div");
        $div.innerText = "Mid";
        $content.innerText = "Bottom";
        // ๊ธฐ์ค์  ๋ธ๋ ์์ ์์นํ๊ฒ ๋๋ค ๊ธฐ์ค์  ๋ธ๋์ null์ ๋ฃ๋ ๊ฒฝ์ฐ ๋งจ๋ค์ ์ถ๊ฐ.
        // document.body.insertBefore($div, null); 
        document.body.insertBefore($div, $content);
        // ๊ฒฐ๊ณผ : <body>...</body>
        console.log(document.body);
    </script>
</html>
```

### ๐งฉ ๋ธ๋ ๊ต์ฒด   
**๐ Node.prototype.replaceChild(์ถ๊ฐํ  ๋ธ๋, ๊ธฐ์กด ๋ธ๋)**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title">Title</div>
        <div id="content">Content</div>
    </body>
    <script>
        // id๊ฐ content์ธ ์์ ๋ธ๋์ ์ ๊ทผ
        const $content = document.querySelector("#content");
        // div ์์ ๋ธ๋ ์์ฑ
        const $subtitle = document.createElement("div");
        // ํ์คํธ ๋ธ๋๋ฅผ Subtitle๋ก ์์ฑ
        $subtitle.innerText = "Subtitle";
        // ๋ธ๋ ๊ต์ฒด
        document.body.replaceChild($subtitle, $content);
    </script>
</html>
```

### ๐งฉ ๋ธ๋ ์ญ์    
**๐ Element.prototype.remove()**   
**๐ Node.prototype.removeChild(์ญ์ ํ  ์์ ๋ธ๋)**

```HTML
<!DOCTYPE html>
<!-- ์์ ๋ธ๋๋ ๋ผ์ด๋ธ ๊ฐ์ฒด์ด๊ธฐ ๋๋ฌธ์ ๋ฒํผ์ ๋๋ฌ console์์ ํ์ธํ ๋ค์ ๋๋ฅด๊ธฐ  -->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <div id="title">Title</div>
        <div id="content">Content</div> <br />
        <button id="btn" type="button">console.log</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $content = document.querySelector("#content");
        const $btn = document.querySelector("#btn");
        // removeChild๋ฅผ ์ฌ์ฉํ์ฌ ํ์คํธ ๋ธ๋๋ฅผ ์ ๊ฑฐํ๋ ํจ์
        const removeContentText = () => {
            const [ textNode ] = $content.childNodes;
            // ์์์ ์์๋ง ์ญ์ ๊ฐ ๊ฐ๋ฅํ๋ค.
            $content.removeChild(textNode);
            console.log(document.body);
            return;
        }
        // remove๋ฅผ ์ฌ์ฉํ์ฌ ์์ ๋ธ๋์ ์์ ๋ธ๋์ ์์๊น์ง ์ ๊ฑฐ
        const removeTitle = () => {
            // ํด๋น ์์ ๋ธ๋์ ์์ ๋ธ๋๊น์ง ์ ๊ฑฐ
            $title.remove();
            console.log(document.body);
        };
        // ์์ฐจ์ ์ผ๋ก ์คํํ๊ธฐ ์ํด์ ์ ๋๋ ์ดํฐ ์ฌ์ฉ
        const step = function * () {
            yield removeTitle();
            yield removeContentText();
        }();
    
        $btn.addEventListener("click", () => {
            const check = step.next();
            // ์ค๋ฅ ๋ฐฉ์ง
            if(check.done) return;
        });
    </script>
</html>
```

**๐ฅ remove ๋ฉ์๋๋ ์์ ๋ธ๋์ ํด๋น ์์ ๋ธ๋๊น์ง ์ ๊ฑฐ**   
**๐ฅ removeChild ๋ฉ์๋๋ ์์ ๋ธ๋๋ง ์ ๊ฑฐ**

### ๐งฉ ๋ธ๋ ๋ณต์ฌ     
**๐ Node.prototype.cloneNode([ deep : true | false ])**

**โ  ๊ณต์๋ฌธ์๋ฑ์ ํ์ธํ  ๋ ๋ฉ์๋ ์์ ์ธ์๊ฐ์ด [] ์ด๋ฐํํ์์ ์๋๊ฒ์ ํ์๊ฐ ์๋๋ผ๋ ๋ป์ด๋ค.**   
**โก default ๊ฐ์ false ์ด๋ค. ์ธ์์ ์๋ฌด๊ฒ๋ ์์ด ์ฌ์ฉํ๋ฉด ๊ธฐ๋ณธ๊ฐ ์ ์ฉ**   
**โข ๊น์ ๋ณต์ฌ๋ Depth์์ ์๋ ๋ชจ๋  ๊ฐ์ ๋ณต์ฌํ๋ค๋ ์๋ฏธ์ด๋ค.**   
**โฃ ์์๊ฐ๊ณผ ์ฐธ์กฐ๊ฐ์ ์์๋ณต์ฌ, ๊น์๋ณต์ฌ ๊ฐ๋๊ณผ ์ฐธ์กฐ๊ฐ์์์ ์์๋ณต์ฌ ๊น์๋ณต์ฌ ๊ฐ๋์ ๋ค๋ฅด๋ค.**

```JavaScript
// ๊ฐ์ฒด ์์ ํ๋กํผํฐ ๊ฐ์ด ๊ฐ์ฒด๋ฅผ ๊ฐ์ง๊ณ  ์์ ๊ฒฝ์ฐ Depth๋ ํ๋จ๊ณ ์ฌ๋ผ๊ฐ๋ค.
// ๋ชจ๋  ์ฐธ์กฐ๊ฐ์ด ๊ฐ์ ๊ฐ๋ (๋ฐฐ์ด, ๊ฐ์ฒด)
const Object = {
    // 1 Depth
    A: 1,
    B: {
        // 2 Depth
        C: 2,
        D: 2,
        E: {
            // 3 Depth
            F: 3,
            G: 3
        }
    }
}
```

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <!--์์๋ธ๋๋ถํฐ 2 Depth ์์ ํ์คํธ ๋ธ๋๋ ์์๋ธ๋์ ํฌํจ๋๋ค.-->
        <div id="title"> Hello
            <span>World</span>
        </div>
    </body>
    <script>
        const $title = document.querySelector("#title");
        // ์์ ๋ณต์ฌ $title.cloneNode(false)๋ ํํ์ด ๊ฐ๋ค.
        const shallowCopy = $title.cloneNode(); 
        // ๊น์ ๋ณต์ฌ
        const deepCopy = $title.cloneNode(true);
        // ๊ฒฐ๊ณผ : <div id="title"></div> ์์ ๋ธ๋๋ง ๋ณต์ฌ
        console.log(shallowCopy);
        // ๊ฒฐ๊ณผ : <div id="title">...</div> ์์ ์์ ์๋ ์์๋ธ๋๋ ๋ชจ๋ ๋ณต์ฌ
        console.log(deepCopy);
    </script>
</html>
```

## ๐ ์์ ๋ธ๋์ ์์ฑ ๋ธ๋ ์กฐ์๋ฐฉ๋ฒ (CREATE, READ, UPDATE, DELETE)

- ์์ฑ ๋ธ๋์ ๊ฐ ์ ๊ทผ   
**๐ Element.prototype.getAttribute("์์ฑ ๋ธ๋ ์ด๋ฆ")**
- ์์ฑ ๋ธ๋์ ๊ฐ์ ์์   
**๐ Element.prototype.setAttribute("์์ฑ ๋ธ๋ ์ด๋ฆ", "์์ ํ  ๊ฐ")**
- ์์ฑ ๋ธ๋์ ๊ฐ์ ์ญ์    
**๐ Element.prototype.removeAttribute("์์ฑ ๋ธ๋ ์ด๋ฆ")**
- ์์ฑ ๋ธ๋์ ๊ฐ์ด ์กด์ฌํ๋์ง ํ์ธ
**๐ Elemnet.prototype.hasAttribute("์์ฑ ๋ธ๋ ์ด๋ฆ")**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <input id="input" type="text" value="Default"> <br/> <br/>
        <button type="button">console.log</button>
    </body>
    <script>
        const $input = document.querySelector("#input");
        const $btn = document.querySelector("button");
        // ์์ฐจ์ ์ผ๋ก ์คํํ๊ธฐ ์ํด์ ์ ๋๋ ์ดํฐ ์ฌ์ฉ
        const step = function * () {
            // value ์์ฑ ๋ธ๋์ ๊ฐ์ ๊ฐ์ ธ์จ๋ค.
            yield $input.getAttribute("value");
            // value ์์ฑ ๋ธ๋์ ๊ฐ์ ์์ ํ๋ค.
            $input.setAttribute("value", "Change");
            // value ์์ฑ ๋ธ๋์ ๊ฐ์ ๊ฐ์ ธ์จ๋ค
            yield $input.getAttribute("value");
            // value ์์ฑ ๋ธ๋๋ฅผ ์ ๊ฑฐํ๋ค.
            $input.removeAttribute("value");
            // input ์์ ๋ธ๋์ ์์ฑ ๋ธ๋์ value๊ฐ ์๋์ง ํ์ธํ๋ค.
            yield $input.hasAttribute("value");
        }();

        $btn.addEventListener("click", () => {
            const check = step.next();
            // ์ค๋ฅ ๋ฐฉ์ง
            if(check.done) return;
            else console.log(check.value);
        });
    </script>
</html>
```

## ๐ HTML ์์ฑ๊ณผ DOM์ ํ๋กํผํฐ

HTML ์์ฑ์ ์ด๊ธฐ์ ์์ฑ ๋ธ๋์ ๊ฐ์ ๋์ํ๋ค. ์ฒ์์ HTML ํ๊ทธ์์ ์ ์ ์์ฑ๊ฐ์ ๊ฐ์ง๊ณ  ์๋ค. ์ด๊ธฐ๊ฐ์ ์ ๊ทผ ํ๋ ๋ฐฉ๋ฒ์ getAttribute() ๋ฉ์๋๋ฅผ ์ด์ฉํด์ ๊ฐ์ ์ ๊ทผํ๊ฑฐ๋ setAttribute()๋ก ์ด๊ธฐ๊ฐ์ ์์ ํ๋ ๋ฐฉ๋ฒ์ด ์๋ค.

DOM์ ํ๋กํผํฐ๋ ์ฌ์ฉ์๊ฐ ์ธํฐํ์ด์ค๋ฅผ ์ด์ฉํด์ ๋ฐ๊พผ ์ต์ ์ํ์ ๊ฐ์ ๊ฐ์ง๊ณ  ์๋ค.

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <input id="input" type="text" value="Default"> <br/> <br/>
        <button id="default" type="button">Default</button>
        <button id="change" type="button">Change</button>
    </body>
    <script>
        const $input = document.querySelector("#input");
        const $default = document.querySelector("#default");
        const $change = document.querySelector("#change");
        // HTML์ ์์ฑ์ผ๋ก ์ ๊ทผ
        $default.addEventListener("click", () => {
            // input์ ๋ณ๊ฒฝํด๋ HTML ํ๊ทธ ์์ ์๋ ์ด๊ธฐ๊ฐ์ ๊ฐ์ง๊ณ  ์๋ค.
            console.log($input.getAttribute("value"));
        });
        //DOM ํ๋กํผํฐ๋ก ์ ๊ทผ
        $change.addEventListener("click", () => {
            // ํ์ฌ ์ต์ ๊ฐ์ผ๋ก ๋ณ๊ฒฝ๋๋ค.
            console.log($input.value);
        });
    </script>
</html>
```
**๐ฅ DOM์ ํ๋กํผํฐ๋ก ์ ๊ทผํ๋ ๋ฐฉ๋ฒ์ ์ง์  ์์ ๋ธ๋์ ์์ฑ ๋ธ๋์ ์ด๋ฆ์ ๊ฐ์ฒด ํ๋กํผํฐ๋ก ์ ๊ทผํ๋ค.**   
**๐ฅ HTML์ ์์ฑ์ผ๋ก ์ ๊ทผํ๋ ๋ฐฉ๋ฒ์ ๋ฉ์๋๋ฅผ ์ด์ฉํด ์ ๊ทผํ๋ค.**

## ๐ ์์ ๋ธ๋์ data ์ด์ฉ

**์์ฑ ๋ฐฉ๋ฒ : ํด๋น ์์ ๋ธ๋์ ์์ฑ ๋ธ๋๋ฅผ ์ถ๊ฐ ํ์์ data-string ํํ**   
**์ ๊ทผ ๋ฐฉ๋ฒ : ํด๋น ์์ ๋ธ๋์ ์ ๊ทผํ์ฌ ๊ฐ์ฒด ํ๋กํผํฐ(dataset)๋ก ์ ๊ทผ ์นด๋ฉํ๊ธฐ๋ฒ ์ค์**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="list">
            <!-- ์์ฑ -->
            <li data-animals-index="0">Cat</li>
        </ul>
    </body>
    <script>
        const $li = document.querySelector("li");
        // ์ ๊ทผ ๋ฐฉ๋ฒ ๊ฒฐ๊ณผ : "0";
        console.log($li.dataset.animalsIndex);
    </script>
</html>
```

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <ul id="list">
            <li data-animals-index="0">Cat</li>
            <li>Dog</li>
        </ul>
    </body>
    <script>
        const $li = document.querySelectorAll("li");
        const [$cat, $dog] = $li;
        // ์ด๋ฐ์์ผ๋ก ์ ๊ทผ๋ ๊ฐ๋ฅํ๋ค.
        $dog.setAttribute("data-animals-index", "1");
        // ๊ฒฐ๊ณผ : "1"
        console.log($dog.dataset.animalsIndex);
    </script>
</html>
```

**๐ฅ ๋ณดํต์ฌ์ฉ ๋ฐฉ๋ฒ์ ํด๋น ์์ ๋ธ๋์ ์ธ๋ฑ์ค๋ฅผ ์ ๊ณตํ์ฌ ์ด๋ฒคํธ ์์์ ์ฌ์ฉํ์ฌ ํด๋น ์์ ๋ธ๋๋ฅผ ์ฒดํฌํ๊ณ  CRUD์ ์ด์ฉํ๋ค.**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <body>
        <input id="input" type="text"> <br/> <br/> 
        <button id="add">์ถ๊ฐ</button> <br/>
        <ul id="list">

        </ul>
    </body>
    <script>
        // ๋๋ฌผ์ ์ด๋ฆ์ ์๋ ฅ ๋ฐ์ ์ ์ฅํ  ๋ฐฐ์ด ์ ์ธ
        const animals = [];
        // input์ ๋๋ฌผ์ ์ด๋ฆ์ ์ ์กํ๊ธฐ ์ํด ๋ฒํผ ์์ ์ ๊ทผ
        const $addbtn = document.querySelector("#add");
        // ์ด๋ฒคํธ ์์์ ์ํด์ id๊ฐ list์ธ ์์์ ์ ๊ทผ
        const $list = document.querySelector("#list");
        // ํ์ด์ง๋ฅผ ๊ณ์ ๊ณ ์ณ์ค ํจ์ ์์ฑ
        const render = () => {
            // animals์ ์ด๋ฆ์ ๋ฐ์์ HTML์์๋ก ๋ฐ๊พธ๊ธฐ
            const makeHTML = animals.map((item, index) => {
                // index๋ฅผ ๋ฐ์์ data์ index๋ก ์ฌ์ฉํ๊ธฐ ์ํด ์ง์ 
                return `<div data-animals-index=${index} style="display: flex">
                    <li>${item}</li>
                    <button id="update" style="margin-left: 10px">์์ </button>
                    <button id="remove" style="margin-left: 10px">์ญ์ </button>
                </div>`
            });
            // ํด๋น ๋ฐฐ์ด ๋ด์ฉ์ ๋ฌธ์์ด๋ก ์นํํ HTML ์กฐ์
            $list.innerHTML = makeHTML.join('');
        }
        $addbtn.addEventListener("click", () => {
            // input ์์์ ์ ๊ทผ
            const $input = document.querySelector("#input");
            // animals ๋ฐฐ์ด์ ํด๋น ๋๋ฌผ์ ์ ์ฅ
            animals.push($input.value);
            // input ์ด๊ธฐํ
            $input.value = null;
            // ํ์ด์ง ์์ 
            render();
        });
        // ์ด๋ฒคํธ ์์
        $list.addEventListener("click", (e) => {
            // ํด๋น ๋๋ฌผ์ ์ธ๋ฑ์ค ๋ฒํธ๋ฅผ ์ด๋ฒคํธ๋ฅผ ์์ํด๋ผ ์์์ dataset์ ์ ๊ทผ 
            const index = e.target.closest("div").dataset.animalsIndex;
            // ํด๋ฆญํ ์์๊ฐ id๊ฐ update ๋ฒํผ์ธ์ง ํ์ธ
            if(e.target.id === "update") {
                // ์์ ๋ฐ๋ ๊ฐ์ ๋ณ์์ ์ ์ฅ
                const updateText = prompt("์์ ํ  ๋๋ฌผ์ ์ด๋ฆ์ ์๋ ฅํ์ธ์.");
                // ํด๋น ๋ฐฐ์ด์ธ๋ฑ์ค์ ์ ๊ทผํ์ฌ  ๊ฐ ์์ 
                animals[index] = updateText;
                // ํ์ด์ง ์์ 
                render();
            // ํด๋ฆญํ ์์๊ฐ id๊ฐ remove ๋ฒํผ์ธ์ง ํ์ธ
            } else if(e.target.id === 'remove') {
                // ํด๋น ๋ฐฐ์ด์์ ์์ ์ญ์ 
                animals.splice(index, 1);
                // ํ์ด์ง ์์ 
                render();
            }
        });
    </script>
</html>
```
**๐ฅ Element.prototype.closest("ํด๋น ํ๊ทธ")๋ ์ฒ์์ผ๋ก ๋ง๋ ํด๋น ํ๊ทธ์ ๋ถ๋ชจ๋ธ๋๋ฅผ ๋ฐํํ๋ค.**   
**๐ฅ ์ด๋ฒคํธ ์์๊ณผ e.target์ ์ด๋ฒคํธ ๋ถ๋ถ์์ ํ์ธํ๊ธฐ**

```HTML
<!DOCTYPE html>
<!-- innerHTML XSS ๋จ์ ์ผ๋ก ๋ธ๋์ ์์์ ์ด์ฉํด์ ๋ง๋  ์ฝ๋ -->
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .form {
            display: flex;
        }
        .blank {
            margin-left: 10px;
        }
    </style>
    <body>
        <input id="input" type="text"> <br/> <br/> 
        <button id="add">์ถ๊ฐ</button> <br/>
        <ul id="list">

        </ul>
    </body>
    <script>
        const animals = [];
        const $addbtn = document.querySelector("#add");
        const $list = document.querySelector("#list");
        // ๋ธ๋์ ์์๋ค์ ๋ชจ๋ ์ง์์ฃผ๊ธฐ ์ํด์ reset ํจ์ ์์ฑ
        const reset = () => {
            // childeNodes๋ ๋ผ์ด๋ธ๊ฐ์ฒด์ด๋ฏ๋ก ๋ฐฐ์ด๋ก ๋ฐ๊ฟ์ ์ฌ์ฉ
            const child = [...$list.childNodes];
            // ํด๋น ์์ ์์ ๋ธ๋ ์ ๋ถ ์ญ์ 
            child.forEach((item) => item.remove());
        }
        // ํ์ด์ง๋ฅผ ์๋ก ๊ณ ์ณ์ค ํจ์
        const render = () => {
            // ํ์ด์ง๋ฅผ ๊ณ ์น๊ธฐ ์ ์ resetํจ์ ์คํ
            reset();
            // ์๋ฏธ์๋ ํ๊ทธ์ธ div๋ฅผ ํ๋ฒ๋ ์์ฑํ์ง ์๊ธฐ ์ํด ์์ฑ
            const $container = document.createDocumentFragment();
            // ํด๋น ๋ฐฐ์ด์ ์์๋ง๋ค ์คํํ  ์ฝ๋
            animals.forEach((item, index) => {
                // ๋ธ๋ ์์ฑ ํ๊ณ  ์์ฑ ์์ฑ ํด๋์ค์ด๋ฆ ์์ฑ์ผ๋ก CSS ์ ์ฉ
                const $div = document.createElement("div");
                const $li = document.createElement("li");
                const $updateBtn = document.createElement("button");
                const $removeBtn = document.createElement("button");
                $updateBtn.id = "update";
                $updateBtn.className = "blank";
                $updateBtn.innerText = "์์ ";
                $removeBtn.id = "remove";
                $removeBtn.className = "blank";
                $removeBtn.innerText = "์ญ์ ";
                $li.innerText = item;
                $div.className = "form";
                $div.setAttribute("data-animals-index", index);
                // ์์ ์ฝ๋
                $div.appendChild($li);
                $div.appendChild($updateBtn);
                $div.appendChild($removeBtn);
                $container.appendChild($div);
            });
            // ul ํ๊ทธ์ ์ถ๊ฐ
            $list.appendChild($container);
        }
        $addbtn.addEventListener("click", () => {
            const $input = document.querySelector("#input");
            animals.push($input.value);
            $input.value = null;
            render();
        });
        $list.addEventListener("click", (e) => {
            const index = e.target.closest("div").dataset.animalsIndex;
            if(e.target.id === "update") {
                const updateText = prompt("์์ ํ  ๋๋ฌผ์ ์ด๋ฆ์ ์๋ ฅํ์ธ์.");
                animals[index] = updateText;
                render();
            } else if(e.target.id === 'remove') {
                animals.splice(index, 1);
                render();
            }
        });
    </script>
</html>
```

## ๐ ์์ ๋ธ๋์ Class ์กฐ์

**๐ฅ class ์์ฑ ๋ธ๋๋ฅผ ์กฐ์ํ๋ ์ด์ ๋ CSS ๋๋ฌธ์ด๋ค. ๋ฉ์๋๋ฅผ ์ด์ฉํด์ ์ด๋ฒคํธ์์์ ํ  ๋๋ ์ฌ์ฉํ๋ค.**   
**๐ฅ DOM์ ์ ๊ทผํ  ๋ className, ClassList์ธ ์ด์ ๋ JS์์ Class๋ ์์ฝ์ด์ด๊ธฐ ๋๋ฌธ์ด๋ค.**

className๊ณผ classList๋ ๋ค๋ฅธ์ ์ด ์๋ค. className์ ๋ฌธ์์ด์ ๋ฐํํ๋ ํ๋กํผํฐ๋ก className์ ์ด์ฉํด์ className์ ๋ฐ๊ฟ์ ์๋ค๋ฉด classList๋ ์ธ๋ถ์ ์ธ ๋ฉ์๋๋ฅผ ์ ๊ณตํ๋ค.

### ๐งฉ ํด๋์ค ์ถ๊ฐ   
**๐ Element.prototype.classList.add("ํด๋์ค ์ด๋ฆ")**
```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
    </style>
    <body>
        <span id="title" class="bold">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // ๋ฒํผ์ ๋๋ฅด๋ฉด class์ red ์ถ๊ฐ
        $btn.addEventListener("click", () => {
            $title.classList.add("red");
            // ๊ฒฐ๊ณผ : bold red
            console.log($title.className);
        });
    </script>
</html>
```
**๐ฅ class๋ ์ด๋ฆ์ ๊ณต๋ฐฑ์ ๊ธฐ์ค์ผ๋ก CSS๋ฅผ ๋ฃ๋๋ค. ๋ํ CSS๊ฐ ๊ฒน์น๋ฉด class ์ด๋ฆ์ ๋ง์ง๋ง CSS๋ฅผ ์ฐธ์กฐํ๋ค.**
```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
        .blue {
            color: blue;
        }
    </style>
    <body>
        <span id="title" class="bold">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // ๋ฒํผ์ ๋๋ฅด๋ฉด class์ red blue ์ถ๊ฐ
        $btn.addEventListener("click", () => {
            $title.classList.add("red")
            $title.classList.add("blue");
            // ๊ฒฐ๊ณผ : bold red blue 
            // (ํด๋น ํ์คํธ ์๊น์ ํ๋์ ์๋๋ฉด red๋ณด๋ค blue๊ฐ ์ด๋ฆ์ด ๋ค์์์)
            console.log($title.className);
        });
    </script>
</html>
```
### ๐งฉ ํด๋์ค ์ญ์    
**๐ Element.prototype.classList.remove("ํด๋์ค ์ด๋ฆ")**

```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
    </style>
    <body>
        <span id="title" class="bold red">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // ๋ฒํผ์ ๋๋ฅด๋ฉด class์ red ์ญ์         
        $btn.addEventListener("click", () => {
            $title.classList.remove("red")
            // ๊ฒฐ๊ณผ : bold
            console.log($title.className);
        });
    </script>
</html>
```

### ๐งฉ ํด๋์ค ํ์ธ   
**๐ Element.prototype.classList.contains("ํด๋์ค ์ด๋ฆ")**
```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
    </style>
    <body>
        <span id="title" class="bold red">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // ๋ฒํผ์ ๋๋ฅด๋ฉด class์ ์์๊ฐ ํฌํจ๋๋์ง ํ์ธ
        $btn.addEventListener("click", () => {
            // ๊ฒฐ๊ณผ : true
            console.log($title.classList.contains("red"));
            // ๊ฒฐ๊ณผ : false
            console.log($title.classList.contains("blue"));
            // ๊ฒฐ๊ณผ : true
            console.log($title.classList.contains("bold"));
        });
    </script>
</html>
```

### ๐งฉ ํด๋์ค ๋ณ๊ฒฝ   
**๐ Element.prototype.classList.replace("๊ธฐ์กด ํด๋์ค ์ด๋ฆ", "๋ณ๊ฒฝํ  ํด๋์ค ์ด๋ฆ")**
```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
        .blue {
            color: blue;
        }
    </style>
    <body>
        <span id="title" class="bold red">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // ๋ฒํผ์ ๋๋ฅด๋ฉด class์ red๋ฅผ blue๋ก ๋ณ๊ฒฝ
        $btn.addEventListener("click", () => {
            $title.classList.replace("red", "blue");
            // ๊ฒฐ๊ณผ : bold blue
            console.log($title.className);
        });
    </script>
</html>
```

### ๐งฉ ํด๋์ค ์ถ์ถ   
**Element.prototype.classList.item(ํด๋น ์ธ๋ฑ์ค)**
```HTML
<!DOCTYPE html>
<html lang="kr">
    <head>
        <meta charset="UTF-8">
    </head>
    <style>
        .bold {
            font-weight: bold;
        }
        .red {
            color: red;
        }
        .blue {
            color: blue;
        }
    </style>
    <body>
        <span id="title" class="bold red">Hello</span>
        <button id="btn" type="button">add</button>
    </body>
    <script>
        const $title = document.querySelector("#title");
        const $btn = document.querySelector("#btn");
        // ๋ฒํผ์ ๋๋ฅด๋ฉด classList์ ์์ ์ถ์ถ
        $btn.addEventListener("click", () => {
            // ๊ฒฐ๊ณผ : bold
            console.log($title.classList.item(0));
            // ๊ฒฐ๊ณผ : red
            console.log($title.classList.item(1));
            // ๋ฐฐ์ด์ฒ๋ผ ์ ๊ทผํด์ ๊ฐ์ ๋ฐ๊พธ๋๊ฑด ๋ถ๊ฐ๋ฅ add, replace ๋ฑ๋ฑ ๋ฉ์๋๋ฅผ ์ฌ์ฉ
            try {
                $title.classList.item(1) = "blue";
            } catch {
                console.log("error");
            }
        });
    </script>
</html>
```

**๐ฅ ํด๋์ค ์ด๋ฆ์ ์์๋ฅผ ์ถ์ถ ์ฆ ์์์ ๊ฐ์ ์ป์ ๋์ ์ธ๋ฑ์ค ์ฒ๋ผ ์ฌ์ฉํ๋ ๋ฒํธ๋ String.split(" ")์ ํด์ ๋ฌธ์์ด๋ก ๋ฐํํ๊ฑฐ๋ ๊ฐ๋ค๊ณ  ๋ณด๋ฉด๋๋ค.**
