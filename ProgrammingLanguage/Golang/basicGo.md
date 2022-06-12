# Go Programming Language



##### Basic Types

Go's basic types are:

```
bool

string

int int8 int16 int32 int64
uint uint8 uint16 uint32 uint64

byte // alias for uint8

rune // alias for int32 represents a Unicode code point

float32 float64

complex64 complex128
```

The `int`, `uint` and `uintptr` types are usually 32 bits wide on 32bit systems and 64 bits wide on 64-bit systems. When   you need an integer value you should use `int` unless you have a specific reason to use a sized or unsigned ingteger type.

Variables declared without an explicit initial value are given their `zero value`. The zero value is:

- 0 for numeric types
- false for the boolean type
- "" (the empty string) for strings



**Type conversions**: The expression `T(v)` converts the value `v` to type `T`

**Type inference**: When declaring a variable without specifying an explicit type (either by using the `:=` syntax or `var =` expression syntax), the variable's type is inferred from the value on the right hand side.

**Constants**: Constants are declared like variables, but with the `const` keyword. Constants can be character, string, boolean, or numeric values. Constants cannot be declared using the `:=` syntax.



##### Flow control

Go has only one looping construct, the `for` loop:

three components separated by semicolons:

- the init statement: executed before the first iteration
- the condition expression: evaluated before every iteration
- the post statement: executed at the end of every iteration

The init statement will often be a short variable declaration, and the variables declared there are visible only in the scope of the `for` statement.

`init statement` and `post statement` are optional.

**if statement**: `if` statement can start with a short statement to execute before the condition. Variables declared by the statement are only in scope until the end of the `if` 

**switch statement**: A `switch` statement is a shorter way to write a sequence of `if - else` statements. It runs the first case whose value is equal to the condition expression. Switch cases evaluate cases from top to bottom, stopping when a case succeeds.

**defer statement**: A defer statement defers the execution of a function until the surrounding function returns. 

​	The deferred call's arguments are evaluated immediately, but the function call is not executed until the surrounding function returns.

*stacking defers*: Deferred function calls are pushed onto a stack. When a function returns, its deferred calls are executed in LIFO order.

**Pointers**: Go has pointers, A pointer holds the memory address of a value. The type `*T` is a pointer to a `T` value, its zero value is `nil`

**Structurs**: A `struct` is a collection of fields, struct fields are accessed  using a dot. Struct fields can be accessed through a struct pointer.

​	Struct Literal: denotes as a newly allocated struct value by listing the values of its fields.

**Arrays**: The type `[n]T` is an array of `n` values of type `T`

**Slices**: array -> fixed size, slice -> dynamic Array. The type `[]T` is a slice with elements of type `T` . A slice is formed by specifying two indices, a low and high bound, separated by a colon. `a[low : high]` the default of low bound is zero

​	Slice does not store any data, it just describes a section of an underlying array. Changing the elements of a slice modifies the corresponding elements of its underlying array. Other slices that share the same array will see the changes.

A slice has both a `length` and a `capacity`. The length represents the number of elements slice contains, the capacity of a slice is the number of elements in the underlying array, counting from the first element in the slice.

Slices can be created with the built-in `make` function; this is how you create dynamically-sized arrays. The `make` function allocates a zeroed array and returns a slice that refers to that array:

```go
a := make([]int, 5) // len(a) = 5

b := make([]int, 0, 5) // len(b)=0, cap(b)=5
```

Range: two values are returned for each iteration, the first is the index and the second is a copy of the element at that index.



**Maps**: A map maps keys to values. The zero value of a map is `nil`. The `make` function returns a map of the given type, initialized and ready for use. Map literals are like struct literals, but the keys are required. If the top-level type is just a type name, you can omit it from the elements of the literal.

```go
package main

import "fmt"

type Vertex struct {
	Lat, Long float64
}

var m = map[string]Vertex {
	"Bell Labs": {40.68433, -74.39967},
	"Google":    {37.42202, -122.08408},
}

func main() {
	fmt.Println(m)
}
```

**Mutating Maps**:

insert or update an element in map `m` : `m[key] = ele`

Retrieve an element: `ele = m[key]`

Delete an element : `delete(m, key)`

Test that a key is present with a two-value assignment : `element, ok = m[key]`



**Function values**: Functions are values two. They can be passed around just like other values. Function values may be used as function arguments and return values.

```go
// function closure => A closure is a function 
// value that references variables from outside its
// body. The function may access and assign to the 
// referenced variabels.
import "fmt"

func adder() func(int) int {
	sum := 0
	return func(x int) int {
		sum += x
		return sum
	}
}
```



**Methods**: Define methods on types. A method is a function with a special receiver argument. 

The receiver appears in its own argument list between the `func` keyword and the method name.

Methods are functions, a method is just a function with a receiver argument.



**Pointer receivers**: declaring methods with pointer receivers. Methods with pointer receivers can modify the value to which the receiver points. 

**Pointers and functions**: While methods with pointer receivers take either a value or a pointer as a receiver when they are called. Functions that take a value argument must take a value of that specifc type. While methods with value receivers take either a value or a pointer as the receiver when they are called.

**Value or Pointer receiver**: 

​	Two reasons to use a pointer receiver:

- The method can modify the value that its receiver points to
- avoid copying the value on each method call.



##### Interfaces

An interface type is defined as a set of method signatures. A value of interface type can hold any value that implements those methods.



























