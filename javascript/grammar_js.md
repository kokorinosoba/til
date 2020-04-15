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
  document.write(i % 15 ? i % 3 ? i % 5 ? i + ' ' : 'Buzz ' : 'Fizz ' : 'FizzBuzz ');
}
```

# Array

```js
var classes = ['A', 'B', 'C', 'D'];
console.log(classes);

var a = [];
console.log(a);
console.log(a.length);
a.push('X');
console.log(a);
console.log(a.length);
a.push('Y');
console.log(a);
console.log(a.length);

for (var grade = 1; grade < 4; grade++) {
  for (var i = 0 ; i < classes.length; i++) {
    document.write('<p>' + 'Grade' + grade + 'Class' + classes[i] + '</p>');
  }
}

kanas = 'あいうえおかきくけこ';
for (var i = 0; i < kanas.length; i++) {
  for (var j = 0; j < kanas.length; j++) {
    document.write('<p>' + kanas[i] + kanas[j] + '</p>');
  }
}
```

# Naming Rules

- Lower Camel Case

# Function

```js
// on Console
function logDate() {
  console.log(new Date());
}

logDate();
```

## Animation using Function

```html
<!-- js-function.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>JavaScript Function</title>
  </head>
  <body>
    <p id="birth-time"></p>
    <script src="function.js"></script>
  </body>
</html>
```

```js
// function.js
var myBirthTime = new Date(1982, 11, 17, 12, 30);
function updateParagraph() {
  var now = new Date();
  var seconds = (now.getTime() - myBirthTime.getTime()) / 1000;
  document.getElementById('birth-time').innerText = seconds + 'seconds passed from your birth';
}
setInterval(updateParagraph, 50);
```

# Object

```js
var student = {
  name: 'Taro',
  age: 15
};

// Omit values
var age = 13;
var student = {
  name: 'Jiro',
  age
};

console.log(student.name);
console.log(student.age);

var counter = {
  number: 0,
  print: function() {
    counter.number++;
    console.log(counter.number);
  }
}
counter.print();
counter.print();
counter.print();
```

```html
<!-- js-object.html  -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>JavaScript Object</title>
  </head>
  <body>
    <h1 id="display-area"></h1>
    <script src="object.js"></script>
  </body>
</html>
```

```js
// object.js
var game = {
  startTime: null,
  displayArea: document.getElementById('display-area')
};

function start() {
  game.startTime = Date.now();
  document.body.onkeydown = stop;
}

function stop() {
  var currentTime = Date.now()
  var seconds = (currentTime - game.startTime) / 1000;
  if (9.5 < seconds && seconds < 10.5) {
    displayArea.innerText = seconds + 'seconds. You are great!';
  } else {
    displayArea.innerText = seconds + 'seconds...';
  }
}

if (confirm('Press OK and when you think you have 10 seconds, press any key.')) {
  start();
}
```
