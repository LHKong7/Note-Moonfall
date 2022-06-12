### JavaScript



1.丢弃小数部分,保留整数部分  : `parseInt(7/2) `

2.向上取整,有小数就整数部分加1 `Math.ceil(7/2)` 

3,四舍五入. `Math.round(7/2) `

4,向下取整 `Math.floor(7/2)`

都是JS内置对象

javascript除法如何取整
Math.round(x) 四舍五入，如Math.round(0.60)，结果为1；Math.round(0.49)，结果为0；
Math.floor(x) 向下舍入，如Math.floor(0.60)与Math.floor(0.49)，结果均为0；
Math.ceil(x)向上舍入，如Math.ceil(0.60)与Math.ceil(0. 49)，结果均为1。



##### Array:

Shallow Copy:

- spread sequence `let shallowCopySpread = [...array]`
- Array.slice() : `let shallowCopySlice = array.slice()`
- Array.from() : `let shallowCopyFrom = Array.from(array)`

**Static Methods**:

- `Array.isArray()`
- `Array.from()`

**Instance Methods**:

- `Array.prototype.concat` : Return a new array that is this array joined with other array(s) and/or value(s).



Used as Queue (FIFO):

- `push()` : Adds one or more elements to the end of an array, and returns the new `length` of the array.
- `shift()`: Removes the first element from an array and returns that element.



Used as Stack (LIFO) :

- `push()`
- `pop()`: Removes the last element from an array and returns that element.



[`Array.prototype.reduce()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) Apply a function against an accumulator and each value of the array (from left-to-right) as to reduce it to a single value.

[`Array.prototype.sort()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort): Sorts the elements of an array in place and returns the array.

[`Array.prototype.slice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) : Extracts a section of the calling array and returns a new array.

[`Array.prototype.map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) : Returns a new array containing the results of calling a function on every element in this array.

[`Array.prototype.reverse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) : Reverses the order of the elements of an array *in place*. (First becomes the last, last becomes first.)

[`Array.prototype.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter): Returns a new array containing all elements of the calling array for which the provided filtering function returns `true`.

[`Array.prototype.find()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find) : Returns the found `element` in the array, if some element in the array satisfies the testing function, or `undefined` if not found.

[`Array.prototype.includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) :Determines whether the array contains a value, returning `true` or `false` as appropriate.

##### String

**Static Methods**:

[`String.fromCharCode(num1 [, ...[, numN\]])`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode) : Returns a string created by using the specified sequence of Unicode values.

**Instance Methods**:

[`String.prototype.charAt(index)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)Returns the character (exactly one UTF-16 code unit) at the specified `index`.

`String.prototype.includes(searchString [, position\])` : Determines whether the calling string contains `searchString`.

`String.prototype.indexOf(searchValue [, fromIndex\])`  : Returns the index within the calling [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) object of the first occurrence of `searchValue`, or `-1` if not found.

`String.prototype.substring(indexStart [, indexEnd\])` : Returns a new string containing characters of the calling string from (or between) the specified index (or indices).

`String.prototype.slice(beginIndex[, endIndex\])` : Extracts a section of a string and returns a new string.

##### Map

The **`Map`** object holds key-value pairs and remembers the original insertion order of the keys. Any value (both objects and [primitive values](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)) may be used as either a key or a value.

A `Map` object iterates its elements in insertion order — a [`for...of`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of) loop returns an array of `[key, value]` for each iteration.



**Key Equality**:

- Key equality is based on the [`sameValueZero`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness#same-value-zero_equality) algorithm.
- [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) is considered the same as `NaN` (even though `NaN !== NaN`) and all other values are considered equal according to the semantics of the `===` operator.
- In the current ECMAScript specification, `-0` and `+0` are considered equal, although this was not so in earlier drafts. See *"Value equality for -0 and 0"* in the [Browser compatibility](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map#browser_compatibility) table for details

[`Object`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) is similar to `Map`—both let you set keys to values, retrieve those values, delete keys, and detect whether something is stored at a key. For this reason (and because there were no built-in alternatives), `Object` has been used as `Map` historically.



```javascript
const contacts = new Map()
contacts.set('Jessie', {phone: "213-555-1234", address: "123 N 1st Ave"})
contacts.has('Jessie') // true
contacts.get('Hilary') // undefined
contacts.set('Hilary', {phone: "617-555-4321", address: "321 S 2nd St"})
contacts.get('Jessie') // {phone: "213-555-1234", address: "123 N 1st Ave"}
contacts.delete('Raymond') // false
contacts.delete('Jessie') // true
console.log(contacts.size) // 1
```



[`Map.prototype.clear()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/clear) Removes all key-value pairs from the `Map` object.

[`Map.prototype.delete(key)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/delete) Returns `true` if an element in the `Map` object existed and has been removed, or `false` if the element does not exist. `Map.prototype.has(key)` will return `false` afterwards.

[`Map.prototype.get(key)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/get) Returns the value associated to the `key`, or `undefined` if there is none.

[`Map.prototype.has(key)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/has) Returns a boolean asserting whether a value has been associated to the `key` in the `Map` object or not.

[`Map.prototype.set(key, value)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map/set) Sets the `value` for the `key` in the `Map` object. Returns the `Map` obje





##### Set

The **`Set`** object lets you store unique values of any type, whether [primitive values](https://developer.mozilla.org/en-US/docs/Glossary/Primitive) or object references.

`Set` objects are collections of values. You can iterate through the elements of a set in insertion order. A value in the `Set` **may only occur once**; it is unique in the `Set`'s collection.



**Instance Methods**:

[`Set.prototype.add(value)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/add) Appends `value` to the `Set` object. Returns the `Set` object with added value.

[`Set.prototype.clear()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/clear) Removes all elements from the `Set` object.

[`Set.prototype.delete(value)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/delete) Removes the element associated to the `value` and returns a boolean asserting whether an element was successfully removed or not. `Set.prototype.has(value)` will return `false` afterwards.

[`Set.prototype.has(value)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/has) Returns a boolean asserting whether an element is present with the given value in the `Set` object or not.



[`Set.prototype.keys()` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set/values)

与**`values()`**方法相同，返回一个新的迭代器对象，该对象包含`Set`对象中的按插入顺序排列的所有元素的值。

[`Set.prototype.values()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set/values)

返回一个新的迭代器对象，该对象包含`Set`对象中的按插入顺序排列的所有元素的值。





