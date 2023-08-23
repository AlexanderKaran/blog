---
title: "Errors in TypeScript"
seoDescription: "How do you create custom error types in TypeScript or add values to the Error object? Time to reach for a class."
datePublished: Wed Aug 23 2023 00:08:15 GMT+0000 (Coordinated Universal Time)
cuid: cllmz83wn000009moa27y7c0c
slug: errors-in-typescript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692748970229/f21c1e75-1c4d-4be1-8bdc-741c35c9bd43.png
tags: javascript, typescript, types

---

Throwing a custom error in JavaScript is easy. Want to add a status field to all errors thrown by networking code, no problem. Need to add a further info field? Anything goes in JavaScript, but in TypeScript, things are different. So what's the best way to extend an Error? Time to reach for a class. Let's use the example of throwing a custom error for networking with a status property.

```typescript
class APIError extends Error {
    status: number;

    constructor(message: string, status: number) {
        super(message);
        this.status = status;

        Object.setPrototypeOf(this, APIError.prototype);
    }
}

const err = new APIError("Some error", 401)
console.log(err) // Error: 'Some error'
console.log(err.status) // 401
```

Super easy, right? Ignore `Object.setPrototypeOf` we will get to that later. Now we can throw our custom error when making network requests.

```typescript
  const res = await fetch("some-url")
  if (!res.ok) {
    throw new APIError("Could not fetch the data from some url", res.status)
  }
  
  return await res.json()
```

Even better, we can also use the class as a Type. Using a library like [SWR](https://swr.vercel.app) for networking, you can pass the APIError class in as a type to define the error type.

```typescript
import useSWR from 'swr'
import type APIError from "errors"
import type User from "types/user"

const { data, error, isLoading } = useSWR<User, APIError>('/api/user', fetcher)
```

So now let's explain that weird line `Object.setPrototypeOf(this, APIError.prototype)`. When working with TypeScript and ES6 classes, you can sometimes run into an issue when extending them. Sometimes when the class is set up or compiled, its prototype chain can be incorrect. Every object in JavaScript has a prototype property, which it uses to inherit values and methods; this passing of methods and values is the prototype chain.

Let's use a code example to explain this further.

```typescript
const error = new APIError("An error", 500);

console.log(error instanceof APIError); // true
console.log(error instanceof Error);  // true
```

As you can see `error` is an instance of both `APIError` and `Error`. If we remove the set prototype of line, there is a chance that the first line might return false even though it should be true when compiling to older versions of JS. So make sure to keep this line there to be safe.

One final thing that always comes up is checking the error type in the catch clause. This is pretty straightforward; you use `instanceof`.

```typescript
try {
  const error = new APIError("The request failed", 400)
  throw error
} catch (err) {
  if (err instanceof APIError) {
    console.log(err.status)
  }
}
```

Extending errors in TypeScript is easy when you reach for a class.