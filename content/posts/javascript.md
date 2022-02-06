---
title: "🤷‍♂️ JavaScript and TypeScript (noob notes)"
date: 2022-02-05T12:00:00+01:00
draft: true
showtoc: true
tags: ["javascript", "noob notes"]
---

- [JavaScript References by Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript#reference)
- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [RealPython: Python vs JavaScript for Pythonistas](https://realpython.com/python-vs-javascript/)


## Formatting and style

### Indentation


### Naming


## Loops

### for


## TypeScript

> We recommend learning a little bit of JavaScript without types first to understand JavaScript’s runtime behaviors. [...] TypeScript uses the same runtime as JavaScript, so any resources about how to accomplish specific runtime behavior (converting a string to a number, displaying an alert, writing a file to disk, etc.) will always apply equally well to TypeScript programs.

Source: [TypeScript Docs](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes-oop.html)

OOP in TypeScript

> C# and Java are what we might call mandatory OOP languages. In these languages, the class is the basic unit of code organization, and also the basic container of all data and behavior at runtime.

> In JavaScript, functions can live anywhere, and data can be passed around freely without being inside a pre-defined class or struct. Free” functions (those not associated with a class) working over data without an implied OOP hierarchy tends to be the preferred model for writing programs in JavaScript.

Rethinking Types

> In C# or Java, any given value or object has one exact type - either null, a primitive, or a known class type. In C# or Java, it’s meaningful to think of a one-to-one correspondence between runtime types and their compile-time declarations.

> In TypeScript, it’s better to think of a type as a _set_ of values that share something in common. Because types are just sets, a particular value can belong to many sets at the same time. How do you describe a value that either belongs in the string set or the number set? It simply belongs to the union of those sets: `string | number`.
> 
> In TypeScript, objects are not of a single exact type. For example, if we construct an object that satisfies an interface, we can use that object where that interface is expected even though there was no declarative relationship between the two. TypeScript’s type system is _structural_, not nominal: We can use `obj` as a `Pointlike` because it has `x` and `y` properties that are both numbers. **The relationships between types are determined by the properties they contain, not whether they were declared with some particular relationship**.


```js
// Example
interface Pointlike {
  x: number;
  y: number;
}
interface Named {
  name: string;
}
 
function logPoint(point: Pointlike) {
  console.log("x = " + point.x + ", y = " + point.y);
}
 
function logName(x: Named) {
  console.log("Hello, " + x.name);
}
 
const obj = {
  x: 0,
  y: 0,
  name: "Origin",
};
 
logPoint(obj);
logName(obj);
```

Surpises with TS: Empty types

> We can see that { k: 10 } has all of the properties that Empty does, because Empty has no properties. Therefore, this is a valid call

```js
class Empty {}
 
function fn(arg: Empty) {
  // do something?
}
 
// No error, but this isn't an 'Empty' ?
fn({ k: 10 });
```

### TypeScript Handbook

- [ ] Read [about page](https://www.typescriptlang.org/docs/handbook/intro.html) on handbook (3min)