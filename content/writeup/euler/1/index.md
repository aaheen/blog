---
title: "Multiples of 3 or 5"
date: 2022-02-24T14:28:09-06:00
author: "Erik Heen"
tags: ["euler","math","go","easy"]
description: "Difficulty: Easy" 
draft: false
canonicalURL: "https://heen.dev/euler/1"
---
### Question
[Original post on ProjectEuler.net](https://projecteuler.net/problem=1)

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6, 9. The sum of these multiples is 23.

Find the sum of all the multiples of 3 or 5 below 1000.

___
### Solution

This problem is essentially checking the exact same logic as **Fizzbuzz**, so I feel there isn't much to be said about the fundamentals of the math and logic behind this.

The **Go** language, however, has a semantically convenient and syntactically beautiful way to implement this. Instead of writing cascading `if {} else if {} else {}` statements that get tedious and ugly, `switch` statements without arguments are used. A `switch` statement without an argument is the same as writing `switch true`, meaning it will evaluate each `case` in order until one evaluates to true. This allows me to write more readable code, while also bypassing any extraneous redundancy checking.

```go
// Returns the sum of all multiples of 3 and 5 below n.
func sumThreeFive(n uint64) sum uint64 {
    sum = 0
	for i := uint64(0); i < n; i++ {
		switch {
		case i%3 == 0:
			sum += i
		case i%5 == 0:
			sum += i
		}
	}
	return sum
}
```