# Javascript Anomaly Page

This page created for javascript beginner programmers to show not obvious behaviors, let's call all of them "anomalies"


### Assigment anomaly

```
(function(){
  var a = b = 3;
})();

console.log(typeof a);
// output: undefined

console.log(typeof b);
// output: number
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
// sum of float values is not equeals obvious float value

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
// output: true

console.log("abcd" < "abcd");
// output: false

console.log("abcd" < "abdc");
// output: true
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

Note that `anomaly` word has only literary turnover, it's not a technical term.
