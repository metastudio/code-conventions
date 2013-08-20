# JS conventions (draft)

This document outlines the conventions we have at [MetaStudio](http://metastudiohq.com) for writing JavaScript code.

We always use pure JavaScript.

## Derived from

- http://contribute.jquery.org/style-guide/js/
- http://javascript.crockford.com/code.html
- https://github.com/rwaldron/idiomatic.js

## Idiomatic JS

This part is largely taken from https://github.com/necolas/idiomatic-css

- *Indentation :* 2 spaces
- *Line length :* 80 columns
- *Whitespaces :* configure your editor to "show invisibles" or to automatically remove end-of-line whitespace.
- *No whitespace at the end of line or on blank lines*
- *Never mix spaces and tabs*
- `if/else/for/while/try` always have braces and always go on multiple lines.
- Unary special-character operators (e.g., `!`, `++`) must not have space next to their operand.
- Any `,` and `;` must not have preceding space.
- Any `;` used as a statement terminator must be at the end of the line.
- Any `:` after a property name in an object definition must not have preceding space.
- The `?` and `:` in a ternary conditional must have space on both sides.
- No filler spaces in empty constructs (e.g., `{}`, `[]`, `fn()`)
- *New line at the end of each file.*

*Bad example*

```js

// Bad
if(condition) doSomething();
while(!condition) iterating++;
for(var i=0;i<100;i++) object[array[i]] = someFn(i);
```

*Goog example*

```js

var i = 0;

if ( condition ) {
  doSomething();
} else if ( otherCondition ) {
  somethingElse();
} else {
  otherThing();
}

while ( !condition ) {
  iterating++;
}

for ( ; i < 100; i++ ) {
  object[ array[ i ] ] = someFn( i );
}

try {
  // Expressions
} catch ( e ) {
  // Expressions
}
```


*TODO:*

- Unobtrusive JS - use classes
