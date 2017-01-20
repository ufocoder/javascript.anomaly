# Javascript Anomaly Page

This page created for javascript beginner programmers to show not obvious behaviors, let's call all of them "anomalies"

* [Assigment Anomaly](#assigment-anomaly)
* [Reference Anomaly](#reference-anomaly)
* [New Anomaly](#new-anomaly)
* [Closure Anomaly](#closure-anomaly)
* [Context Anomay](#context-anomaly)
* [Delete Anomaly](#delete-anomaly)
* [Type Anomaly](#type-anomaly)
* [Compare Anomaly](#compare-anomaly)
* [Math Anomaly](#math-anomaly)
* [Logic Anomaly](#logic-anomaly)
* [Variable scope Anomaly](#variable-scope-anomaly)
* [Function Arguments Anomaly](#function-arguments-anomaly)
* [toString Anomaly](#tostring-anomaly)
* [New line Anomaly](#new-line-anomaly)
* [Variable hoisting Anomaly](#variable-hoisting-anomaly)

### Assigment Anomaly

```
(function(){
  var a = b = 3;
})();

console.log(typeof a);
// output: undefined

console.log(typeof b);
// output: number


var a={},
    b={key:'b'},
    c={key:'c'};

a[b]=123;
a[c]=456;

console.log(a[b]);
// output: 456
```

### Reference Anomaly

```
var a = { value: 1 };
var b = a;
b.value = 2;

console.log(a.value);
// output: 2
```

### New Anomaly 

```
var myClass = function() {
  this.a = 1;
  this.b = 2;
};

var myClass2 = function() {
  this.a = 1;
  this.b = 2;

  return {
    a: 2
  };
};

var myObject = new myClass();
var myObject2 = new myClass2();

console.log(typeof myObject.b);
// output: number
console.log(typeof myObject2.b);
// output: undefined
```

### Closure Anomaly
```
for (var i = 0; i < 3; i++) {
  setTimeout(function() {
    console.log(i);
  }, 100);
}

// output: 3
// output: 3
// output: 3
```

### Context Anomaly

```
var message = {
  content: 'Hello world!',
  send: function () {
    console.log(this.content)
  }
};

setTimeout(message.send);

// output: undefined
```

### Delete Anomaly

```
var x = 1;
var output = (function(){
  delete x;
  return x;
})();

console.log(output);
// output: 1
```


### Type Anomaly

```
console.log(typeof null);
// output: object


console.log(null instanceof Object);
// output: false

console.log(typeof NaN);
// output: number

console.log(typeof function () {});
// output: function
// but there's no function type http://ecma-international.org/ecma-262/5.1/#sec-8
```


### Compare Anomaly


```
console.log('' == '0');
// output: false

console.log(0 == '');
// output: true

console.log(0 == '0');
// output: true

console.log(false == 'false');
// output: false

console.log(false == '0');
// output: true

console.log(false == undefined);
// output: false

console.log(false == null);
// output: false

console.log(null == undefined);
// output: true

console.log(' \t\r\n ' == 0);
// output: true

console.log("abc" == new String("abc"));
// output: true

console.log("abc" === new String("abc"));
// output: false

console.log(0.1 + 0.2 == 0.3);
// output: false
// sum of float values is not equals obvious float value

console.log(NaN != NaN);
// output: true

console.log(NaN == NaN);
// output: false

console.log(NaN === NaN);
// output: false

console.log(!!undefined);
// output: false

console.log(!!NaN);
// output: false

console.log(!!null);
// output: false

console.log([1, 2, 3] == [1, 2, 3]);
// output: false
// How to detect array equality in JavaScript?

console.log(new Array(3) == ",,");
// output: true

console.log(new Array(3) === ",,");
// output: false

console.log("a" > "b");
// output: false

console.log("abcd" < "abcd");
// output: false

console.log("abcd" < "abdc");
// output: true

console.log("123" > "13");
// output: false
```


### Math Anomaly

```
console.log("2" * "3");
// output: 6

console.log("2" * "3" + "4");
// output: "64"

console.log("2" * "3" + "4" * "5")
// output: 26

console.log("test " + 1);
// output: test 1

console.log("test " + 1 + 1);
// output: test 11

console.log("days" * 2);
// output: NaN

console.log(null + null);
// output: 0

console.log({} + {});
// output: [object Object][object Object]

console.log({} + []);
// output: [object Object]

console.log({} + 5);
// output: [object Object]5

console.log([] + {});
// output: [object Object]

console.log([] + []);
// output:
// will output empty string ''

console.log([] + 5);
// output: 5
```

### Logic Anomaly

```
console.log(0 || 'a');
// output: a

console.log(0 || undefined);
// output: undefined

console.log({} && 'a');
// output: a

console.log(0 && 'a');
// output: 0
```

### Variable scope Anomaly

```
function Foo(value) {
    this.bar = value;
}
var test = new Foo('test');
console.log(test.bar);
// output: test

Foo('test');
console.log(bar);
// output: test
```


### Function Arguments Anomaly

```
(function (foo, bar) {
    console.log(typeof arguments);
    // output: object

    arguments[0] = 999;
    console.log(foo);
    // output: 999
})(1, 2);
```


### toString Anomaly

```
try {
    eval("2.toString()")
} catch (err) {
    console.log(err.message)
    // output: Unexpected token ILLEGAL
}

console.log(2..toString());
// output: 2

console.log(2 .toString());
// output 2

console.log((2).toString());
// output: 2

console.log([1, 2, 3].toString())
// output: 1,2,3

var a = {b: 2, c: 3};
console.log(a.toString())
// output: [object Object]
```

### New line Anomaly

```
function foo() {
  return "Yeah";
}
 
function bar() {
  return 
    "Yeah";
}

console.log(foo());
// output: Yeah

console.log(bar());
// output:
```

### Variable hoisting Anomaly

```
var a = 1; 
function bar() { 
    if (!a) { 
        var a = 10; 
    } 
    console.log(a); 
} 
bar();
// output: 10
```

```
var a = 1;
function b() {
    a = 10;
    return;
    function a() {}
} 
b(); 
console.log(a);
// output: 1
```

Note that `anomaly` word has only literary turnover, it's not a technical term.
