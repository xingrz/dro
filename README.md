dro
==========

[![][npm-version]][npm-url] [![][npm-downloads]][npm-url] [![license][license-img]][license-url] [![issues][issues-img]][issues-url] [![stars][stars-img]][stars-url] [![commits][commits-img]][commits-url]

A slim DOM manipulation library written in TypeScript.

## Install

```sh
npm install --save dro
```

## Quick start

Basic querying:

```ts
import { $, $$ } from 'dro';
const container = $<HTMLElement>(document, '.foo');
const children = $$(document, '.foo a');
```

Typed query multiple elements at once:

```ts
import { $H } from 'dro';

interface MyForm {
  username: HTMLInputElement;
  password: HTMLInputElement;
  submit: HTMLElement;
}

const form = $H<MyForm>(document, {
  username: '.my-form input.user',
  password: '.my-form input.pass',
  submit: '.my-form button[type="submit"]',
});

console.log(form?.username.value);
```

Create and style an element, then append it to a parent:

```ts
import { append, create, html, attrs, style, on } from 'dro';

append(document.body, () => {
  const el = create('div');
  html(el, 'foo');
  attrs(el, {
    'class': 'foo',
  });
  style(el, {
    'margin-top': '200px',
  });
  on(el, 'click', () => console.log('lol!'));
  return el;
});
```

## License

[MIT License](LICENSE)

[npm-version]: https://img.shields.io/npm/v/dro.svg?style=flat-square
[npm-downloads]: https://img.shields.io/npm/dm/dro.svg?style=flat-square
[npm-url]: https://www.npmjs.org/package/dro
[license-img]: https://img.shields.io/github/license/xingrz/dro?style=flat-square
[license-url]: LICENSE
[issues-img]: https://img.shields.io/github/issues/xingrz/dro?style=flat-square
[issues-url]: https://github.com/xingrz/dro/issues
[stars-img]: https://img.shields.io/github/stars/xingrz/dro?style=flat-square
[stars-url]: https://github.com/xingrz/dro/stargazers
[commits-img]: https://img.shields.io/github/last-commit/xingrz/dro?style=flat-square
[commits-url]: https://github.com/xingrz/dro/commits/master
