---
title: "🤷‍♂️ Java (noob notes)"
date: 2021-01-10T12:00:00+01:00
draft: false
showtoc: true
tags: ["java", "noob notes"]
---

Quick link: [Oracle Java Docs](https://docs.oracle.com/en/java/javase/17/docs/api/index.html)

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

* File: `<Class>.java`
* Class: capitalised
* Method: lowercase camelcase

## Loops

### for

```java
for (1. initialise; 2. if condition; 4. then iterate) {
    // 3. do statement
}
```

1. initialises variable (can be initialised elsewhere)
2. checks condition
3. executes statements
4. iteration

*Source: POP2 Session 1*


### for-each

```java
// for-each
for (<type> <name> : arr) { 
  // make use of <name> variable;
}

// equivalent to normal for loop
for (int i = 0; i < arr.length; i++) { 
  <type> <name> = arr[i];
  // make use of <name> variable;;
}

// Example 
public static int maximum(int[] numbers){
  
  // defines variable
  int max = numbers[0];
  
  // for each iteration
  for (int num : numbers){
    if (num > max) {
      max = num;
    }
  }
  
  return max;
```

**Limitation**: 

- Not appropriate when you want to **modify** the array
 
```java
for (int num : marks) {
  // only changes num, not the array element
  num = num*2; 
}
```
-  Only iterates **forward** over the array in **single steps**

*Source: [Geekforgeeks](https://www.geeksforgeeks.org/for-each-loop-in-java/)*


### while

// TODO


### do while

// TODO


## Lambda expression

> A lambda expression is a short block of code which takes in parameters and returns a value. 
> 
> Lambda expressions are similar to methods, but they do not need a name and they can be implemented right in the body of a method.

*Source: [W3School](https://www.w3schools.com/java/java_lambda.asp)*

The simplest lambda expression contains a single `parameter` and an `expression`:

```java
parameter -> expression
```

`Expressions` are limited. They have to immediately return a value, and they cannot contain variables, assignments or statements such as `if` or `for`.

To use more than one parameter, wrap them in parentheses:

```java
(parameter1, parameter2) -> expression
```

To do more complex operations, a code block can be used with curly braces. If the lambda expression needs to return a value, then the code block should have a return statement.

```java
(parameter1, parameter2) -> { code block }
```

Example: 

```java
// Some ArrayList instance: 
// e.g. ArrayList<String> lst = ArrayList<String>();
lst.removeIf( s -> lst.indexOf(s) % 2 == 0);

```

## Package: [java.lang](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/package-summary.html)

Provides classes that are fundamental to the design of the Java programming language:
- The most important classes are `Object`, which is the root of the class hierarchy, and 
- `Class`, instances of which represent classes at run time.

The class `Math` provides commonly used mathematical functions such as sine, cosine, and square root. 
The classes `String`, `StringBuffer`, and `StringBuilder` similarly provide commonly used operations on character strings.

Class `Throwable` encompasses objects that may be thrown by the throw statement. Subclasses of `Throwable` represent errors and exceptions.

### Class: [`java.lang.reflect.Array`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/reflect/Array.html)

N.B: The package *java.lang.reflect* provides classes and interfaces for obtaining reflective information about classes and objects. 

```java
public final class Array
extends Object
```

The Array class provides static methods to dynamically create and access Java arrays. 


#### `<type>[] <name> = new <type>[<size>]`

In Java, all arrays are **dynamically allocated**.

```java 
/* In one step: 
 * <type>[] <name> = new <type>[<size>];
*/
int[] arr = new int[20];
int[][] arr2D = new int[10][20]; //a 2D array or matrix
int[][][] arr3D = new int[10][20][10]; //a 3D array

/* 
 * In two steps: 
 * <type>[] <name>;
 * <name> = new <type>[<size>];
*/
int[] arr;
arr = new int[20];

/*
 * As array literal: 
 * <type>[] <name> = new <type>[]{ element, element, element, ... }; 
*/
int[] arr = new int[]{ 1,2,3,4,5,6,7,8,9,10 }; 
```

*Source: [Geekforgeeks](https://www.geeksforgeeks.org/arrays-in-java/)*


#### `arr.length`

Since arrays are objects in Java, we can find their length using the object **property** `length`. Instead of `s.length()`, which is a String method that computers the length of a *String*.

*Source: [Geekforgeeks](https://www.geeksforgeeks.org/arrays-in-java/)*

#### [`arr.clone()`](####obj.clone())

For detail see: [`obj.clone()`](####obj.clone()) in this doc.

**Deep copy and shallow copy**:

> When you clone a single-dimensional array, such as `Object[]`, a “**deep copy**” is performed with the new array containing copies of the original array’s elements as opposed to references.
>
> A clone of a multi-dimensional array (like `Object[][]`) is a “**shallow copy**,” however, which is to say that it creates only a single new array with each element array a reference to an original element array, but subarrays are shared. 

*Source: [Geekforgeeks](https://www.geeksforgeeks.org/arrays-in-java/)*

**Context**: 
- Every array type implements the **interface** *Cloneable* (*Source: [Geekforgeeks](https://www.geeksforgeeks.org/arrays-in-java/)*). 
- Since the Array class **extends** the *Object* class (see class signature below), it **inherits** the `obj.clone()` method defined in the *Object* class.

```java
public final class Array
extends Object
```

### Class: [java.lang.Object](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Object.html)

```java
public class Object
```

- Class Object is the root of the class hierarchy. 
- Every class has Object as a superclass. 
- All objects, including arrays, implement the methods of this class.

#### [`obj.clone()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Object.html#clone())

```java
protected Object clone()
                throws CloneNotSupportedException
```

Creates and returns a copy of this object. The precise meaning of "copy" may depend on the class of the object. 

The general intent is that, for any object `x`, the expression:
- `x.clone() != x` will be **true**, 
- `x.clone().getClass() == x.getClass()` will be **true**, and
- `x.clone().equals(x)` will be **true**.

N.B: ⚠️ But these are not absolute requirements! ⚠️ 


### Class: [java.lang.Character](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html)

The Character class **wraps a value of the primitive type `char` in an object**. An object of class `Character` contains a single field whose type is `char`.

Two parameter types: 
- int codepoint (unicode)
- char ch (character)

#### [`getType(char ch)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html#getType(char))

#### [`Character.isAlphabetic()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html#isAlphabetic(int))

```java
public static boolean isAlphabetic(int codePoint)
```

Mostly used with `s.codePointAt(i)` e.g.

```java
Character.isAlphabetic(s.codePointAt(i))
```

#### [`Character.isLetter(char ch)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html#isLetter(char))

```java
public static boolean isLetter(char ch)
```

A character is considered to be a letter if its general category type, provided by `Character.getType(ch)`, is any of the following:

* UPPERCASE_LETTER
* LOWERCASE_LETTER
* TITLECASE_LETTER
* MODIFIER_LETTER
* OTHER_LETTER


#### [`Character.isDigit(char ch)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html#isDigit(char))

```java
public static boolean isDigit(char ch)
```

A character is a digit if its general category type, provided by `Character.getType(ch)`, is DECIMAL_DIGIT_NUMBER.



#### [`Character.isLowerCase(char ch)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html#isLowerCase(char))

```java
public static boolean isLowerCase(char ch)
```

A character is lowercase if its general category type, provided by `Character.getType(ch)`, is LOWERCASE_LETTER


#### [`Character.isUpperCase(char ch)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html#isUpperCase(char))

```java
public static boolean isUpperCase(char ch)
```

A character is uppercase if its general category type, provided by `Character.getType(ch)`, is UPPERCASE_LETTER.


#### [`Character.isWhitespace(char ch)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html#isWhitespace(char))

```java
public static boolean isWhitespace(char ch)
```

A character is a Java whitespace character if and only if it satisfies one of the following criteria:
It is a Unicode space character (SPACE_SEPARATOR, LINE_SEPARATOR, or PARAGRAPH_SEPARATOR) but is not also a non-breaking space ('\u00A0', '\u2007', '\u202F').
* It is '\t', U+0009 HORIZONTAL TABULATION.
* It is '\n', U+000A LINE FEED.
* It is '\u000B', U+000B VERTICAL TABULATION.
* It is '\f', U+000C FORM FEED.
* It is '\r', U+000D CARRIAGE RETURN.
* It is '\u001C', U+001C FILE SEPARATOR.
* It is '\u001D', U+001D GROUP SEPARATOR.
* It is '\u001E', U+001E RECORD SEPARATOR.
* It is '\u001F', U+001F UNIT SEPARATOR.



#### [`Character.toLowerCase(char ch)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html#toLowerCase(char))

```java
public static char toLowerCase(char ch)
```

Converts the character argument to lowercase using case mapping information from the UnicodeData file.

#### [`Character.toUpperCase(char ch)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html#toUpperCase(char))

```java
public static char toUpperCase(char ch)
```

Converts the character argument to uppercase using case mapping information from the UnicodeData file.

### Class: [java.lang.String](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html)

The String class represents **character strings**. All string literals in Java programs, such as "abc", are implemented as instances of this class.

Strings are constant (**immutable**); their values cannot be changed after they are created.

#### [`s.length(int index)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html#length())

```java
public char charAt(int index)
```

Returns the length of this string. The length is equal to the number of Unicode code units in the string.

#### [`s.charAt(int index)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html#charAt(int))

```java
public char charAt(int index)
```

Returns the char value at the specified index. An index ranges from 0 to length() - 1.

#### [`s.indexOf()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html#indexOf(int))

```java
public int indexOf(int ch)
```

Returns the index within this string of the first occurrence of the specified character `ch`.

```java
public int indexOf(int ch,
                   int fromIndex)
```

Returns the index within this string of the first occurrence of the specified character, starting the search at the specified index.

#### [`s.codePointAt(int index)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html#codePointAt(int))

```java
public int codePointAt(int index)       
```

Returns the character (Unicode code point) at the specified index. The index refers to char values (Unicode code units) and ranges from 0 to length() - 1.

#### [`s.toLowerCase()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html#toLowerCase())

```java
public String toLowerCase()
```

Converts all of the characters in this String to lower case using the rules of the default locale.

#### [`s.toUpperCase()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html#toUpperCase())

```java
public String toUpperCase()
```

Converts all of the characters in this String to upper case using the rules of the default locale.

## Package: [java.util](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/package-summary.html)

Contains the **collections** framework, some internationalization support classes, a service loader, properties, **random number generation**, string parsing and **scanning** classes, base64 encoding and decoding, a bit array, and several miscellaneous utility classes.

### Class: [`ArrayList<E>`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html)

```java
public class ArrayList<E>
extends AbstractList<E>
implements List<E>, RandomAccess, Cloneable, Serializable
```

- `<E>` = the type of elements in this list

Resizable-array implementation of the `List` interface. Implements all optional list operations, and permits all elements, including `null`. (This class is roughly equivalent to `Vector`, except that it is unsynchronized.)

#### Constructor: [`ArrayList()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html#%3Cinit%3E())

```java
ArrayList<String> lString = new ArrayList<String>()
ArrayList<Integer> lInteger = new ArrayList<Integer>()
```

Constructs an empty list with an initial capacity of ten.

> Elements in an ArrayList are actually **objects**. 
> 
> To use other types, such as `int`, you must specify an equivalent **wrapper class**: `Integer`. For other primitive types, use: `Boolean` for boolean, `Character` for char, `Double` for double, etc:

*Source: [W3School](https://www.w3schools.com/java/javaarraylist.asp)*


#### [lst.size()](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html#size())

```java
public int size()
```

Returns the number of elements in this list.

#### [`lst.remove(int index)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html#remove(int))

Removes the element at the specified position in this list. Shifts any subsequent elements to the left (subtracts one from their indices).

```java
public E remove(int index)
```

#### [`lst.removeIf(predicate)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html#removeIf(java.util.function.Predicate))

```java
public boolean removeIf(Predicate<? super E> filter)
```

Removes all of the elements of this collection that **satisfy the given predicate**.

For context, [`Interface Predicate<T>`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/function/Predicate.html) is a **functional interface** and can therefore be used as the assignment target for a **lambda expression** or method reference.


#### [`lst.indexOf(Object o)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html#indexOf(java.lang.Object))

```java
public int indexOf(Object o)
```

Returns the index of the first occurrence of the specified element in this list, or -1 if this list does not contain the element.