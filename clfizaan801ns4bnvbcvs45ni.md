---
title: "Arithmetic Series"
seoTitle: "How to find a missing number in an array"
seoDescription: "How do you find a missing number in an array? What is Arithmetic Series, and where does it come from?"
datePublished: Wed Mar 22 2023 01:00:39 GMT+0000 (Coordinated Universal Time)
cuid: clfizaan801ns4bnvbcvs45ni
slug: arithmetic-series
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/YJiB74zQLMs/upload/b894db190278c55ec81240d5036b7a17.jpeg
tags: algorithms, javascript, array, mathematics

---

Recently I found myself having to find a missing number in an array. After some searching on the internet, I found a simple and efficient answer. I wanted to know why it worked and dug further into the math. Most explanations hit me with pages and pages of algebra, not the friendliest intro. Once I dug further, I scratched the itch in my brain about why this works and fell back in love with math.

%[https://media.giphy.com/media/zPbnEgxsPJOJSD3qfr/giphy.gif] 

Here is the problem: we have an array of numbers and need to find the missing one.

```javascript
const numbers = [0, 1, 2, 3, 4, 5, 7, 8, 9, 10]
```

It turns out there is a simple formula for finding the missing number.

```plaintext
total = n * (n + 1) / 2
missing_number = total - sum
```

When I first looked at that, I died inside a little. What is n? Let's break it down further. The n stands for the last number in the series. In this case, our series goes from zero to ten, so n is ten. The sum is the total of all the numbers in the array. Let's turn this into a JavaScript function to see it in action.

```javascript
function findMissingNumber(numbers) {
    let actualSum = 0
    for (const num of numbers) {
        actualSum += num
    }

    // Also called n
    const lastNumberInSeries = numbers.length

    const shouldBeSum = (lastNumberInSeries + 1) * (lastNumberInSeries / 2);
  
  	const missingNumber = shouldBeSum - actualSum

    console.log(`Missing number is: ${missingNumber}`)
}

findMissingNumber([0, 1, 2, 3, 4, 5, 7, 8, 9, 10])
```

The missing number will be six if you run this in your browser's console or any other JS runtime. Great, it works; however, I could not leave it here. I want to know why this works. Why does this calculation give me the missing number? It turns out it has something to do with the arithmetic series.

Rewind to the late 17 hundreds. A student called Carl Friedrich Gauss impressed his teacher by finding the sum of numbers from one to 100 incredibly fast. Carl figured he had 50 pairs of numbers and could multiply that by 101.

```plaintext
50 * 101 = 5050 

Is the same as 

1 + 2 + 3 + 4 + 5 .... + 98 + 99 + 100
```

However, where does the 101 number come from? 101 is the answer to adding each pair together.

```plaintext
100 + 1 = 101
99 + 2 = 101
98 + 3 = 101
```

How Carl solved this problem led to a general formula for finding the sum of a series of consecutive numbers. Let's tie this back to the code. We can use this formula to calculate the array's total if no numbers are missing.

```javascript
    // Also called n
    const lastNumberInSeries = numbers.length

    const shouldBeSum = (lastNumberInSeries + 1) * (lastNumberInSeries / 2);
```

Based on what we learned above, let's rewrite the function to understand better how the formula fits in.

```javascript
    // Also called n
    const lastNumberInSeries = numbers.length

    // What each pair added together equals e.g 1 + 10 or 2 + 9
    const pairTotal = lastNumberInSeries + 1 // 11

    const numberOfPairs = lastNumberInSeries / 2 // 5

    const shouldBeSum = pairTotal * numberOfPairs // 11 * 5;
```

We can then calculate the actual sum of the array and take it away from shouldBeSum to get the missing number.

```javascript
function findMissingNumber(numbers) {
    let actualSum = 0
    for (const num of numbers) {
        actualSum += num
    }

    // Also called n
    const lastNumberInSeries = numbers.length

    // What each pair added together equals e.g 1 + 10 or 2 + 9
    const pairTotal = lastNumberInSeries + 1 // 11

    const numberOfPairs = lastNumberInSeries / 2 // 5

    const shouldBeSum = pairTotal * numberOfPairs // 11 * 5;
  
  	const missingNumber = shouldBeSum - actualSum

    console.log(`Missing number is: ${missingNumber}`)
}

findMissingNumber([0, 1, 2, 3, 4, 5, 7, 8, 9, 10])
```

Looking at this, I wish my high school teachers had tried to make maths more fun. There are so many patterns, and they bleed into software development all over the place.

As always any questions or find a mistake, leave a comment or reach out on Twitter.