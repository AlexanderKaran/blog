---
title: "What's In My Array"
datePublished: Mon Sep 04 2023 05:53:20 GMT+0000 (Coordinated Universal Time)
cuid: clm4gu3iz000g0ale8yue21nj
slug: whats-in-my-array
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693570513309/2ad39269-33d0-4716-b9d4-7f998d23a52a.png
tags: javascript, typescript

---

Arrays are some of the most common data types you work with as a programmer. We filter them, we map over them, we edit them and more. As we spend so much time with them, JavaScript has created some great helper functions to make them easier to work with. Let's look at checking if an array contains a specific value. Say we have a list of IDs and want to check if a given ID is inside the array.

We could use `indexOf` which returns the first index the given value can be found at or `-1` if not present.

```javascript
const ids = [1, 2, 3, 4, 5];
const idToCheck = 3;

const exists = ids.indexOf(idToCheck) !== -1;
console.log(exists) // true
```

Great if we want to grab the index simultaneously, but in this case, I don't care about the index. We could use `some` that checks if at least one element matches the given value.

```javascript
const ids = [1, 2, 3, 4, 5];
const idToCheck = 3;

const exists = ids.some(id => id === idToCheck);
console.log(exists); // true
```

Nice, but now I am passing a function. I think we can slim this down by using `includes` which returns a boolean if the array contains the passed value.

```javascript
const ids = [1, 2, 3, 4, 5];
const idToCheck = 3;

const exists = ids.includes(idToCheck);
console.log(exists); // true
```

We have covered a few array methods here, but I love `includes` it turns some validation checks into one-liners. All these methods have full browser support, but you can find a breakdown in the links below.

* [`Array.prototype.indexOf()`](https://caniuse.com/mdn-javascript_builtins_array_indexof)
    
* [`Array.prototype.some()`](https://caniuse.com/mdn-javascript_builtins_array_some)
    
* [`Array.prototype.includes()`](https://caniuse.com/array-includes)