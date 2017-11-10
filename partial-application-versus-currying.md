### Partial application

Partially applied function will execute the body regardless of whether you supplied the required arguments or not.
Its not smart as curried functions, which keep returns function until all arguments are supplied

```js
const add = (a, b, c) => a + b + c;
```

**Example of partially applied function:**

```js
const add1 = add.bind(null, 1);
add1() // result NaN
// The function executes even if not all the arguments are supplied, the result is NaN because we are trying to do this : 1 + undefined + undefined which results to NaN
add1(2);
// result still will be NaN -> 1 + 2 + undefined = NaN
add1(2, 3)
// result will be 6 - we finally supplied all the arguments
```
<hr />

To demonstrate above example without using 'bind' function for binding first argument, we could write something like that:

```js
const add1Example = (b, c) => add(1, b, c);
const add2Example = (c) => add1Exmaple(2, c); // or add(1, 2, c);
add2Example(3);
```

## Curried function

Takes multiple arguments and translates them into sequence of functions, each with a single argument. The curried function is only executed when all arguments are supplied.

```js
const curriedAdd = (a) => (b) => (c) => a + b + c;

const res = curriedAdd(1)(2)(3);
console.log('curried', res);
```

## Difference between partial application and currying

*Short explanation:*
The massive difference between them two: is that partial application will always execute no matter if you supplied all the arguments while curried function only executes when you supplied all the arguments! Partial application is not smart enough as currying!

*Longer explanation:*
They're closely related but different things.
They're both about filling in arguments and returning a new function with the
remaining arguments. The difference is that a curried function is smart
enough to keep returning functions that need the remaining arguments until
everything is provided, and a partially applied function is not (ie: the next
function call will evaluate the body of the function regardless of whether you
supplied the required arguments or not).
