# Generators function

`yield` a keyword only valid in generator function

a generator function give a generator object to use.

`next()` : execute the generator function into next state.

```
{
	done property
	value property
}
```

we can have mutiple generator object. Each generator object are isolated each other.

`return` : exit the generator



we can create infinity loop in generator function.

1. create infinite loop

2. Iterator

   ```javascript
   function* arrayIterator(arr) {
   	for (let i = 0; i < arr.length; i++) {
   		yield arr[i]
   	}
   }
   ```

   





