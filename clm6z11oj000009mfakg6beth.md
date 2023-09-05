---
title: "Padding Strings"
datePublished: Tue Sep 05 2023 23:58:09 GMT+0000 (Coordinated Universal Time)
cuid: clm6z11oj000009mfakg6beth
slug: padding-strings
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693958262728/2238d610-6855-4969-8b09-c93cab0daed5.png
tags: javascript, typescript

---

We have been messing with arrays in the last few blogs, so let's switch gears and look at some string methods. There are a lot of built-in methods on a string, but two you might not know are `padStart()` and `padEnd()`. So what do they do? They pad a string with another string at the start or the end. Let's take a look at some examples.

Take a phone number. Sometimes, we don't want to show the whole number and one way to obscure the printout is `padStart()`:

```javascript
const phone = "+61422167343"
const endDigits = phone.slice(-3)

const masked = endDigits.padStart(phone.length, "*")
console.log(masked)
```

There are more elegant ways of doing this, but it's an excellent example of using one of the pad methods. The first argument is the target length of the string once the string has been padded. The second argument is the string to pad the current string with. If no value is passed, it uses an empty string.

Let's use another example. Say I wanted to print a text table in my console listing something like most rock albums ever sold. I could use `padEnd` to ensure each cell is the same width.

```javascript
const ID_WIDTH = 5;
const ARTIST_WIDTH = 20;
const ALBUM_WIDTH = 35;
const SALES_WIDTH = 15;

const albums = [
  { id: 1, artist: "The Wiggles", album: "Wiggle Time", sales: "99M" },
  { id: 2, artist: "The Eagles", album: "Their Greatest Hits (1971–1975)", sales: "45M" },
  { id: 3, artist: "Led Zeppelin", album: "Led Zeppelin IV", sales: "37M" },
  { id: 4, artist: "Pink Floyd", album: "The Wall", sales: "33M" },
];

function displayTable(data) {
  // Headers
  console.log(
    "ID".padEnd(ID_WIDTH) + 
    "Artist".padEnd(ARTIST_WIDTH) + 
    "Album".padEnd(ALBUM_WIDTH) + 
    "Sales".padEnd(SALES_WIDTH)
  );

  // Separator
  console.log("-".repeat(ID_WIDTH + ARTIST_WIDTH + ALBUM_WIDTH + SALES_WIDTH));

  // Data rows
  for (const item of data) {
    const id = item.id.toString().padEnd(ID_WIDTH);
    const artist = item.artist.padEnd(ARTIST_WIDTH);
    const album = item.album.padEnd(ALBUM_WIDTH);
    const sales = item.sales.padEnd(SALES_WIDTH);

    console.log(`${id}${artist}${album}${sales}`);
  }
}

displayTable(albums);
```

Which would log a table with the following output:

```markdown
ID   Artist              Album                             Sales         
---------------------------------------------------------------------------
1    The Wiggles         Wiggle Time                       99M           
2    The Eagles          Their Greatest Hits (1971–1975)   45M           
3    Led Zeppelin        Led Zeppelin IV                   37M           
4    Pink Floyd          The Wall                          33M
```

The pad functions have full browser support (except IE), but you can find the [full breakdown here](https://caniuse.com/pad-start-end).