---
title: "🤷‍♂️ Competitive Programming (noob notes)"
date: 2021-06-10T12:00:00+01:00
draft: false
tags: ["competitive programming", "algorithms", "leetcode", "codeforces", "hackerrank", "time complexities", "noob notes"]
---

At university programming questions in algorithms and data structures classes usually give you an upper bound time complexity in Big-O notation to achieve full marks.

Programming questions on CodeForces, LeetCode and HackerRank don't usually provide an upper bounds in Big-O notation but instead provide

* an **input size** of the type $$1 \leq n \leq 10^5$$ 
* and a **time limit** in seconds (usually 1 or 2 seconds).

It's then up to you to find out what an appropriate run time for your algorithm would be. For example, you might get:

* 60% of the points for passing test cases in 2 seconds for input sizes $$1 \leq n \leq 10^3$$
* and 100% of the points for passing test cases in 2 seconds for input sizes $$1 \leq n \leq 10^5$$

## In Practice

The user [MaxiMaxi](https://codeforces.com/profile/maximaxi) shared a very useful table from the [Competitive Programming 3](https://www.amazon.co.uk/Competitive-Programming-3/dp/B00FG8MNN8) book (by [Steven Halim](https://www.comp.nus.edu.sg/~stevenha/) from NUS) on the CodeForces [forum](https://codeforces.com/blog/entry/21772).

_How do I use this?_

1. check the input size in the problem statement e.g. $$1 \leq n \leq 10^5 = 100000$$
2. check the table for the worst case runtime in big-O notation e.g.
$$O(n\log_2n)$$
3. chose your algorithm accordingly

{{< figure src="https://i.imgur.com/pmHPGi8.png" width="100%" >}}
