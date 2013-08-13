# SASS conventions (draft)

This document outlines the conventions we have at [MetaStudio](http://metastudiohq.com) for writing CSS code.

We always use SASS with SCSS syntax.

## Derived from

- https://github.com/lewattman/sass-conventions
- https://github.com/necolas/idiomatic-css
- https://github.com/anthonyshort/idiomatic-sass
- https://github.com/sturobson/a-slightly-bizarre-starting-point

## Idiomatic CSS

This part is largely taken from https://github.com/necolas/idiomatic-css

- *Indentation :* 2 spaces
- *Line length :* 80 columns
- *Whitespaces :* configure your editor to "show invisibles" or to automatically remove end-of-line whitespace.
- *Comments :* Always use ```//``` SASS comments, they will not be outputed. Use regular comment if you have a good reason
- *Format :*
  - Use one discrete selector per line in multi-selector rulesets.
  - Include one declaration per line in a declaration block.
  - Include a single space after the colon of a declaration.
  - Use lowercase and shorthand hex values, e.g., #aaa.
  - Use (single or) double quotes consistently. Preference is for double quotes, e.g., content: "".
  - Quote attribute values in selectors, e.g., input[type="checkbox"].
  - Where allowed, avoid specifying units for zero-values, e.g., margin: 0.
  - Include a space after each comma in comma-separated property or function values.
  - Include a semi-colon at the end of the last declaration in a declaration block.
  - Place the closing brace of a ruleset in the same column as the first character of the ruleset.


## Naming convention

- .only-hyphens
- #only_underscores


## Colors

```css

// literal colors
$black: #000;
$bgColor: #f0fafe;

.selector {
  color: #ccaaff;
  border-color: $black;
  background-color: $bgColor;
}
```

## Properties

### Ordering

Taken from https://github.com/necolas/idiomatic-css

Blocks:

0. Positioning
1. Display & Box Model
2. Other

Each block should contain rules with the next order:

1. rules
2. @extend directives
3. @include directives


```css
.selector {
  position: absolute;
  z-index: 10;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  @include zeroPosition;
  display: inline-block;
  overflow: hidden;
  box-sizing: border-box;
  width: 100px;
  height: 100px;
  padding: 10px;
  border: 10px solid #333;
  margin: 0;
  @extend .some-class;
  @include borderRadius(4px);
  background: #000;
  color: #fff;
  font-family: sans-serif;
  font-size: 16px;
  text-align: right;
  text-transform: lowercase;
}
```

### Mixins

Taken from https://github.com/anthonyshort/idiomatic-sass#mixins

- Mixins should only be used when there are dynamic properties, otherwise use @extend
- Mixins that output selectors should be capital-case: @mixin GridBuilder
- Mixins that output only properties should be camel-case: @mixin borderBox
- In general, mixins with logic should not be longer than ~50 lines just like any other programming language
- Private mixins that are not used outside of the current file should be prefixed with a dash: @mixin -gridHelper
- Avoid using more than 4 parameters. It is a sign that a mixin is too complex. When Sass adds hashes life will be - easier.
- Mixins should be documented



```css

// Add transition effect. Usage: @include trasition(all, 1s, ease-in-out);
@mixin transition($property, $duration:0.3s, $function: ease-out) {
  -moz-transition: $property $durations $function; /* FF3.7+ */
  -o-transition: $property $durations $function; /* Opera 10.5 */
  -webkit-transition: $property $durations $function; /* Saf3.2+, Chrome */
  transition: $property $durations $function;
}

.popup {
  position: fixed;
  z-index: 5;
  left: 0px;
  top: 0px;
  display: block;
  width: 100%;
  height: 100%;
  opacity: 1;
  @include transition(all, 1s, ease-in-out)
  background: #f5f0f5 url('/images/bg.png') repeat -40% 0;
  font-style: italic;
  text-align: left;
  &.incompleted {
    left: 100%;
    right: inherit;
    display: block;
    color: #f00;
  }
  &:hover {
    color: #fff;
  }
  p > .note {
    color: #ccc;
  }
}

```
