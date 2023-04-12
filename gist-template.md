# Matching a Hex Value with Regular Expressions

This tutorial will explain various concepts concerning regular expressions (regex), and will show how to use regex to match a specific hexidecimal value.

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.
```/^#?([a-f0-9]{6}|[a-f0-9]{3})$/```

The expression above allows one to filter strings for hexidecimal numbers. The string provided must begin with and end with the hexidecimal value for a match to occur. This filter accepts either 6 hex character strings or 3 hex character strings.

```fff``` or ```000aaa``` would be acceptable, while ```fff9``` or ```fffa``` would not.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

Anchors allow the user to specify the position constraints of a regex match. The caret ```^``` can be used to specify that the match must occur at the beginning of a string. For example, a regex such as ```/^aee/``` would match
```aee```
but not
```123aee```
Alternatively, one can match the end of a string by using the ```$``` character. This could be accomplished with ```/fff$/``` which would match
```000fff```
but not 
```fff000```


### Quantifiers

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
