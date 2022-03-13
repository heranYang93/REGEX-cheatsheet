# REGEX Cheatsheet

This is a Regex cheatsheet

## Summary

A regular expression is a sequence of characters that defines a search pattern for certain target text combination. Such sequence of characters is made up by preset notations (meta and literal characters) that form conditions to narrow a larger text down the text of search.

This cheatsheet provides an overview of regex meta characters in the context of Javascript.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

This is how Regex typically look like:

### Character Classes

| topic | function                                              | example                                                             | Regex                                   | Alternative     |
| ----- | ----------------------------------------------------- | ------------------------------------------------------------------- | --------------------------------------- | --------------- |
| .     | any single character                                  | yes make <span style="color:red">my</span> day                      | /.y/                                    |                 |
| \d    | any digit                                             | R<span style="color:red">2</span>-D<span style="color:red">2</span> | /.\d-.\d/                               | /[0-9]/         |
| \D    | <span style="color:red">NOT</span> digit              | Javascript                                                          | /\D/                                    | /[^0-9]/        |
| \w    | alphanumeric + \_                                     | Javascript                                                          | /\w/                                    | /[A-Za-z0-9_]/  |
| \W    | <span style="color:red">NOT</span> alphanumeric + \_  | Javascript                                                          | /\W/                                    | /[^a-za-z0-9_]/ |
| \s    | white space                                           | foo<span style="color:red"> bar</span>                              | /<span style="color:red">\s</span>\w\*/ |                 |
| \S    | <span style="color:red">OTHER THAN</span> white space | <span style="color:red">foo</span> bar                              | /<span style="color:red">\S</span>\w\*/ |                 |
| \t    | tab                                                   |                                                                     |                                         |                 |
| \r    | return                                                |                                                                     |                                         |                 |
| \n    | linefeed                                              |                                                                     |                                         |                 |
| \v    | vertical tab                                          |                                                                     |                                         |                 |
| \f    | form-feed                                             |                                                                     |                                         |                 |
| \0    | NUL character                                         |                                                                     |                                         |                 |
| \t    | tab                                                   |                                                                     |                                         |                 |

### Assertions

Anchors mark the <strong style="color:red"> position </strong>

| char    | function             | example                                   | Regex                      |
| ------- | -------------------- | ----------------------------------------- | -------------------------- |
| ^       | beginning            | <span style="color:red">J</span>avascript | /^J/                       |
| $       | end                  | Javascrip<span style="color:red">t</span> | /t$/                       |
| x(?=y)  | look ahead           | <span style="color:red">Jack</span> Sprat | /Jack(?=\sSprat\|\sFrost)/ |
| x(?!y)  | NEGATIVE look ahead  | Jack Frost                                | /Jack(?!\sSprat\|\sFrost)/ |
| (?<=y)x | look behind          | Jack <span style="color:red">Sprat</span> | (?<=Jack\s\|Tom\s)Sprat    |
| (?<!y)x | NEGATIVE look behind | Jack Sprat                                | (?<!Jack\s\|Tom\s)Sprat    |

### Grouping Constructs

| char         | function                         | example                                                                                                      | Regex                            |
| ------------ | -------------------------------- | ------------------------------------------------------------------------------------------------------------ | -------------------------------- |
| x\|y         | or                               | <span style="color:red">red</span> apple                                                                     | /green\|red/                     |
| [xyz][a-c]   | any enclosed                     | J<span style="color:red">a</span>vascript                                                                    | /[abcd]/                         |
| [^xyz][^a-c] | NONE enclosed                    | <span style="color:red">J</span>avascript                                                                    | /[^abcd]/                        |
| (x)          | match groups (matchAll)          | foo <span style="color:red">bar</span> <span style="color:red">bar</span> <span style="color:red">bar</span> | /(bar)/                          |
| \k<Name>     | matching the Named capture group | Do you copy? <span style="color:red">Sir, yes Sir</span>                                                     | /(?\<title>\w+), yes \k\<title>/ |

### Quantifiers

| char   | function                        | example                                                                             | Regex  |
| ------ | ------------------------------- | ----------------------------------------------------------------------------------- | ------ |
| x\*    | 0 or more repetition            | <span style="color:red">boooooed</span> or <span style="color:red">bird</span>      | /bo\*/ |
| x+     | 1 or more repetition            | <span style="color:red">boooooed</span> but NOT <span style="color:red">bird</span> | /bo+/  |
| x?     | 0 or 1                          |                                                                                     |        |
| x{n}   |                                 | <span style="color:red"></span>                                                     |        |
| x{n,}  |                                 | <span style="color:red"></span>                                                     |        |
| x{n,m} | <span style="color:red"></span> |                                                                                     |        |

### Bracket Expressions

### The OR Operator

### Flags

| function     | example    | Regex |
| ------------ | ---------- | ----- |
| multiline    | Javascript | //m   |
| global       | Javascript | //g   |
| alphanumeric | Javascript | //i   |
| end          | Javascript | /\d/  |
| alphanumeric | Javascript | /\w/  |
| end          | Javascript | /\d/  |

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
