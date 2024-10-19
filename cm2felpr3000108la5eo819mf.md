---
title: "Replace vs Replace All"
seoTitle: "Replace vs Replace All Comparison"
seoDescription: "Learn how `replace` and `replaceAll` functions differ, and discover the benefits of using `replaceAll` for global string replacements"
datePublished: Sat Oct 19 2024 00:11:35 GMT+0000 (Coordinated Universal Time)
cuid: cm2felpr3000108la5eo819mf
slug: replace-vs-replace-all
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729295816550/b33f0ce8-9648-49b8-a755-f36d89f4f901.png
tags: javascript, nodejs, typescript

---

There is a good chance that `replace` does not work how you think:

```javascript
const numbers = "10.00.00.0000"

const replaced = numbers.replace(".", "_")
console.log(replaced) // '10_00.00.0000'
```

Wait what? It only replaced the first instant, `replace` is a simple function and expects you to pass a regular expression if you want more complex results. We can pass an expression that makes it run a global replacement like so:

```javascript
const numbers = "10.00.00.0000"

const globalReplace = numbers.replace(/\./g, "_");
console.log(globalReplace); // '10_00_00_0000'
```

It works, but do any of us really understand RegEx 🤪. Now, there is a more straightforward method.

```javascript
const numbers = "10.00.00.0000"

const replacedAll = numbers.replaceAll(".", "_")
console.log(replacedAll) // '10_00_00_0000'
```

The fantastic function `replaceAll` has full support across all browsers except IE; you can find the [full breakdown here](https://caniuse.com/?search=replaceAll).

**Update 20/10/2024:**

After posting on BlueSky, [Larry Williamson](https://bsky.app/profile/l422y.com) pointed out another method of replacing all occurrences in a string.

```javascript
const numbers = "10.00.00.0000"

const splitReplace = numbers.split(".").join("_")
console.log(splitReplace) // '10_00_00_0000'
```

The speed difference between them is negligible. You have to be parsing large strings before even getting close to a 0.01 millisecond difference in speed. Like all quick benchmarking using, [`performance.now`](http://performance.now)`()` take it with a pinch of salt. Personally, I will be reaching for `replaceAll` from now on.