# Title (replace with your title)

Introductory paragraph (replace this with your text)

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

For [Module 12 homework - Employee Manager](https://github.com/conradjohnson/employee-mgr-m12), I used a code snippet from [Elias Zamaria](https://stackoverflow.com/users/28324/elias-zamaria) posted on [StackOverflow](https://stackoverflow.com/questions/2901102/how-to-print-a-number-with-commas-as-thousands-separators-in-javascript). 

The function that Elias posted: 
```
function numberWithCommas(num) {
    return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
}
```

The function receives a number and returns a string that inserts commas in the thousands places.  It is a handy function for string output formatting of large numbers for better readability. 

Example:
```
let formattedNum = numberWithCommas(123454015.99);

//formattedNum = String "123,454,015.99"
```

It uses regular expression functionality (Regex) to match string patterns in order insert commas where it finds a match of its search pattern.

As a developer, I've avoided regex patterns for as long as is possible.  This is my attempt to destructure this pattern and explain its functionaliy (as well as learn for myself).  For simplicity, this regex pattern assumes that a number with 3 or less numbers beyond the decimal point (to the right of the decimal point).

```
/\B(?=(\d{3})+(?!\d))/g
```



## Table of Contents
- [Regex Definition](#regex-definition)
- [Regex Components](#regex-components)
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Definition

A pattern that matches strings or pieces of strings. Regex is based upon the work of Ken Thompson, Bell Labs: Thompson's construction.

https://en.wikipedia.org/wiki/Thompson%27s_construction
https://en.wikipedia.org/wiki/Ken_Thompson

Regex has a rich toolset that allows applications and users to match complex patterns in strings of text.

## Regex Components

search pattern & 
text string


literal character
meta-characters 

### Anchors


```
^ = Beginning of string (or line, depending on the mode)
$ = End of string (or line, depending on the mode)
\A = Beginning of string
\z = End of string
\Z = Varies a lot depending on the engine, so be careful with it
\b = Word boundary
\B = Not a word boundary
```
source: https://cs.lmu.edu/~ray/notes/regex/

### Quantifiers
```
* = 0 or more
+ = 1 or more
? = 0 or 1
{min, max}
{n}
```
source: https://www.youtube.com/watch?v=YTocEnDsMNw&t=410s

### Grouping Constructs

### Bracket Expressions

### Character Classes


### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
