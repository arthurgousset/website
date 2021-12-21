---
title: "Python"
date: 2021-12-21T12:00:00+01:00
draft: true
showtoc: true
tags: ["python"]
---

## Sets

The `difference_update()` method removes the items that exist in both sets.

The `difference_update()` method is different from the `difference()` method, because the `difference()` method returns a new set, without the unwanted items, and the `difference_update()` method removes the unwanted items from the original set.

```py
# difference = new set (return type = set)
new = x.difference(s)
# difference_update = update set (return type = None)
x.difference_update(s)
```

Source: [W3School](https://www.w3schools.com/python/ref_set_difference_update.asp)
    
The `update()` method updates the current set, by adding **items** from another set (or any other iterable).

The `add()` method adds an **element** to the set.

```py
# update = same set (return type = None)
x.update(s)
# add = same set (return type = None)
x.add("a")
```

Source: [W3School](https://www.w3schools.com/python/ref_set_update.asp)

## Dictionaries

`d.items()` and `ErrorValue: too many values to unpack (expected 2)`

Source: [Career Karma](https://careerkarma.com/blog/python-valueerror-too-many-values-to-unpack-expected-2/)