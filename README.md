<h1 align="center">Welcome to jest-wake-lock-mock 👋</h1>
<p>
  <img alt="npm" src="https://img.shields.io/npm/v/jest-wake-lock-mock?style=for-the-badge">
  <img alt="GitHub Workflow Status" src="https://img.shields.io/github/workflow/status/jorisre/jest-wake-lock-mock/CI?style=for-the-badge">
  <img alt="Codecov" src="https://img.shields.io/codecov/c/github/jorisre/jest-wake-lock-mock?style=for-the-badge&token=D75F3R5OEO">
  <a href="https://github.com/jorisre/jest-wake-lock-mock/blob/master/LICENSE" target="_blank">
    <img alt="License: MIT" src="https://img.shields.io/github/license/jorisre/jest-wake-lock-mock?style=for-the-badge" />
  </a>
  <a href="https://twitter.com/_jorisre" target="_blank">
    <img alt="Twitter: _jorisre" src="https://img.shields.io/twitter/follow/_jorisre.svg?style=for-the-badge" />
  </a>
</p>

> Mock [Screen Wake Lock API](https://w3c.github.io/screen-wake-lock/) _(`navigator.wakeLock`)_ with ease and run your tests using Jest

### 🏠 [Homepage](https://github.com/jorisre/jest-wake-lock-mock#readme)

## Prerequisites

- node >=10

## Install

```sh
npm i -D jest-wake-lock-mock
# or
yarn add -D jest-wake-lock-mock
```

## Usage

In your `jest.config.js` or `package.json` under `jest` section create a [`setupFiles`](https://jestjs.io/docs/en/configuration#setupfiles-array) array and add `jest-wake-lock-mock` to it.

```js
{
  setupFiles: ['jest-wake-lock-mock'],
  // jest config...
}
```

## Tests

Write your tests with confidence using the same [Screen Wake Lock API](https://w3c.github.io/screen-wake-lock/) api as in the browser.

**Example** ([More](https://github.com/jorisre/jest-wake-lock-mock/blob/master/test/jest-wake-lock-mock.test.ts)):

```js
const requestWakeLock = async () => {
  try {
    const wakeLock = await navigator.wakeLock.request('screen');

    return { wakeLock };
  } catch (error) {
    return { error };
  }
};

test('wakeLock request with success', async () => {
  const { wakeLock, error } = await requestWakeLock(handleRelease);

  expect(error).not.toBeDefined();
  expect(wakeLock).toBeDefined();
  expect(wakeLock?.type).toEqual('screen');
  expect(wakeLock?.released).toBe(false);
});
```

## Author

👤 **Joris**

- Twitter: [@Jor1s\_](https://twitter.com/Jor1s_)
- Github: [@jorisre](https://github.com/jorisre)

## 🤝 Contributing

Contributions, issues and feature requests are welcome!<br />Feel free to check [issues page](https://github.com/jorisre/jest-wake-lock-mock/issues).

## Show your support

Give a ⭐️ if this project helped you!

## 📝 License

Copyright © 2020 [Joris](https://github.com/jorisre).<br />
This project is [MIT](https://github.com/jorisre/jest-wake-lock-mock/blob/master/LICENSE) licensed.

---

_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_
