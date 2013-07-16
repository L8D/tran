Tran
====
Tran is a programming language inspired by ternary operators like `?:`. Besides a standard library for interfacing with `std{in,out}` and such, the entire language consists of no "words".

So far, I have yet to actually make an interpreter or copmiler for it, but it's *so far* rules are as follows with example output code in Javascript.

### Code blocks
In most cases when you see a simple set of `{}`s it means something like: `function(){ ... }()` in order to compress that block down to one instruction.

### If, else if, and else
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
