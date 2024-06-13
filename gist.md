# Matching URL Regex Tutorial 

Regex expressions, also known as regular expressions or rational expressions are a sequence of characters that specify a match pattern in text. They do this by searching and manipulating text strings, particularly in processing text files. A singluar line of regex can replace several dozen lines of programming code, this is what makes regex expressions so useful! Regex expression are implemented in Pytho, C and Java, to say a few. Though in all language the expression works the same, there may be differences in syntax, but today we will look at the Javascript regex that matches URL expressions, ensuring they are a valid URL.

## Summary

This is the Regex expression in question that is used in Javasript to validate a URL: 

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Let move onto breaking this expression down, figuring out how it works.


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)

## Regex Components

A regex consists of multiple componenets to describe the patterns and must be wrapped in slash characters (/), as they are an expression literal. 

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

### Anchors

Anchors are used to limit how a regex matches a particular string by telling the regex engine where matches can begin and where they can end. 

- `'^'` which is called a caret is used the start the regex, the caret acts as an anchor to define the starting position of the string. For example, the regex '^hello' only matches text that includes 'hello' at the start of a string.

- `'$'`, the dollar sign is used to end a regex expression. it specifies that the string must end with the chracter that precedes it. For example, the regex hello$ only matches text that includes "hello" at the end of a string.

in the URL regex the `'^'` ensures the string starts with the URL pattern and the `'$'` ensures it ends with the URL pattern. 

### Quantifiers

Quantifiers are used to specify the amount of times a chracter or group of characters can occur in the input string. 

In the URL matching regex, there are several quntifiers:  `'?'`, `'+'`, `'*'`, and `'{2,6}'`.

- `'?'` this quntifier makes the group preceding group optional, meaning it can occur 0 to 1 time. In the regex expression: `'(https?:\/\/)?'` the `'?'` makes the `'https://'` or `'http://'` part optional.

- `'+'` this quntifier allows the the preceding expressions or characters to occur one or more times. For example for expression: `'([\da-z\.-]+)'` any of the characters inside can occur one or more times. 

- `'*'` this quantifier means that the preceding character or expression can occur zero of more times. For example in: `'([\/\w \.-]*)'` any of the characters inside the expression can occur zero or more times. 

- `'{2,6}'` this quantifier defines that the characters inside the bracket expression can occur between 2 and 6 times. For example, this expression: `'([a-z\.]{2,6})'` ensures the the TLD (Top Level Domain) of the URL is between 2 and 6 characters long, meaning that shorter domain names like '.com', '.co', '.net' and longer domain names, including, '.info', '.media' and '.travel' are accpeted.

### Grouping Constructs

In Regex grouping constructs separate a regular expression into subexpressions, and capture the substrings of an input string. In the URL match expression there are four groups: `'(https?:\/\/)?'`, '`([\da-z\.-]+)'`, `'([a-z\.]{2,6})'`, and `'([\/\w \.-]*)*'`.

These groups are defined with parentheses `'()'` at the beginning and end of each group. They are used to organise specific part of the expression and allow manipulation of specific parts of data (e.g. extracting or chnaging a specific part of text such as the domain name from a URL). 

### Bracket Expressions

Bracket expressions contain character classes which define the set of characters we want to match in the expression, or can be used to to define a set of characters we don't want to match. Now, lets look at the bracket expressions used in our URL regex: 

`[\da-z.-]`
- '`\d`' matches and digit from '0' to '9'.
- '`a-z`' matches any lowercase letter from 'a' to 'z'.
- '`\.`' matches a dot (.).
- '`-`' matches a hyphen (-).

This bracket expression ensures that the domain name section of the URL expression can contain digits, lowercase letters, dots, and hyphens.

`[a-z.]`
- '`a-z`' matches any lowercase letter from 'a' to 'z'.
-  '`\.`' matches a dot (.).

This bracket expression ensures that the top-level domain (TLD) part of the URL can contain lowercase letters and dots.

`[/\w .-]`
- '`\/`' matches a forward slash (/).
- '`\w`' matches any word character (This is further explained in the character class section). 
- '` `' matches a space character. 
- '`\.`' matches a dot (.).
- '`-`' matches a hyphen (-).

This bracket expression ensures that the path section of a URL can contain forward slashes, word characters, spaces, dots, and hyphens.

By understanding these bracket expressions, we can see how the regex allows for a flexible yet specific matching of various parts of a URL.


### Character Classes

Character classes are used to specify a set of characters. Lets see examples used in the URL matching expression: 

- '`[]`' specifies a set of characters.
- '`\d`' specifies a digit, its equivalent is this bracket expression '`[0-9]`'
- '`\w`' specifies a word character, its equivalent is this bracket expression: '`[a-zA-Z0-9_]`'.

These character expressions are used in the bracket expressions: '`([\da-z\.-]+)'`, and `'([\/\w \.-]*)*'`.

### The OR Operator

The OR operator '|' is used to combine multiple patterns. Though there are no explicit OR operators there are implicit OR operators used within bracket expressions of the URL regex. For example: 

- `'[a-z.]'` could be written as: `'(a|b|c|d|e|f|g|h|i|j|k|l|m|n|o|p|q|r|s|t|u|v|w|x|y|z|\.)'`


## Author

Adelle Ocampo - [GitHub Link](https://github.com/adellemaeocampo )