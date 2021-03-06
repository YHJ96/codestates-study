# redux

## ๐ redux๋?

์ ์ฅ์์์ ๋ฐ์ดํฐ๋ฅผ ์ฝ๊ณ  ์ ์ฅ์์ ์์์ ์ ๋ฌํ์ฌ ์ํ๋ฅผ ์๋ฐ์ดํธ ํ  ์ ์๊ฒ ํด์ฃผ๋ ๋ผ์ด๋ธ๋ฌ๋ฆฌ์ด๋ค. (์ ์ญ ์ํ๊ด๋ฆฌ๋ฅผ ์ํ ๋ผ์ด๋ธ๋ฌ๋ฆฌ)

## ๐ redux์ 3์์น

- Single source of truth : ํ๋์ ์คํ ์ด๋ฅผ ๊ฐ์ง๊ณ  ์์ด์ผํ๋ค.
- State is read-only : ์ฝ๊ธฐ ์ ์ฉ์ด๊ธฐ ๋๋ฌธ์ ์ํ๋ฅผ ์ง์  ๋ณ๊ฒฝ์ํค๋ฉด ์๋๋ค. (action)
- Changes are made with pure functions : ์ํ์ ๋ณ๊ฒฝ์ ์์ํจ์๋ก๋ง ๋ณ๊ฒฝ์ด ๊ฐ๋ฅํ๋ค. (reducer)

## ๐ redux์ ๊ตฌ์ฑ์์

<p align="center">
<img src="../img/redux-flow.png" width="500px" height="350px">
</p>

### ๐งฉ action
`type`ํ๋กํผํฐ๋ฅผ ํ์์ ์ผ๋ก ๊ฐ์ง๊ณ  ์์ด์ผํ๋ฉฐ ์ํ๋ฅผ ๋ฐ๊พธ๋ ์ ๋ณด๋ฅผ ๋ด๊ณ ์๋ ๊ฐ์ฒด์ด๋ค.

```javascript
// action
const addCounter = () => {
    return { type: "ADD_COUNTER" }
}
```

### ๐งฉ reducer 
- ์ํ๋ฅผ ์ง์  ๋ณ๊ฒฝ์ํค๋ ํจ์์ด๋ฉฐ ์ก์์ ์ ๋ณด๋ฅผ ๋ฐ์ ์๋ก์ด ์ํ๋ฅผ ๋ฐํํ๋ค.
- reducer์ ์ฒซ ๋ฒ์งธ ์์๋ state๋ฅผ ๋ด๊ณ  ์์ผ๋ฉฐ ๋ ๋ฒ์งธ ์์๋ action ๊ฐ์ฒด๋ฅผ ๊ฐ์ง๊ณ  ์๋ค.
- state์ default ๊ฐ์ ์ค์ ํด์ผ ํ๋ค.

```javascript
// reducer
const counterReducer = (state = 0, action) => {
    const { type = '', payload = 0 } = action;
    switch (type) {
        case ADD_COUNTER:
        return state + 1;
        case MINUS_COUNTER:
        return state - 1;
        case CHANGE_COUNTER:
        return payload;
        default:
        return state;
    }
};
```

### ๐งฉ store
์ํ์ ๋ฆฌ๋์๊ฐ ๋ค์ด๊ฐ์๋ค. (์ ์ฅ์)

```javascript
// store
import { createStore } from 'redux'
import { counterReducer } from './store/index';

const store = createStore(counterReducer);
```

### ๐งฉ subscribe 
- ์คํ ์ด์์ ์ํ๋ฅผ ๊ฐ์ ธ์ค๋ ํจ์์ด๋ค. (๊ตฌ๋)
- ํจ์ํ ์ปดํฌ๋ํธ์์๋ useSelector๋ฅผ ์ฌ์ฉํ๋ค.
- useSelector์ ์ฒซ ๋ฒ์งธ ์์๋ ์คํ ์ด์ state๋ฅผ ๊ฐ์ ธ์จ๋ค.

```javascript
// subscribe
import React from "react";
import { useSelector } from 'react-redux';

function App() {
    // useSelector์ ์ฒซ ๋ฒ์งธ ์์๋ ์คํ ์ด์ state๋ฅผ ๊ฐ์ ธ์จ๋ค.
    const counter = useSelector((state) => state);

    return (
        <React.Fragment>
            <span>{counter}</span>
        </React.Fragment>
    );
}

export default App;
```

