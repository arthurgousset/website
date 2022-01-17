---
title: "🤷‍♂️ Java (noob notes)"
date: 2021-01-10T12:00:00+01:00
draft: true
showtoc: true
tags: ["java", "noob notes"]
---

## Formatting and style

### Indentation

> Line wrapping for if statements should generally use the 8-space rule, since conventional (4 space) indentation makes seeing the body difficult. For example:

```java
//USE THIS INDENTATION INSTEAD
if ((condition1 && condition2)
        || (condition3 && condition4)
        ||!(condition5 && condition6)) {
    doSomethingAboutIt();
} 
```

_Source: [Oracle](https://www.oracle.com/java/technologies/javase/codeconventions-indentation.html#248)_

### Naming

Classes: capitalised
Methods: lowercase camelcase

## [`package java.lang`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/package-summary.html)

Provides classes that are fundamental to the design of the Java programming language:
- The most important classes are `Object`, which is the root of the class hierarchy, and 
- `Class`, instances of which represent classes at run time.

The class `Math` provides commonly used mathematical functions such as sine, cosine, and square root. 
The classes `String`, `StringBuffer`, and `StringBuilder` similarly provide commonly used operations on character strings.

Class `Throwable` encompasses objects that may be thrown by the throw statement. Subclasses of `Throwable` represent errors and exceptions.

### Class [`java.lang.String`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html)

The String class represents character strings. All string literals in Java programs, such as "abc", are implemented as instances of this class.

**Strings are constant**; their values cannot be changed after they are created.

#### [String.length()](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html#length())

```java
public char charAt(int index)
```

Returns the length of this string. The length is equal to the number of Unicode code units in the string.

#### [String.charAt()](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html#charAt(int))

```java
public char charAt(int index)
```

Returns the char value at the specified index. An index ranges from 0 to length() - 1.
