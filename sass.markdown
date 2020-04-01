## SASS:

### 1. intro
SASS compiler is needed to convert to css

features:
variables, nesting, partials n imports, mixins, extends, operators, functions, conditional directives, loops

syntaxs : sass(without curly and semicolons but with indentations), scss

sass-lang.com . sass opensource compiler => koala
or npm install

### 2. variables:
syntax:
```scss
$main-color : crimson
// starts with $ sign
```
### 3. nesting:
```scss
nav{
ul{}
li{}
a{
&:hover {}	//& is indicated to represent parent
		// as hover is part of a e.g a:hover

}
}
```
### 4. partials and imports:

_headers.scss // partial files
```scss
@import "headers" // no underscore or extensions
```
### 5. mixin:
```scss
.abc {
propa: 5px;
propb: 5px;
}

.xyz {
propa: 5px;
propb: 5px;
}
```
declaration:
```scss
@mixin declaredmixinname($val1, $value : 7px) { // assigning default value is optional
propa: $value;
propb: $value;

}
```

implementation:
```scss
.abc {
@include declaredmixinname(5px);
}
```

### 6. extends:
direct implementation
```scss
@extend // it will override same features

.abc {
propa: 5px;
propb: 5px;
}

.xyz {
propa: 5px; // overriding or new attributes
@extend .abc // copy attributes from .abc
}
```
//placeholder concept :
not real css declaration so no css of it will be created after compilation
```scss
%abc {	//% represeents placeholder
propa: 5px;
propb: 5px;
}

.xyz {
propa: 5px; // overriding or new attributes
@extend %abc // % is also used here to copy placeholder
}
```

### 7. operators:

five types of operators : equality, relational, numeric, string, boolean

equality and relationals : ==  != < > <= >=

e.g.
```scss
.abc {
padding : 19px >= 2s; // compilation error mismatch type
paddingb : 19px > 33px ;// true
paddingc : ariel == 'ariel' // true
paddingd :not ariel != 'ariel' // true
}
```
and or not :
e.g.
10px == 10px and arial == "arial"		//true

### 8. operators II:
```
+ // for string concatenation
- + * / % // math operators
```
```scss
button { 
  width: calc(200px / 2) 
}
```
lighten function , darken function
```scss
background-color: lighten($background-color, 20%);
```
### 9. interpolation.
```scss
#{} //is used in attribute name not in value
```
### 10. function:
A funtion will always have return value.
```scss
 @function func-name($val) {
	@return ($val/2) +px;
}
.half-width {
width : func-name($val);
}
```
### 11.  functions: 
datatypes : (boolean , null ) have no direct meaning in css but used in sass directives
<br />
rest datatypes : number, string, color, list, map
<br /> 
// few importants are listed not all
<br /> 
types of functions are : numbers, strings, colors, lists, maps ,selectors, introspection
<br /> 
numbers functions:
```
abs(),
percentage(100px/50px) = 200%,
comparable($a, $b) = true/false,
random() =  value from 0 to 1
random($val) where $val > 1 = abs value from $val to 1 == $val is the upper limit
unit(100em * 2px)  = em*px
unitless() = true/false
```
### 12. string functions:
```
unquote()
unique-id() = //random partial hashcode
```

### 13. colors:
```
mix()
transparentize()
lighten(), darken()
saturate(), desaturate()
adjust-hue()
```
### 14. list:
```scss
$listName : 10px 20px 30px;	//is-bracketed()  = false
$listName : [10px 20px 30px];	//is-bracketed()  = true
separations are : coma, space, auto

join()
zip($list1, $list2) = $list3 of same length, each ele clubbed
list-separator()
is-bracketed()  = true/false
```
### 15. selectors functions:
selector-nest, - append, -replace   <br /> 
selector-unify, -extend             <br /> 

is-superselector() = true/false // if first arg is ancestor of the second
<br /> 
simple-selectors

### 16. map functions:
```scss
$map1 : ("key1": val, "key2": val2)
```
map-get(), -merge(), -remove(), -keys(), -values(), -has-key()

### 17. introspection functions:
// to check if the sass declaration is present
<br />
variable, global-variable, mixin,function	 -exists()
<br /> 
type-of()

### 18. directives
content-directive: // like functional interface in java
```scss
@mixin{
@content	// always declare inside mixin then pass value during implementation
}

@include(){
//pass attributes with values here.
}
```
### 19. if else directives:
```scss
p{
@if $val<5 {
color : blue;
} @else {
color : red;
}
```
### 20. for directive
```scss
@for $var from $start through $end {
// use interpolation and var declaration to use it at best way possible
}
```
### 21. each directive:
is used to iterate over list or map
```scss
@each $val in $list1 {}

// for multi-dimensional
@each $val1, $val2, $val3 in $list{ 
//here 3 vals are each ele of $list has 3 eles
}

// for maps
@each $k, $v in $map1{}
```
### 22. while directive:
```scss
@while $val < 30 {


$val : $val + 10;
}
```
### 23.@media, @at-root

