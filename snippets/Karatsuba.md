---
title: String starts with substring
shortTitle: Starts with substring
tags: string
cover: blog_images/boutique-home-office-3.jpg
author: chalarangelo
firstSeen: 1/14/2023 11:45 AM
---

Multiplication of two integers using the Karatsuba algorithm 

- Base case : when the number x, y are lesser than 10 use the standard multplication algorithm.
- kartsuba split the number in two parts, and uses recursion.
- For more information : https://youtu.be/yWI2K4jOjFQ

```js
function karatsuba(x, y){
    if (x < 10 && y < 10) return x * y;
    else{
        let n = Math.max(String(x).length, String(y).length);
        let half = Math.floor(n / 2);
        let a = Math.floor(x / (Math.pow(10, half)));
        let b = x % (Math.pow(10, half));
        let c = Math.floor(y / Math.pow(10, half));
        let d = y % Math.pow(10, half);
        let ac = karatsuba(a,c);
        let bd = karatsuba(b,d);
        let ad_plus_bc = karatsuba(a+b, c+d)-ac-bd;
        let result = ac * (10 ** (2 * half)) + (ad_plus_bc * (10 ** half)) + bd;
        return result;
    }
};
```