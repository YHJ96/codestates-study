# useState

## π useStateλ?
- μνλ₯Ό κ΄λ¦¬νλ Hookμ΄λ€.
- useStateλ λ°°μ΄μ λ°ννκΈ° λλ¬Έμ κ΅¬μ‘° λΆν΄ ν λΉμΌλ‘ μ¬μ©νλ€.
- μ²« λ²μ§Έ μμλ μνμ΄λ©° λ λ²μ§Έ μμλ μνλ₯Ό λ³νμν€λ ν¨μλ₯Ό λ°ννκ³  μλ€.
- μνκ° λ³ννλ©΄ νλ©΄μ΄ λ€μ λλλ§ λλ€.
- setState ν¨μλ λ£μ΄μ€ κ²½μ° λΉλκΈ°μ μΌλ‘ μλν  μ μλ€.

[React κ³΅μλ¬Έμ](https://ko.reactjs.org/docs/faq-state.html#gatsby-focus-wrapper)

## π useState κΈ°λ³Έ νν

- const [μν, μν λ³ν ν¨μ] = useState("κΈ°λ³Έκ°")

```javascript
import React, { useState } from 'react';

function App() {
    // λ³΄ν΅ μν λ³ν ν¨μλ μ λμ¬ setμ λΆνμ μλλ₯Ό μ ννκ² νλ€.
    const [num, setNum] = useState(0);
    // μνλ₯Ό λ³νμν€λ μ΄λ²€νΈ
    const handleOnClick = () => setNum(num + 1);
    return (
        <div>
        {/* νμ¬ κΈ°λ³Έκ°μ 0μ΄λ€ */}
        <div>{num}</div>
        <button onClick={handleOnClick}>+1</button>
        </div>
    );
}

export default App;
```

## π μν λ³ν ν¨μμ 2κ°μ§ νν (setState)

### π§© μν λ³ν ν¨μμ κ°μ λ£μ΄μ€ κ²½μ°

- κ°μ λ£μ΄μ€ κ²½μ° λ§μ§λ§μΌλ‘ μ€νλ κ°μΌλ‘ λ³κ²½νλ€.
- λΆνμν λλλ§μ λ§κΈ° μν΄μ λ§μ§λ§ setStateλ§ μ²λ¦¬νλ€.

```javascript
import React, { useState } from 'react';

function App() {
    const [num, setNum] = useState(0);
    const handleOnClick = () => {
        // μμ μ€ν 0 + 1
        setNum(num + 1);
        // μμ μ€ν 1 + 2
        setNum(num + 2);
        // μμ μ€ν 3 + 3
        setNum(num + 3);
    }
    return (
        <div>
        {/* κ²°κ³Ό : 3 */}
        <div>{num}</div>
        <button onClick={handleOnClick}>+1</button>
        </div>
    );
}

export default App;
```

### π§© μν λ³ν ν¨μμ ν¨μλ₯Ό λ£μ΄μ€ κ²½μ°

- μ°μ°μ κ²°κ³Όλ₯Ό λ€ μ²λ¦¬ν΄μ€λ€.
- μ½λ°±ν¨μμ μΈμλ λ°λ‘ μ§μ μ state κ°μ΄λ€.
- μ½λ°±ν¨μμ return κ°μ΄ stateμ λ°μλλ€.

[React κ³΅μ λ¬Έμ](https://ko.reactjs.org/docs/hooks-reference.html#usestate)

```javascript
import React, { useState } from 'react';

function App() {
    const [num, setNum] = useState(0);
    const handleOnClick = () => {
        // μμ μ€ν 0 + 1
        setNum((prevState) => prevState + 1);
        // μμ μ€ν 1 + 2
        setNum((prevState) => prevState + 2);
        // μμ μ€ν 3 + 3
        setNum((preState) => preState + 3);
    }
    return (
        <div>
        {/* κ²°κ³Ό : 6 */}
        <div>{num}</div>
        <button onClick={handleOnClick}>+1</button>
        </div>
    );
}

export default App;
```