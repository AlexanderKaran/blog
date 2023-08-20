---
title: "JavaScript Find Last"
seoDescription: "Need to search through an array in JavaScript but need to start from the end? Find last works like find but starts from the end of the array."
datePublished: Sat Aug 19 2023 00:23:26 GMT+0000 (Coordinated Universal Time)
cuid: cllha07ym000409me2nwx4odu
slug: javascript-find-last
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692404924264/fe10a0cd-98af-40c5-89d3-0ee4151d19ca.png
tags: js, javascript, typescript

---

We all have used [`find`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find) before on an array, but what if we wanted to start from the end of the array? Well, thanks to [`findLast`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLast) you no longer need to perform some weird logic or use an external library to pull this off.

In this example, you can see how `findLast` works the same way as `find` the only difference is that it starts from the end of the array.

```javascript
const numbers = [5, 10, 15, 20, 25]

// Find starts from the begining
const n = numbers.find(num => num > 10)
console.log(n) // 15

// Find Last starts from the end
const n = numbers.findLast(num => num > 10)
console.log(n) // 25
```

Other than IE, you can use `findLast` in all major browsers. Check the [**browser compatibility list**](https://caniuse.com/mdn-javascript_builtins_array_findlast) for more info.