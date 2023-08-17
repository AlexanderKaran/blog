---
title: "Nullish Coalescing Operator"
seoDescription: "When should you use the nullish coalescing operator or the or operator in JavaScript?"
datePublished: Thu Aug 17 2023 00:59:15 GMT+0000 (Coordinated Universal Time)
cuid: cllegekvs000109mrhdigft26
slug: nullish-coalescing-operator
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692234301828/08697b64-0b3b-4cce-954f-b54e329a108a.png
tags: js, javascript, typescript

---

We often use the or operator `||` in JavaScript to create a fallback value. However, this comes with risks, and you should try to use nullish coalescing operator instead `??`. When we use the or operator, it will default to the value provided if the value is falsy, like so:

```javascript
const user = {_id: 1, name: null}

const name = user?.name || "John Doe"
console.log(name) // "John Doe"
```

Here we safely unwrap the name in case it is `null` or `undefined` if the value is falsy, we fallback to the string `John Doe`. However, think about what we are doing here. Other values register as falsy not just `null` or `undefined`. Let's compare the two operators on a few different values to see the difference.

```javascript
console.log(false || "Error") // 'Error'
console.log(false ?? "Error") // ??

console.log("" || "No value given") // 'No value given'
console.log("" ?? "No value given") // ''

console.log(0 || "Number missing") // 'Number missing'
console.log(0 ?? "Number missing") // 0
```

Here you can see the or operator will fall back to the given value for an empty string, the number zero and a false boolean. When you want to provide fallback values when accessing something that might be `null` or `undefined` it would be best if you reached for the `??` first, unless, for example, you want to create a fallback for an empty string.

Let's look at a real example of where it can cause problems. Say you have a setting where a user can set the volume, but if it has not, you fall back to default. If the user has set the volume to zero and you use the or operator, you will fall back to the default.

```javascript
const userSetVolume = 0
const defaultVolume = 5

const volume = userSetVolume || defaultVolume
console.log(volume) // 5

const volume = userSetVolume ?? defaultVolume
console.log(volume) // 0
```

The nullish coalescing operator is a great way to provide a default value when safely unwrapping or accessing values in JavaScript. Give it a try.