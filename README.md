Tran
====
Tran is a programming language inspired by ternary operators like `?:`. Besides a standard library for interfacing with `std{in,out}` and such, the entire language consists of no "words".

So far, I have yet to actually make an interpreter or copmiler for it, but it's *so far* rules are as follows with example output code in Javascript.

### Code blocks
In most cases when you see a simple set of `{}`s it means something like: `function(){ ... }()` in order to compress that block down to one instruction.

### If, else if, and else (?:)
Conditional statements are only ternary conditional expressions.

``` javascript
bool ? {
  // code for if bool is true
} : another_bool ? {
  // code for if another_bool is true
} : {
  // code for if neither another_bool nor bool are true
}
```
This converts to:
``` javascript
if(bool) {
  // code for if bool is true
} else if(another_bool) {
  // code for if another_bool is true
} else {
  // code for if neither another_bool nor bool are true
}
```

### Functions (->)
Functions in tran almost mock coffeescript. Also the `return` keyword is `<-`.
``` javascript
function_name = (parameters) -> {
  -> return_value;
}
```
Converts(although akwardly) to:
``` javascript
var function_name = function(parameters) {
  return return_value;
}
```

### Objects (={})
Objects in Tran are very closely like javascript objects, although instead of using `:`s for defining attributes, it simply just uses the standard `=`.
``` javascript
object_name = {
  method_name = (-><- "returned value from the method";),
  attribute = 10
}

object_name.attribute // returns 10
object_name.method_name() // returns "returned value from the method"
```
Will look like:
``` javascript
object_name = {
  "method_name": function() { return "returned value from the method"; },
  "attribute" = 10
}

object_name.attribute // returns 10
object_name.method_name() // returns "returned value from the method"
```

### Loops and Breaks (^ /)
Because anything other than while loops are for sissies.
```
bool ^ {
  // will be rerun until bool == false or loop is broken
  some_condition ? /;
}
```
to...
``` javascript
while(bool) {
  // will be rerun until bool == false or loop is broken
  if(some_condition) break;
}
```

### Switch and Case (?&:)
Its a little finicky to explain like this, so I'll let you read the code...But basically: `?&` is one operator, no spaces in-betweeen.
``` javascript
some_var ?& {
  "foo": /* some_var is "foo"! */ /;
  "bar": /* some_var is "bar"! */ /;
  : /* some_var is neither "foo" or "bar"... */;
}
```
in javascript:
``` javascript
switch(some_var) {
  case "foo": /* some_var is "foo"! */ break;
  case "bar": /* some_var is "bar"! */ break;
  default: /* some_var is neither "foo" or "bar"... */
}
