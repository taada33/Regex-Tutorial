# Matching a Hex Value with Regular Expressions

This tutorial will explain various concepts concerning regular expressions (regex), and will show how to use regex to match hexidecimal values.

## Summary

--hex blurb?
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
but not:  
```123aee```  
Alternatively, one can match the end of a string by using the ```$``` character. This could be accomplished with ```/fff$/``` which would match  
```000fff```      
but not:     
```fff000```    
These anchors can be used in the same expressions such as ```/^000fff$/``` which would match  
```000fff```   
but not:   
```000ffff``` or ```0000fff```   

### Quantifiers

Quantifiers can be used in regular expressions to determine how many times a match is made. For instance, the ```*``` character following a specified item means that the item will be matched 0 or more times. A similarly placed ```+``` character means that the item will be matched 1 or more times.   
For instance, ```/00f*/``` will produce matches given strings ```00``` ```00f``` or ```00ffffff```   
While ```/00f+``` will match in all cases above except ```00```, since there is no occurence of the ```f``` character.   
Additionally, ```?``` can be used to indicate that a match will be made with either 0 or 1 occurences of the preceding character. In practice, a regular expression of ```/00f?/``` would match the strings ```00``` and ```00f``` but not ```00ffffff```   

If a specific number of matches are required, then curly brackets can be used to accomplish this. Using ```x{n}```  means that the character ```x``` must be matched exactly ```n``` times. Alternatively, ```x{n,}``` means that the character ```x``` must be matched at least ```n``` times.   
A range of matches can be specified using ```x{n,m}```, where ```x``` is matched between ```n``` (lower bound) and ```m``` (higher bound) times.   

### OR Operator

The OR operator can be used with regex to implement more complex logical expressions. For instance, if you wanted to have matches where the binary representation of the hexidecimal looked something like ```1xxx0000``` (where x indicates bits that can take any value), then one would want to accept hexidecimal values ```80``` or ```90``` or ```a0``` etc. This could be accomplished with the following regex expression:   
```/80|90|a0|b0|c0|d0|e0|f0/```   
where the pipe ```|``` indicates an OR operator within the regex. This means that only of the the strings within the expression must be present for a match to occur.  

### Character Classes

Character classes allow the regex user to specify which characters can occur in a match. For example, if we wanted to match ```ffx``` in hexidecimal, where x can be any hexidecimal character, we would use the regex expression:
```/ff[abcdef0123456789]/```
this indicates that the match must be ```ff``` followed by any of the characters inside the square brackets. Alternatively, this could be accomplished using
```/ff[a-f0-9]/``` where the notation ```a-f``` and ```0-9``` specify the range of acceptable characters (abcdef and 0123456789).

Character classes can also be expressed in the form ```\d``` or ```\s``` ```\w```. ```\d``` would match any digit, ```\s``` would match any whitespace symbol (spaces, tabs, or newlines) and ```\w``` would match word characters. ```\w``` is equivalent to the bracket expression ```[A-za-z0-9_]```. Finally, the dot character class ```.``` can be used to match any character (except newline). 

### Flags

Three flags(```i```, ```g``` and ```m```) will be covered in this tutorial. Flags are used in regular expressions to allow for additional specified functionality.    For instance, following your regex with an ```i``` flag such as ```/ffff/i``` will search for the ```ffff``` with case insensitivety; this means that both ```ffff``` and ```FFFF``` or ```ffFF``` will all match.   
Another useful flag is the ```g``` (global) flag, which does not return after the first match, but rather searches throughout the provided string for all matches.   
ex: given ```"90 + 10 = a0"``` to the expression ```/[a-f0-9]{2}/g``` will match ```90, 10, a0``` where not including the global flag would result in only the first hex number being matched.   
The multi line flag ```m``` can be used to alter the functionality of the ```$``` and ```^``` anchors, which will instead refer to the beginning and end of a line instead of the beginning and end of a string.

### Grouping and Capturing

Grouping in regular expressions is the use of parenthesis or round brackets ```(``` and ```)``` to denote a group. This allows one to treat a set of characters inside a group as a singular item. By default, each group in an expression is numbered from left to right and can be [back-referenced](#back-references). If this behaviour is not desired, then a non-capturing group can be used with syntax ```(?:text)```. A regular capture group may look something like:   
```/a(ff)/```
Where ff is grouped together. This allows one to use quantifiers on a group of characters (ex: ```/a(ff){2}/``` which would match ```affff```) or allows the use of alternation within groups (ex: ```/f(11|00)/``` which would match ```f11``` or ```f00```).

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
