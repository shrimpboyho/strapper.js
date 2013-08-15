strapper.js
===========

#How To Use

Using strapper.js is very simple.

```html
<script src="jquery.min.js"></script>
<script src="strapper.js"></script>
<script src="yourjavascript.js"></script>
```

#Documentation

##CSS Cycles

Cycle through changing CSS aspects of elements.

```js
// cycleColor function generic

$('thing').cycleColors('cssProperty',['HEXVALUE','HEXVALUE','HEXVALUE'], milliseconds);

// Example

$('#titleBanner').cycleColors('color',['#ff6347','#ffff00','#ee82ee'],500);
```

##Multimedia Control

Turn a div into an ```<audio>``` object.

```js
// musicify() function generic

$('thing').musicify('file', options);

// Example

$('#musicDiv').musicify('musicfile.mp3', {controls:"true",autoplay:"true",loop:"false"});
```

Turn a div into an ```<video>``` object.

```js
// video() function generic

$('thing').musicify('file', options);

// Example

$('#videoDiv').musicify('vidfile.mp4', {controls:"true",autoplay:"true",loop:"false"});
```

##Regular Expression Construction System

Build a regular expression with ease:

```js
// Example

var exp = $.regex().whichContains("freeText","abcdefg","1+").getRegex();
alert(exp);

```
Output:

```
/abcdefg{1,}/ 
```

###The Basics
To use jRegex create a jRegex object which can be done easily by invoking:

```js
$.regex()
```

Now in order to create an actual regular expression begin the process of chaining methods. The regex creation methods that can be chained are:

```js
.startingWith()
.whichContains()
.or()
.followedBy()
.onlyIfFollowedBy()
.onlyIfNotFollowedBy()
.endingIn()
```

Finally, once all the chaining is done, you'd probably want to get the RegExp object, and this can be done by tacking one last method at the end:

```js
.getRegex()  // No arguments nessecary
```

A full example is below:

```js
var gre = $.regex()
           .startingWith("freeText","narc","1")
           .followedBy("anyChar","","2:5")
           .followedBy("anyWhitespace","","2+")
           .getRegex()
```

###The Golden Rule

Each of these methods:

```js
.startingWith()
.whichContains()
.or()
.followedBy()
.onlyIfFollowedBy()
.onlyIfNotFollowedBy()
.endingIn()
```

Requires 3 string variables as arguments. Nothing more, nothing less.

Thus, this is acceptable:

```js
.startingWith("","","")
```

Even if some strings are empty it doesn't really matter. As long as there ARE three strings present jRegex will function properly.

###The Three Arguments

These are the three string arguments that are passed into the string creation methods:

1. A Specifier
2. Field Text
3. A Quantifier

They are passed in as followed:

```js
.startingWith(specifier,fieldText,quantifier)
```

####Valid Specifier Strings

These are the valid strings you can set as your specifier

```js
"anyChar"
"anyLetter"
"anyUppercaseLetter"
"anyLowercaseLetter"
"freeText"
"anyWhitespace"
"anyDigit"
```

####Valid Field Text

When using the ```freeText``` method, you can set the fieldText string as whatever you want to match:

```js
.startingWith("freeText","YOU TEXT HERE","")
```

####Valid Quantifier Strings

You quanitifer strings can be one of three kinds:

1. An Explicit Number        "6"
2. Boundless Numbers         "6+"
3. Numbers between a range   "6:20"

This example demonstrates:

```js
.startingWith("anyChar","","6")       // Any character exactly 6 times
.startingWith("anyChar","","6+")      // Any character 6 or more times
.startingWith("anyChar","","6:20")    // Any character between 6 thru 20 times
