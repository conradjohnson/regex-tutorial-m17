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

Regex has a rich toolset that allows applications and users to match complex patterns in strings of text.  Once a pattern is matched, programming languages like javascript provide string and logic tools to use with what you DO with that pattern: parse and store data, manipulate the string pattern found, remove from string, etc...

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
n* = 0 or more of character 'n'
n+ = 1 or more of character 'n'
n? = 0 or 1 of character 'n'
n{2, 4} = 2, 3 or 4 sequential character 'n'
n{2} =  exactly 2 'n'
n{2,} = 2 or more 'n'
```
source: https://www.youtube.com/watch?v=YTocEnDsMNw&t=410s, https://regexcrossword.com


### Grouping Constructs
```
. = Any character except new line (\n)
(A|B) = A or B
(...) = Group
\n = nth group/sub pattern
```
### Bracket Expressions
Also known as 'Range' expressions.
```
[ABC] = A or B or C
[^ABC] = Not A, B or C
[A-Z] = Character between A and Z uppercase
[0-9] = Number between 0 and 9
[A-Z0-9] = Characters between A and Z and numbers between 0 and 9

```

### Character Classes

```
\w = Word is any of (a-z, A-Z, 0-9, underscore)
\W = non word
\d = digit
\D = Non-digit
\s = Whitespace
\S = Not whitespace
\b = Match at begining or end
\B = Do not match at beginning or end
\0 = NULL character
\n = new line

```

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
