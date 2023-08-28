---
title: "Testing Array Elements in JavaScript"
datePublished: Mon Aug 28 2023 23:13:23 GMT+0000 (Coordinated Universal Time)
cuid: cllvhwnud000109jvayj07bdb
slug: testing-array-elements-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693224465335/ab5c77ed-9bcc-43af-a259-6bacb1cdb4c8.png
tags: javascript, typescript

---

There are so many functions in JavaScript, especially in arrays, that it can be hard to keep track of all of them. You may not have used `every` before, but it is a simple way to ensure each element in the array passes a test.

The array method returns a `truthy` value if each element passes the check inside the provided function or a `falsy` value if one or more fail.

```javascript
const users = [
  {id: 1, name: "Alexander", created: 2015},
  {id: 2, name: "Orhan", created: 2023},
  {id: 3, name: "Akshaya", created: 2023}
]

const startedBefore2024 = users.every(user => {
  return user.created < 2024
})
console.log(startedBefore2024) // true
```

```javascript
const students = [
    { name: 'Alice', age: 21, hasPassed: true },
    { name: 'Bob', age: 19, hasPassed: false },
    { name: 'Charlie', age: 20, hasPassed: true },
    { name: 'Emily', age: 22, hasPassed: false }
];

const allStudentsPassed = students.every(student => {
    return student.hasPassed === true;
});
console.log(allStudentsPassed);  // false
```

As you can see `every` is super simple to use and saves you from having to use a custom filter, reduce or for loop. There is support in every major browser for `every` so start using it today. You can find the full [browser breakdown here](https://caniuse.com/mdn-javascript_builtins_array_every).