### ๐งฉ dispatch
- ์ก์์ ๋ฐ์์ํค๋ ํจ์์ด๋ค.
- ํจ์ํ ์ปดํฌ๋ํธ์์๋ useDispatch๋ฅผ ์ฌ์ฉํ๋ค.
- useDispatch๋ ํจ์๋ฅผ ๋ฐํํ๋ฉฐ ๊ทธ ๋ฐํํ ํจ์์ ๊ฐ์ฒด๋ฅผ ๋ฃ์ด์ค๋ค.

```javascript
// dispatch
import React from "react";
import { useSelector, useDispatch } from 'react-redux';

function App() {
    const counter = useSelector((state) => state);
    const dispatch = useDispatch();
    // action ํจ์
    const addCounter = () => {
        return { type: "ADD_COUNTER" }
    }
    // dispatch์ ์ก์ ๊ฐ์ฒด ๋๊ฒจ์ฃผ๋ฉด ์ก์์ ๋ฐ์์ํจ๋ค
    const handleOnClick = () => {
        dispatch(addCounter());
    }

    return (
        <React.Fragment>
            <span>{counter}</span>
            <button onClick={handleOnClick}>+1</button>
        </React.Fragment>
    );
}

export default App;
```

## ๐ store๋ฅผ ๋๋ ์ ๊ด๋ฆฌํ๊ธฐ

- reducer๋ฅผ ๊ฐ์ ๊ด๋ฆฌํ  ์ ์์ด์ ๊ฐ๋์ฑ๊ณผ ์ ์ง๋ณด์์ฑ์ด ์ข์์ง๋ค.
- combineReducers ๋ฉ์๋๋ฅผ ์ฌ์ฉํ๋ค.

```javascript
import { createStore, combineReducers } from 'redux';
import { counterReducer, counterAction } from './counterReducer';
import { listReducer, listAction } from './listReducer';
// combineReducers ๋ฉ์๋์ ๊ฐ์ฒด๋ฅผ ํ๋ผ๋ฏธํฐ๋ก ๋ฃ์ด์ค๋ค.
const root = combineReducers({
    counter: counterReducer,
    list: listReducer
});
// combineReducers๋ฅผ ๋จ์ผ ์คํ ์ด๋ก ์์ฑํ๋ค.
const store = createStore(root);

export { store, counterAction, listAction };
```

### ๐งฉ ์ฐ๊ฒฐ๋ store๋ฅผ ์ฌ์ฉํ๋ ๋ฐฉ๋ฒ

```javascript
import React from "react";
import { useSelector, useDispatch } from 'react-redux';
import { counterAction } from '../src/store/counterReducer';

function App() {
    const counter = useSelector((state) => state.counter);
    const dispatch = useDispatch();

    const handleOnClick = () => {
        dispatch(counterAction.addCounter());
    }

    return (
        <React.Fragment>
            <span>{counter}</span>
            <button onClick={handleOnClick}>+1</button>
        </React.Fragment>
    );
}

export default App;
```

## ๐ redux Ducks ๊ตฌ์กฐ
- Action Type๊ณผ Action ๊ทธ๋ฆฌ๊ณ  Reducer๋ฅผ ๋ฐ๋ก ๊ด๋ฆฌํ๋๋ฐ ๊ทธ๊ฑธ ํ๋์ ํ์ผ๋ก ๊ด๋ฆฌํด์ ๋ชจ๋ํ ํ๋ ๋ฐฉ๋ฒ์ด๋ค.
- ์ ์ง๋ณด์์ ๊ฐ๋์ฑ์ด ์ข์์ง๋ค.

```javascript
// actions
const ADD_COUNTER = "ADD_COUNTER";
const MINUS_COUNTER = "MINUS_COUNTER";
const CHANGE_COUNTER = "CHANGE_COUNTER";

// action creators
const counterAction = {
    addCounter: () => ({ type: ADD_COUNTER }),
    minusCounter: () => ({ type: MINUS_COUNTER }),
    changeCounter: (item) => ({ type: CHANGE_COUNTER, payload: item })
};

// reducer
const counterReducer = (state = 0, action) => {
    const { type = '', payload = 0 } = action;
    switch (type) {
        case ADD_COUNTER:
        return state + 1;
        case MINUS_COUNTER:
        return state - 1;
        case CHANGE_COUNTER:
        return payload;
        default:
        return state;
    }
};

export { counterReducer, counterAction };
```