# useEffect

## ๐ useEffect๋?
- ์ปดํฌ๋ํธ๊ฐ ๋๋๋ง ๋  ๋๋ง๋ค ํน์  ์์์ ์ํํ๋๋ก ํ  ์ ์๋ Hook์ด๋ค.
- componentDidMount์ componentDidUpdate๋ฅผ ํฉ์น ํํ์ด๋ฉฐ return ๊ฐ์ผ๋ก ํจ์๋ฅผ ๋๊ฒจ์ฃผ๋ฉด componentDidUnMount๋ก ์๋ํ๋ค.
- useEffect์ ์ธ์๋ 2๊ฐ๋ก ์ฒซ ๋ฒ์งธ ์ธ์๋ ์ฝ๋ฐฑํจ์๋ฅผ ๋ฐ์ผ๋ฉฐ ๋ ๋ฒ์งธ ์ธ์๋ ๋ฐฐ์ด์ ์๋ ฅ๋ฐ๋๋ค.

## ๐ ์ฝ๋ฐฑํจ์๋ง ์ธ์๋ก ์ฌ์ฉํ  ๋
๋๋๋ง์ด ๋๋ฉด useEffect ํจ์ ์คํ

```javascript
import React, { useEffect, useState } from 'react';

const App = () => {
    const [isChecked, setIsChecked] = useState(false);
    // ์ฒ์ ํ๋ฉด์ ๋ง์ดํธ ๋์์ ๋ ์คํ๋๊ณ  ๊ทธ ์ดํ์๋ ํ๋ฉด์ด ์ฌ๋๋๋ง ๋๋ฉด ํจ์ ์คํ
    useEffect(() => {
        /*
        ๊ฒฐ๊ณผ : render
        ๊ทธ ๋ค์ ๋ฒํผ์ ๋๋ฅด๋ฉด ๊ณ์ ๊ฒฐ๊ณผ๋ render์ด๋ค.
        */
        console.log("render");
    });
    // ์ฌ๋๋๋ง์ ์ํ ์ด๋ฒคํธ ํธ๋ค๋ฌ ์์ฑ
    const handleOnClick = () => setIsChecked(!isChecked);
    // ๋ฒํผ์ ๋๋ฅด๋ฉด ํ๋ฉด ์ฌ๋๋๋ง
    return <button onClick={handleOnClick}>Click</button>
}

export default App;
```

## ๐ ์ฝ๋ฐฑํจ์์ ๋ฐฐ์ด ๋ชจ๋ ์ธ์๋ก ์ฌ์ฉํ  ๋
- ๋น ๋ฐฐ์ด์ ์ธ์๋ก ์ค ๊ฒฝ์ฐ ํ๋ฉด์ด ์ต์ด๋ก ๋๋๋ง ๋์์ ๋๋ง ํธ์ถ๋๋ค.
- ๋ฐฐ์ด์ ์ธ์์ state๋ฅผ ๋ฃ์ด์ค ๊ฒฝ์ฐ ํด๋น state์ ์ํ๊ฐ ๋ณํ  ๊ฒฝ์ฐ๋ง ํจ์๊ฐ ํธ์ถ๋๋ค.

### ๐งฉ ๋น ๋ฐฐ์ด์ ์ธ์๋ก ์ฌ์ฉํ  ๋

```javascript
import React, { useEffect, useState } from 'react';

const App = () => {
    const [isChecked, setIsChecked] = useState(false);
    // ๋ ๋ฒ์งธ ์ธ์๋ก ๋น ๋ฐฐ์ด์ ์๋ ฅ
    useEffect(() => {
        // ์ฒซ ๋๋๋ง์ธ ๊ฒฝ์ฐ์๋ง ์คํ
        console.log("render");
    }, []);
    const handleOnClick = () => setIsChecked(!isChecked);
    // ๋ฒํผ์ ํด๋ฆญํด๋ ์ฝ์์ฐฝ์ render๊ฐ ํธ์ถ๋์ง ์์
    return <button onClick={handleOnClick}>Click</button>
}

export default App;
```

### ๐งฉ ๋ฐฐ์ด์ state์ ๋ฃ์ด์ค ๋

```javascript
import React, { useEffect, useState } from 'react';

const App = () => {
    const [isChecked, setIsChecked] = useState(false);
    const [num, setNum] = useState(0);
    // ๋ ๋ฒ์งธ ์ธ์์ ๊ฐ์ state์ธ num์ ์๋ ฅ
    useEffect(() => {
        // ์ฒซ ๋๋๋ง์ธ ๊ฒฝ์ฐ์ num์ด ๋ณ๊ฒฝ๋  ๋๋ง ์คํ
        console.log("render");
    }, [num]);
    // num + 1์ ํด์ฃผ๋ ์ด๋ฒคํธ ํธ๋ค๋ฌ
    const updateNum = () => setNum(num + 1);
    // isChecked๋ฅผ ๋ณ๊ฒฝํด์ฃผ๋ ์ด๋ฒคํธ ํธ๋ค๋ฌ
    const updateIsChecked = () => setIsChecked(!isChecked);
    
    return <div>
        <div>
            <span>{num}</span>
            <button onClick={updateNum}>numUpdate</button>
        </div>
        <button onClick={updateIsChecked}>isCheckedUpdate</button>
    </div>
}

export default App;
```

## ๐ ํจ์๋ฅผ return ๊ฐ์ ๋ฃ์์ ๋

```javascript
import React, { useEffect, useState } from 'react';

const App = () => {
    const [isChecked, setIsChecked] = useState(false);
    const updateIsChecked = () => setIsChecked(!isChecked);
    return <div>
        {/* isChecked์ ์ปดํฌ๋ํธ๋ฅผ ๋๋๋ง */}
        {isChecked ? null : <Log/>}
        <button onClick={updateIsChecked}>isCheckedUpdate</button>
    </div>
}

const Log = () => {
    // ์ปดํฌ๋ํธ๋ฅผ ์ฌ์ฉํ์ง ์์ ๊ฒฝ์ฐ return ๊ฐ์ผ๋ก ๋ฐํํ๋ ํจ์ ์คํ
    useEffect(() => {
        return () => {
            // ์ปดํฌ๋ํธ๊ฐ ์ธ๋ง์ดํธ ๋  ๋๋ง๋ค ์คํ
            console.log("Log");
        }
    })
    return <span>Log</span>
}

export default App;
```