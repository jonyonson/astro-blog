---
layout: "../../layouts/BlogPost.astro"
title: "Nullish Coalescing for JavaScript"
description: "Lorem ipsum dolor sit amet"
datePublished: "May 5, 2020"
lastUpdated: "October 14, 2020"
tags: ["javascript"]
heroImage: "/placeholder-hero.jpg"
---

Traditionally in JavaScript, when assigning a default value, we use the logical OR operator (`||`) to check if the left-hand side expression can be converted to false. If this left-hand side expression is falsy, the right-hand side is returned.

```javascript
const props = {
  color: '',
};

const color = props.color || '#222222'; // "#222222"
```

This can sometimes lead to unintended consequences if we wanted certain falsy values to be accepted.

```javascript
const props = {
  delay: 0,
  message: '',
};

const message = props.message || 'default message'; // "default message"
const delay = props.delay || 200; // 200
```

Since `props.message` and `props.delay` are both falsy values (expressions that can be converted to false), the `||` operator returns the right-hand side expression. Examples of expressions that can be converted to false are `null`, `NaN`, `0`, `""` and `undefined`.

## The Nullish Coalescing Operator

ES2020 introduced the nullish coalescing operator to JavaScript. The nullish coalescing operator (`??`) only checks the left-hand side expression for `null` or `undefined` values. If the left-hand side is a falsy value, but is not `null` or `undefined`, the left-hand side is returned.

```javascript
const props = {
  delay: 0,
  message: '',
};

const message = props.message ?? 'default message'; // ""
const delay = props.delay ?? 200; // 0
```

### Other Resources

- [tc39.es/proposal-nullish-coalescing](https://tc39.es/proposal-nullish-coalescing/)
- [babel-plugin-proposal-nullish-coalescing-operator](https://babeljs.io/docs/en/babel-plugin-proposal-nullish-coalescing-operator)
