To round off numbers, we can use the following methods
- toFixed()
- Math.round()
- generic rounding function

###### toFixed()
it's not accurate all the time

```js
var n = 1.0005;
n = n.toFixed(3);
console.log(n);
```

###### Math.round()
To limit, that is, round a number to n decimal places, use the built-in Math.round() function.

It still has issues like the previous method

For example, let’s round a number to 2 decimal places.

```js
var n = 2.781;
var rounded = Math.round(n * 100) / 100;
console.log(rounded);

```

Output:

2.78

###### Generic Rounding Function in JavaScript
Rounding with epsilon in JavaScript
In the previous example, you learned how to round numbers using Math.round() with number.EPSILON.

But the example only showed you how to round to 2 decimal places.

What if you want to round to n decimal places?

Let’s write a generic rounding function for that with these specifications:

- To round to 1 decimal, multiply by 10, round, and divide by 10 (10^1).
- For 2 decimals multiply and divide by 100 (10^2).
- For n decimals, multiply and divide by 10^n.
Let’s write a generic rounding function and extend the Number.prototype with it. This way you can call .round() on any numeric type in JavaScript.

```js
Number.prototype.round = function(n) {
  const d = Math.pow(10, n);
  return Math.round((this + Number.EPSILON) * d) / d;
}
// Example use:

1.005.round(2) // Returns 1.01
1.22.round(0)  // Returns 1

// Notice how this will also result in problems when rounding numbers close to the built-in floating-point accuracy.

// For instance:
1.32.round(16) // Returns 1.3200000000000003
```
