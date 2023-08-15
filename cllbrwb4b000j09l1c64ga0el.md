---
title: "New JavaScript Array Methods"
datePublished: Tue Aug 15 2023 03:57:40 GMT+0000 (Coordinated Universal Time)
cuid: cllbrwb4b000j09l1c64ga0el
slug: new-javascript-array-methods
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692071913499/a979d953-3bd4-45d8-a3c5-2249d1fb346f.png
tags: javascript, ecmascript, typescript

---

Working with arrays is a staple when it comes to programming, and there are two new methods in JavaScript you should be aware of, `findLast` and `at`. Let's have a closer look at both of them.

## Find Last

We all have used [`find`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find) before on an array, but what if we wanted to start from the end of the array? Well, thanks to [`findLast`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLast) you no longer need to perform some weird logic or use an external library to pull this off.

In this example, you can see how we used `findLast` to find a number greater than ten. It returns the last item in the array as it starts from the end.

```javascript
const numbers = [5, 10, 15, 20, 25]

const number = numbers.findLast(number => number > 10)
console.log(number) // 25
```

## At

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

If you're not using these new methods yet, give them a try, and keep an eye out for future blogs in this series about new features in JavaScript.