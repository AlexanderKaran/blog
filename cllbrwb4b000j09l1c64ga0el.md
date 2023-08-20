---
title: "JavaScript Last Item in an Array"
seoDescription: "When getting the last item in a JavaScript array, you should using the new at method."
datePublished: Tue Aug 15 2023 03:57:40 GMT+0000 (Coordinated Universal Time)
cuid: cllbrwb4b000j09l1c64ga0el
slug: javascript-last-item-in-an-array
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692071913499/a979d953-3bd4-45d8-a3c5-2249d1fb346f.png
tags: javascript, ecmascript, typescript

---

The new method [`at`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/at) allows you to return an item in an array at the given index. You might be thinking I can already do this with brackets. The great thing about `at` is it can take negative numbers and count back from the end of the array. The way `at` works gives you an easy way to get the last item in the array. Instead of `array[array.length - 1]` you can now do `array.at(-1)`.

Here you can see how `at` works and how passing a negative number into the bracket method returns undefined.

```javascript
const numbers = [5, 10, 15, 20, 25]

const firstNumber = numbers.at(0)
console.log(firstNumber) // 5

const last = numbers[-1]
console.log(last) // undefined

const lastNumber = numbers.at(-1)
console.log(lastNumber) // 25
```

With excellent browser support, nothing is stopping you from using it. Check the [**browser compatibility list**](https://caniuse.com/mdn-javascript_builtins_array_at) for more info.