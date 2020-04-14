# Variable

```js
// This is comment for javascript
var x = 10;
document.write(x);
var x = 'Variable of JS';
document.write(x);
```

# Boolean and Logic Operator

```js
var age = 16;
var result = null;
if (age >= 20) {
  result = 'Adult';
} else {
  result = 'Minor';
}
document.write(result);

var age = 65;
var isMember = true;
var result = null;
if (age >= 60 && isMember) {
  result = 'You are eligible for a senior membership discount.';
} else {
  result = 'You are NOT eligible for a senior membership discount';
}
document.write(result);
```

# for Loop

```js
// Type declaration is not required?
for (i = 1; i < 101; i++) {
  document.write(i % 15 ? i % 3 ? i % 5 ? i : 'Buzz' : 'Fizz' : 'FizzBuzz');
}
```
