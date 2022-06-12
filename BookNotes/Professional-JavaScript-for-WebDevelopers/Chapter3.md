# Chapter 3: Language Basics





**Case-Sensitivity**: a variable named `test` is different from a variable named `Test`



**Identifiers**: An `identifier` is the name of a variable, function, property or function argument. Identifiers may be one or more characters in the following format:

- the first character must a letter, an underscore (_) or a dollar sign ($)
- All other characters may be letters, underscores, dollar signs or numbers

Letters in an identifier may include extended ASCII or Unicode letter characters 

By convention, ECMAScript identifiers use camel case, meaning that the first letter is lowercase and each additional word is offset by a capital letter



**Comments**:

```javascript
// 

&&

/** */
```

 

**Strict Mode**: 

Strict mode is a different parsing and execution model for JavaScript where some of the erratic behavior of ES3 is addressed and errors are thrown for unsafe activities. To enable strict mode for an entire script, include the following at the top:

```javascript
"use strict" // a pragma that tells supporting JavaScript engines to change into strict mode.
```

**Statement**

Statements in ECMAScript are terminated by a semicolon, though omitting the semicolon makes the parser determine where the end of a statement occurs

Multiple statements can be combined into a code block by beginning with a left curly brace and ending with a right curly brace.



##### Variables

**var**:

- Declaration Scope -> function scoped: using the `var` operator to define a variable makes it local to function scope in which it was deifned. For example, defining a variable inside of a function using `var` means that the variable is destroyed as soon as the function exits.
- Declaration Hoisting: variables declared using var keyword are hoisted to the top of the function scope. basically, print undefined.The interpreter pulls all variable declarations to the top of its scope. It also allows you to use redundant var declarations without penalty.

**let**:

- `let` is block scoped, variables cannot be referenced outside the block. Block scope is strictly a subset of function scope.
- redundant declarations within a block scope is not allowed.
- Temporal Dead Zone: `let` declarations cannot be used in a way that assumes hoisting. Any attempted references to these varaibles will throw a referenceError
- Unlike the var keyword, when declaring variables using let in the global context, variables will not attach to the window object as they do with var.  `let` declarations will still occur inside the global block scope, which will persist for the lifetime of the page.
- `for` loop definition: When using var, a frequent problem encountered was the singular declaration and modification of the iterator variable



When using var to declare variables, because the declaration is hoisted, the JavaScript engine will happily combine redundant declarations into a single declaration at the top of the scope. Because let declarations are scoped to blocks, it’s not possible to check if a let variable has previously been declared and conditionally declare it only if it has not. 



**const**:

- const behaves identically to that of let but with one important difference—it must be initialized with a value, and that value cannot be redefined after declaration. Attempting to modify a const variable will result in a runtime error.
- The const declaration is only enforced with respect to the reference to the variable that it points to. If a const variable references an object, it does not violate the const constraints to modify properties inside that object.



##### Data Types

**Primitive Types**: undefined, null, boolean, number, string, symbol, bigint.

**Complex Data Type**: Object (an unordered list of name-value pairs)



**undefined:**

```javascript
let message; // this variable is declared but has a value of undefined
// 'age' is not declared
if (message) {
 // This block will not execute
}
if (!message) {
 // This block will execute
}
if (age) {
 // This will throw an error
}
```

**null**:

```javascript
let message = null;
let age;
if (message) {
 // This block will not execute
}
if (!message) {
 // This block will execute
}
if (age) {
 // This block will not execute
}
if (!age) {
 // This block will execute
}
```



| Data Type | Values Converted to True              | Values Converted to False |
| --------- | ------------------------------------- | ------------------------- |
| Boolean   | true                                  | false                     |
| String    | Any nonempty string                   | empty string              |
| Number    | Any nonzero number (include infinity) | 0, NaN                    |
| Object    | Any Object                            | null                      |
| Undefined |                                       | undefined                 |



**The Number Type**:

IEEE-754 format to represent both integers and floating-point values.

Integers can also be represented as either base 8 or base 16 literals. 

Because storing floating-point values uses twice as much memory as storing integer values, ECMAScript always looks for ways to convert values into integers. When there is no digit after the decimal point, the number becomes an integer

The smallest number that can be represented in ECMAScript is stored in Number.MIN_VALUE and is 5e–324 on most browsers; the largest number is stored in Number.MAX_VALUE and is 1.7976931348623157e+308 on most browsers. 

Floating-point can be represented using `e-notation`

Floating-point values are accurate up to 17 decimal places but are far less accurate in arithmetic computations than whole numbers

**NaN**: Not a Number is used to indicate when an operation intended to return a number has failed.



**String Type**:

Strings are immutable in ECMAScript, meaning that once they are created, their values cannot change. To change the string held by a variable, the original string must be destroyed and the variable filled with another string containing a new value.

**Template String**:

- template literals are especially useful when defining templates, such as HTML

- Template literals also support the ability to define tag functions, which are able to define custom interpolation behavior. The tag function is passed the individual pieces after the template has been split by the interpolation token and after the expressions have been evaluated.



**Symbol Type**:

Symbols are primitive values, and symbol instances are unique and immutable. The purpose of a symbol is to be a guaranteed unique identifier for object properties that does not risk property collision.

symbols are intended to be used as unique tokens that can be used to key special properties with something other than a string.

**Global Symbol Registry**: In scenarios where different parts of the runtime would like to share and reuse a symbol instance, it is possible to create and reuse symbols in a string-keyed global symbol registry. This behavior can be achieved using Symbol.for()

Symbols defined in the global registry are totally distinct from symbols created using Symbol(), even if they share a description:

It is possible to check against the global registry using Symbol.keyFor(), which accepts a symbol and will return the global string key for that global symbol, or undefined if the symbol is not a global symbol.



**Using Symbols as Properties**: Anywhere you can normally use a string or number property, you can also use a symbol. This includes object literal properties and Object.defineProperty()/Object.defineProperties(). An object literal can only use a symbol as a property inside the computed property syntax.

**Well-known Symbols**: would be used throughout the language to expose internal language behaviors for direct access, overriding, or emulating. These well-known symbols exist as string properties on the Symbol factory function.

Each well-defined symbol property is non-writeable, non-enumerable, and non-configurable.





##### The Object Type









