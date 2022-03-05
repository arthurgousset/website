---
title: "🤷‍♂️ Java (noob notes)"
date: 2022-01-10T12:00:00+01:00
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


### switch

- The `default` keyword specifies some code to run if there is no case match
- When Java reaches a `break` keyword, it breaks out of the switch block. This will stop the execution of more code and case testing inside the block.

```java
int day = 4;

switch (day) {
  case 1:
    System.out.println("Monday");
    break;
  case 2:
    System.out.println("Tuesday");
    break;
  case 3:
    System.out.println("Wednesday");
    break;
  case 4:
    System.out.println("Thursday");
    break;
  case 5:
    System.out.println("Friday");
    break;
  case 6:
    System.out.println("Saturday");
    break;
  case 7:
    System.out.println("Sunday");
    break;
}
// Outputs "Thursday" (day 4)
```

*Source: [W3School](https://www.w3schools.com/java/java_switch.asp)*


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

## Inheritance

### Subclass Constructors

Invocation of a superclass constructor must be the first line in the subclass constructor.

The syntax for calling a superclass constructor is:

- `super();` the superclass no-argument constructor is called, or
- `super(parameter list);`: the superclass constructor with a matching parameter list is called.

*Source: [Oracles Java Tutorials](https://docs.oracle.com/javase/tutorial/java/IandI/super.html)*

```java
// < Child >.java
public class < Parent > {
    
    // attributes
    int param1;
    int param2;
    
    // constructor
    < Parent >( int a, int b) {
        param1 = a; 
        param2 = b;
    }
}

// < Child >.java
public class < Child > extends < Parent > {
    
    // constructor
    < Child >( int param1, int param2) {
		super(param1, param2); // calls parent constructor
    }
}


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

#### [`obj.equals(Object obj)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Object.html#equals(java.lang.Object))

```java
public boolean equals(Object obj)
```

Indicates whether some other object is "equal to" this one, true/false).

The equals method implements an equivalence relation on non-null object references:

* It is reflexive: for any non-null reference value x, x.equals(x) should return true.
* It is symmetric: for any non-null reference values x and y, x.equals(y) should return true if and only if y.equals(x) returns true.
* It is transitive: for any non-null reference values x, y, and z, if x.equals(y) returns true and y.equals(z) returns true, then x.equals(z) should return true.
* It is consistent: for any non-null reference values x and y, multiple invocations of x.equals(y) consistently return true or consistently return false, provided no information used in equals comparisons on the objects is modified.
* For any non-null reference value x, x.equals(null) should return false.

#### [`@Override obj.equals(Object obj)`](https://www.technofundo.com/tech/java/equalhash.html)

```java
@Override // overrides Object equals() method (for my own objects definition)
public boolean equals(Object obj) {
        // reflexivity
        if(this == obj) { return true; } 
        // comparing apples and pears
        if((obj == null) || (obj.getClass() != this.getClass())) { return false; }
        // Can now safely cast Pair type onto obj
        Pair otherPair = (Pair) obj;
        // equal is x and y are equal
        return x == otherPair.get_x() && y == otherPair.get_y();
}

@Override 
public int hashCode() { 
    int hash = 7;
    return x * hash - y * hash;
}
```

#### [`@Override obj.hashCode(Object obj)`](https://www.technofundo.com/tech/java/equalhash.html)

> When we override `equals()`, it is recommended to also override the `hashCode()` method. If we don’t do so, equal objects may get different hash-values; and hash based collections, including *HashMap*, *HashSet*, and *Hashtable* do not work properly.

*Source: [Geekforgeeks](https://www.geeksforgeeks.org/overriding-equals-method-in-java/)*

```java
@Override 
public int hashCode() { 
    int hash = 7;
    return x * hash - y * hash;
}
```

#### [`getClass()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Object.html#getClass())

```java
public final Class<?> getClass()
```

Returns the runtime class of this Object.


#### [`toString()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Object.html#toString())

```java
public String toString()
```

Returns a string representation of the object.

In general, the toString method returns a string that "textually represents" this object:
- The result should be a concise but informative representation that is easy for a person to read. 
- It is recommended that all subclasses **override** this method.


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

#### [`s.compareTo(s2)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/String.html#compareTo(java.lang.String))

```java
public int compareTo(String anotherString)
```

Compares two strings lexicographically. The comparison is based on the Unicode value of each character in the strings. 

- **negative** integer: if `s` lexicographically precedes the argument string `s2`
- **positive** integer: if `s` lexicographically follows the argument string `s2`
- **0**: when the `s.equals(s2)` returns true.


### Class: [java.lang.StringBuilder](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/StringBuilder.html)

```java
public final class StringBuilder
extends Object
implements Serializable, Comparable<StringBuilder>, CharSequence
```

A **mutable** sequence of characters. The principal operations on a StringBuilder are the `append` (at end) and `insert` (at index) methods, which are overloaded so as to accept data of any type.

If `sb` refers to an instance of a StringBuilder, then `sb.append(x)` has the same effect as `sb.insert(sb.length(), x)`.

Use `sb.toString()` to convert the object into an immutable String.


#### Constructor: [`sb.StringBuilder()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#%3Cinit%3E()) [`sb.StringBuilder(String str)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#%3Cinit%3E(java.lang.String))

Constructs a string builder initialized to the contents of the specified string.

```java
StringBuilder sbEmpty = new StringBuilder();
StringBuilder sbExisting = new StringBuilder("Hello");
```


#### [`sb.toString()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#toString())

Returns a string representing the data in this sequence.


#### [`sb.append(Object obj)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#append(java.lang.Object))

Appends the string representation of the Object argument.

Exists with various methods signatures:

- [`append(boolean b)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#append(boolean)): Appends the string representation of the boolean argument to the sequence.
- [`append(char c)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#append(char)): Appends the string representation of the char argument to this sequence.
- [`append(double d)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#append(double)): Appends the string representation of the double argument to this sequence.
- [`append(float f)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#append(float)): Appends the string representation of the float argument to this sequence.
- [`append(int i)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#append(int)): Appends the string representation of the int argument to this sequence.
- [`append(long lng)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#append(long)): Appends the string representation of the long argument to this sequence.
- [`append(Object obj)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#append(java.lang.Object)): Appends the string representation of the Object argument.
- [`append(String str)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#append(java.lang.String)): Appends the specified string to this character sequence.


#### [`sb.delete(int start, int end)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html#delete(int,int))

Removes the characters in a substring of this sequence. The substring begins at the specified start and extends to the character at index end - 1 or to the end of the sequence if no such character exists. If start is equal to end, no changes are made.


#### [`sb.deleteCharAt(int index)`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/StringBuilder.html#deleteCharAt(int))

```java
public StringBuilder deleteCharAt(int index)
```

Removes the char at the specified position in this sequence. This sequence is shortened by one char.


#### [`sb.replace(int start, int end, String str)`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/StringBuilder.html#replace(int,int,java.lang.String))

```java
public StringBuilder replace​(int start, int end, String str)
```

Parameters:
- `start` - The beginning index, inclusive.
- `end` - The ending index, exclusive.
- `str` - String that will replace previous contents.


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


#### `lst.removeIf(predicate)`

See in Interface `Colletion<E>` method `c.removeIf(Predicate<?superE>filter)` in this doc.


#### [`lst.indexOf(Object o)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html#indexOf(java.lang.Object))

```java
public int indexOf(Object o)
```

Returns the index of the first occurrence of the specified element in this list, or -1 if this list does not contain the element.

### Class: [Scanner](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html)

A simple text scanner which can parse primitive types and strings using regular expressions.

A Scanner breaks its input into tokens using a delimiter pattern, which by default matches whitespace. The resulting tokens may then be converted into values of different types using the various next methods.

The default whitespace delimiter used by a scanner is as recognized by [`Character.isWhitespace()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Character.html#isWhitespace(int)). 

#### [Constructors](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html) 

- `Scanner(File source)`: Constructs a new Scanner that produces values scanned from the specified file.
- `Scanner(String source)`: Constructs a new Scanner that produces values scanned from the specified input stream.
- `Scanner(InputStream source)`: Constructs a new Scanner that produces values scanned from the specified string.
- (more available)

#### [`sc.useDelimiter(String pattern)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html#useDelimiter(java.lang.String))

Sets this scanner's delimiting pattern to a pattern constructed from the specified String.

```java
String input = "1 fish 2 fish red fish blue fish";
Scanner sc = new Scanner(input).useDelimiter("\\s*fish\\s*");
```

#### [`sc.close()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html#close())

Closes this scanner.

#### [`sc.hasNext()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html#hasNext()) variations

- sc.hasNextInt()
- sc.hasNextLine()
- [`sc.hasNext(String pattern)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html#hasNext(java.lang.String)): Returns true if the next token matches the pattern constructed from the specified string.


#### [`sc.next()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html#next())

Finds and returns the next complete token from this scanner.

- [`sc.next(String pattern)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html#next(java.lang.String)): Returns the next token if it matches the pattern constructed from the specified string.
- [`sc.nextInt()`]: Scans the next token of the input as an int.
- [`sc.nextLine()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html#nextLine()): Advances this scanner past the current line and returns the input that was skipped.




### Interface: [`Collection<E>`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Collection.html)

```java
public interface Collection<E>
extends Iterable<E>
```

The root interface in the collection hierarchy.


#### [`c.removeIf(Predicate<? super E> filter)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Collection.html#removeIf(java.util.function.Predicate))

Removes all of the elements of this collection that **satisfy the given predicate**.

For context, [`Interface Predicate<T>`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/function/Predicate.html) is a **functional interface** and can therefore be used as the assignment target for a **lambda expression** or method reference.

### Interface: [`Map<K,V>`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Map.html)

- An object that maps keys to values.
- A map cannot contain duplicate keys; 
- each key can map to at most one value. 


Type Parameters:
- `K`: the type of keys maintained by this map
- `V`: the type of mapped values

This interface takes the place of the Dictionary class, which was a totally abstract class rather than an interface.

### Class: [`HashMap<K,V>`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashMap.html)

```java
public class HashMap<K,V>
extends AbstractMap<K,V>
implements Map<K,V>, Cloneable, Serializable
```

This implementation provides constant-time performance for the basic operations (`get` and `put`), assuming the hash function disperses the elements properly among the buckets.

Useful methods: 
- `m.get(Object key)`
- `m.put(K key, V value)`
- `m.size()`
- `m.remove(Object key)`
- `m.clear()`
- `m.clone()`
- `m.containsKey(Object key)`
- `m.containsValue(Object value)`
- `m.entrySet()` returns `Set<Map.Entry<K,V>>`
- `m.keySet()` returns `Set<K>`

#### For each Map.Entry pair in entrySet()

```java
// HashMap<K, V> m = new HashMap();

for (Map.Entry<K, V> pair: m.entrySet()) {
    // pair.getKey()
    // pair.getValue();
}
```

Source: [zetcode.com](https://zetcode.com/java/hashmapiterate/)

#### Iterator over entrySet()

```java
// HashMap<K, V> m = new HashMap();

Iterator< Map.Entry<K, V> > it = items.entrySet().iterator();

while (it.hasNext()) {
    Map.Entry<K, V> pair = it.next();
    // pair.getKey()
    // pair.getValue();
}
```

Source: [zetcode.com](https://zetcode.com/java/hashmapiterate/)


### Interface: [`Set<E>`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Set.html)

```java
public interface Set<E>
extends Collection<E>
```

A collection that contains no duplicate elements. More formally, sets contain no pair of elements `e1` and `e2` such that `e1.equals(e2)`, and at most one `null` element.

All known implementing classes:
- AbstractSet
- HashSet
- LinkedHashSet
- TreeSet
- *more excl. for simplicity*


### Class: [`HashSet<E>`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html)

```java
public class HashSet<E>
extends AbstractSet<E>
implements Set<E>, Cloneable, Serializable
```

This class implements the *Set* interface, backed by a hash table (actually a *HashMap* instance). It makes no guarantees as to the iteration order of the set; in particular, it does not guarantee that the order will remain constant over time. This class permits the null element.


#### [`Set s = new Hashset()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html#%3Cinit%3E())

Constructs a new, empty set.


#### [`Set s = new HashSet(Collection<? extends E> c)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html#%3Cinit%3E(java.util.Collection))

Constructs a new set containing the elements in the specified collection `c`.


#### [`s.add(E e)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html#add(E))

```java
public boolean add(E e)
```

Adds the specified element to this set if it is not already present. 

If this set already contains the element, the call leaves the set unchanged and returns false.


#### [`s.clear()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html#clear())

```java
public void clear()
```

Removes all of the elements from this set. The set will be empty after this call returns.

#### [`s.clone()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html#clone())

```java
public Object clone()
```

Returns a **shallow copy** of this HashSet instance: the elements themselves are not cloned.


#### [`contains(Object o)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html#contains(java.lang.Object))

```java
public boolean contains(Object o)
```

Returns true if this set contains the specified element.


#### [`s.isEmpty()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html#isEmpty())

```java
public boolean isEmpty()
```

Returns true if this set contains no elements.


#### [`s.remove(Object o)`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html#remove(java.lang.Object))

```java
public boolean remove(Object o)
```

Removes the specified element from this set if it is present.

Returns true if this set contained the element (or equivalently, if this set changed as a result of the call).


#### [`s.size()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html#size())

```java
public int size()
```

Returns the number of elements in this set (its cardinality).

#### [`s.toArray()`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/HashSet.html#toArray())

```java
public Object[] toArray()
```

Returns an array containing all of the elements in this collection.

#### [`equals`]