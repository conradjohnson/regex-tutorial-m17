# Regex - Inevitable 

You've ignored this tool for long enough. Just as death and taxes are certainties in life, regex reliance is a certainty in a developers journey.  Best to give in already. 

## Summary


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
- [Lookaheads](#lookahead)
- [RegEx Example Breakdown](#regex-example-breakdown)

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
? = greedy quantifier.  Optionally include preceeding character.  Manl?y would match 'Many' and 'Manly'
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

Character classes are typically used in [Grouping Constructs](#grouping-constructs) and [Bracket Expressions](#bracket-expressions).

```
[ABC] = A or B or C
[0-9] = Number between 0 and 9
(^10) = No groupings of 0s and 1s.
(1|3) = the number 1 or 3
```


### The OR Operator

The pipe | or the OR operator is used in [Grouping Constructs](#grouping-constructs).

```
Ex:
(1|3) = the number 1 or 3.
```

### Flags
A flag changes the default searching behavior of a regular expression. It makes a regex search in a different way.  source: https://www.codeguage.com/courses/regexp/flags
/pattern/flags

```
i = ignore casing 
g = global will make search for all occurences.
s = Dot all. makes the wild character . match new lines as well.
m = Multiline. Makes Anchor characters ^ and $ match every new line, instead of just the beginning and end of a string.
u = Unicode. Forces characters to match 32 bit characters.
```
### Character Escapes
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

### Lookaheads

Lookaheads can be a positive or negative lookahead.

Positive lookaheads matches something that is followed by pattern defined, without making the pattern defined part of the match.
```r
something(?=pattern)
```

Negative lookaheads matches something NOT followed by something else.
```r
something(?!somethingelse)
```


source: https://www.regular-expressions.info/lookaround.html


### Regex Example Breakdown

```r
/\B(?=(\d{3})+(?!\d))/g

```
First - we're wrapping a [flag](#flags) around the entire pattern with:
```r
/Pattern/g

```
with the \g flag which searches for all occurrences of our pattern, not just a single occurance as we want all groupings of 3 digits starting at a non digit, and preceeded by another digit.

That leaves us with pattern:
```r
\B(?=(\d{3})+(?!\d))

```
Which starts with \B - which says do not match at beginning or end.   Meaning, we don't want to start at the beginning of our number string. 

Remaining pattern is:
```r
(?=(\d{3})+(?!\d))
```

Our pattern:
```r
(?=[some pattern])
```
is a positive [lookahead](#lookaheads).

\B used in conjunction with our positive lookahead will take our positive lookahead pattern and start matching at all unique occurences of 3 digits, 3 digits after the 'beginning' of our number starting from the the zeros place and counting to however many 10 multiples we have.

Our remaining pattern fed to the lookahead:
```r
(\d{3})+(?!\d)
```
we're looking for 3 digits: '(\d{3})' that are '+' and a negative lookahead. 

```r
(?!\d)
```

The negative lookahead will start the search for a group of 3 numbers that are not followed by a digit.

Our regex 'pattern' breakdown is as follows:

```r
Flag/\B-don't start at beginning or end, with a (?= Positive lookead for all (\d{3}) 3 digit ocurrences with a (?!\d) negative lookahead for any digit)/g-Find all occurrences
```


## Author

Conrad Johnson is a web2/web3 developer.  - https://github.com/conradjohnson
