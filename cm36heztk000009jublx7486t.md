---
title: "Immutable Updates with "with""
seoTitle: "Effortless Immutable Updates using "with"
seoDescription: "Learn how to use the `with()` function for immutable array updates without altering the original array"
datePublished: Wed Nov 06 2024 23:00:07 GMT+0000 (Coordinated Universal Time)
cuid: cm36heztk000009jublx7486t
slug: immutable-updates-with-with
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1730900556119/e1cda98e-09a0-45ab-9b46-e29d5586fdb3.png
tags: javascript, typescript

---

Are you looking to update the value in an array but not change the original? Say hello to `with()`. The `with` function allows you to update a value in an array but return a copy with the updated value, not update the original. Pretty simple to use:

```javascript
const consoles = ["PS4", "Switch"]

const updatedConsoles = consoles.with(0, "PS5")
console.log(updatedConsoles) // [ 'PS5', 'Switch' ]
```

The `with` function has two parameters: the index you want to update and the value you want to update it with. Trying to update an index that is not in the array will throw a [range error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RangeError). `with` is currently supported in all [major browsers](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RangeError) and is a handy function for immutable array transformations.