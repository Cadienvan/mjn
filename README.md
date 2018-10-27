<h1 align="center"> ⚡️ MJN ⚡️ </h1>

<h6 align="center">
Simple pseudo-monad to check if a key or a value exists in an object.
</h6>

<p align="center">
  <a href="https://travis-ci.org/micheleriva/mjn">
    <img src="https://img.shields.io/travis-ci/micheleriva/mjn.svg?style=for-the-badge" alt="Build Status" />
  </a>
  <a href="https://codecov.io/gh/micheleriva/mjn">
    <img src="https://img.shields.io/codecov/c/github/micheleriva/mjn.svg?style=for-the-badge" alt="Coverage" />
  </a>
  <a href="https://codeclimate.com/github/micheleriva/mjn">
    <img src="https://img.shields.io/codeclimate/maintainability/micheleriva/mjn.svg?style=for-the-badge" alt="Maintainability">
  </a>
  <a href="https://github.com/prettier/prettier">
     <img src="https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=for-the-badge" />
  </a>
  <a href="https://img.shields.io/badge/speed-blazing%20%F0%9F%94%A5-brightgreen.svg?style=for-the-badge">
    <img src="https://img.shields.io/badge/speed-blazing%20%F0%9F%94%A5-brightgreen.svg?style=for-the-badge" alt="Blazing Fast" />
  </a>
  <a href="https://bundlephobia.com/result?p=mjn@latest">
    <img src="https://img.shields.io/bundlephobia/minzip/mjn.svg?style=for-the-badge" />
  </a>
</p>

<div align="center">
  <img src="/docs/mjn.png" align="center" style="max-width:80%;" />
</div>

<br /><br />

> No `cannot get property x of undefined`. Just returns `void 0` (undefined) if a value or a key does not exist. Highly inspired from Java's Optional Type.

# Index

- [Installation](#installation)
- [Usage](#usage)
  - [Simple Example](#simple-example)
  - [Real World React Example](#real-world-react-example)
- [Demos](#demos)
- [License](#license)

# Installation

**yarn**

```sh
yarn add mjn
```

**npm**

```sh
npm install --save mjn
```

**cdn**

```html
<script src="https://cdn.jsdelivr.net/npm/mjn@latest/dist/dist.min.js"></script>
```

# Usage

### Simple Example

```js
import maybe from "mjn"; // Or import the library as you wish using npm or CDN script tag!

const myObject = {
  user: {
    name: "John",
    surname: "Doe",
    birthday: "1995-01-29",
    contacts: {
      email: "foo@bar.com",
      phone: "000 0000000"
    },
    languages: ["english", "italian"]
  }
};

const a = maybe(myObject, "user.name");
const b = maybe(myObject, "user.languages[1]");
const c = maybe(myObject, "foo.bar.baz");
const d = maybe(myObject, "foo.bar.baz", "no value!");
const e = maybe(myObject, "foo.bar.baz", () => "I can be a function!");

if (a) {
  console.log(a); // => John
}

if (b) {
  console.log(b); // => italian
}

if (c) {
  console.log(c); // => won't log anything!
}

if (d) {
  console.log(d); // => "no value!"
}

if (e) {
  console.log(e); // => "I can be a function!"
}
```

### Real World React Example

```jsx
import React from "react";
import ReactDOM from "react-dom";
import maybe from "mjn";

const user = {
  name: {
    first_name: "John",
    last_name: "Doe"
  },
  contacts: {
    phone: "+00 000 0000000",
    email: "john@doe.do"
  }
};

const App = () => (
  <div className="App">
    <h1>Hello {maybe(user, "name.first_name")}!</h1>
    <h2> {maybe(user, "contacts.email")} </h2>

    <p>
      {maybe(user, "contacts.phone.office", "You don't have an office phone.")}
    </p>
  </div>
);

const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

# Demos

### React.js

[![React Example](/docs/react.png)](https://codesandbox.io/s/l71m022x99)
[![Edit l71m022x99](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/l71m022x99)

### Vue.js

[![Vue Example](/docs/vue.png)](https://codesandbox.io/s/6j7438n7rr?module=%2Fsrc%2Fcomponents%2FHelloWorld.vue)
[![Edit Vue Template](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/6j7438n7rr?module=%2Fsrc%2Fcomponents%2FHelloWorld.vue)

### Vanilla JS

[![Vanilla JS](/docs/vanillajs.png)](https://codesandbox.io/s/30w08xl6wq?module=%2Fsrc%2Findex.js)
[![Vanilla JS](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/30w08xl6wq?module=%2Fsrc%2Findex.js)

# License

[MIT](/LICENSE.md)
