# REGEX Cheatsheet

This is a Regex cheatsheet

## Summary

A regular expression is a sequence of characters that defines a search pattern for a character combination. Such sequence is composed by preset notations (meta and literal characters) that form conditions to narrow a larger text down to the text of search.

This cheatsheet provides an overview of regex meta characters in the context of Javascript.

## Table of Contents

- [Examples](#Examples)
- [Character Classes](#character-classes)
- [Assertions](#assertions)
- [Grouping Constructs](#grouping-constructs)
- [Quantifiers](#quantifiers)
- [Bracket Expressions](#bracket-expressions)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex

### Examples

| function             | example                    | Regex                                                           |
| -------------------- | -------------------------- | --------------------------------------------------------------- |
| Matching a Hex Value | #FF5733                    | /^#?([a-f0-9]{6}\|[a-f0-9]{3})$/gi                              |
| Matching an Email    | test.1111@gmail.com        | /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/               |
| Matching a URL       | https://regex101.com/      | /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]_)_\/?/ |
| Matching an HTML Tag | `<div>this is a div</div>` | /^<([a-z]+)([^<]+)_(?:>(._)<\/\1>\|\s+\/>)$/                    |

- Break down (URL example: https://github.com/heranYang93/REGEX-cheatsheet)

  | 1°   | 2°             | function                                                                            | function                                                                           |
  | ---- | -------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
  | ^    |                | assertion: asserts position at start of the string                                  | <span style="color:red">https://</span>github.com/heranYang93/REGEX-cheatsheet     |
  | ()?  |                | 1st capturing group; the presence of this first group is NOT mandatory              | <span style="color:green">https://</span>github.com/heranYang93/REGEX-cheatsheet   |
  |      | ^()            | Must start with this group of characters                                            | <span style="color:green">https://</span>github.com/heranYang93/REGEX-cheatsheet   |
  |      | http           | must contain characters-http                                                        | <span style="color:green">http</span>s://github.com/heranYang93/REGEX-cheatsheet   |
  |      | s?             | there might be an 's'                                                               | http<span style="color:green">s</span>://github.com/heranYang93/REGEX-cheatsheet   |
  |      | :\/\/          | ':'+'/'+'/'                                                                         | https<span style="color:green">://</span>github.com/heranYang93/REGEX-cheatsheet   |
  | ()   |                | 2nd capturing group; the presence of this first group is mandatory                  | https://<span style="color:pink">github</span>.com/heranYang93/REGEX-cheatsheet    |
  |      | []+            | search for more than 1 letters that belong to the characters in []                  | https<span style="color:pink">://</span>github.com/heranYang93/REGEX-cheatsheet    |
  |      | \d             | numbers                                                                             | https://github.com/heranYang93/REGEX-cheatsheet                                    |
  |      | a-z            | alphabetic                                                                          | https://<span style="color:pink">github</span>.com/heranYang93/REGEX-cheatsheet    |
  |      | \\.            | .(dot)                                                                              | https://github.com/heranYang93/REGEX-cheatsheet                                    |
  |      | -              | -(dash)                                                                             | https://github.com/heranYang93/REGEX-cheatsheet                                    |
  | \\.  |                | .(dot)                                                                              | https://github<span style="color:blue">.</span>com/heranYang93/REGEX-cheatsheet    |
  | ()   |                | 3rd capturing group; the presence of this first group is mandatory                  | https://github.<span style="color:magenta">com</span>/heranYang93/REGEX-cheatsheet |
  |      | [a-z\.]{2,6}   | search for 2-6 letters that belong to []                                            | https://github.<span style="color:magenta">com</span>/heranYang93/REGEX-cheatsheet |
  | ()\* |                | 4th. 5th, 6th ... capturing group                                                   | https://github.com<span style="color:yellow">/heranYang93</span>/REGEX-cheatsheet  |
  | ()\* |                | 4th. 5th, 6th ... capturing group                                                   | https://github.com/heranYang93<span style="color:cyan">/REGEX-cheatsheet</span>    |
  |      | [\\/\w /\.-]\* | 0 to many letters that belong to []                                                 | https://github.com<span style="color:yellow">/heranYang93/</span>REGEX-cheatsheet  |
  |      | \\/            | '/'                                                                                 | https://github.com<span style="color:yellow">/</span>heranYang93/REGEX-cheatsheet  |
  |      | \/w            | alphabetic                                                                          | https://github.com/<span style="color:yellow">heranYang93</span>/REGEX-cheatsheet  |
  |      | ` `            | ` `matches the character with index 3210 (2016 or 408) literally (case insensitive) | https://github.com/heranYang93/REGEX-cheatsheet                                    |
  |      | \\.            | .(dot)                                                                              | https://github.com/heranYang93/REGEX-cheatsheet                                    |
  |      | -              | -(dash)                                                                             | https://github.com/heranYang93/REGEX<span style="color:cyan">-</span>cheatsheet    |
  | \\/? |                | '/', presence NOT mandatory                                                         | https://github.com/heranYang93/REGEX-cheatsheet                                    |
  | $    |                | assertion: asserts position at the end of the string                                | https://github.com/heranYang93/REGEX-cheatsheet                                    |

  -- ^ assertion: asserts position at start of the string
  -- (https?:\/\/)
  --- ()

### Character Classes

Characters, special characters and signs<strong style="color:red"> position </strong>

| topic | function                                              | example                                                             | Regex                                   | Alternative     |
| ----- | ----------------------------------------------------- | ------------------------------------------------------------------- | --------------------------------------- | --------------- |
| .     | any single character                                  | yes make <span style="color:red">my</span> day                      | /.y/                                    |                 |
| \d    | any digit                                             | R<span style="color:red">2</span>-D<span style="color:red">2</span> | /.\d-.\d/                               | /[0-9]/         |
| \D    | <span style="color:red">NOT</span> digit              | <span style="color:red">Javascript</span>                           | /\D/                                    | /[^0-9]/        |
| \w    | alphanumeric + \_                                     | <span style="color:red">Javascadfadsf123123ript</span>              | /\w/                                    | /[A-Za-z0-9_]/  |
| \W    | <span style="color:red">NOT</span> alphanumeric + \_  | Javascadfads<span style="color:red">'"</span>f123123ript            | /\W/                                    | /[^a-za-z0-9_]/ |
| \s    | white space                                           | foo<span style="color:red"> bar</span>                              | /<span style="color:red">\s</span>\w\*/ |                 |
| \S    | <span style="color:red">OTHER THAN</span> white space | <span style="color:red">foo</span> bar                              | /<span style="color:red">\S</span>\w\*/ |                 |

### Assertions

Anchors mark the <strong style="color:red"> position </strong>

| char    | function             | example                                                                          | Regex                      |
| ------- | -------------------- | -------------------------------------------------------------------------------- | -------------------------- |
| ^       | beginning            | <span style="color:red">J</span>avascript                                        | /^J/                       |
| $       | end                  | Javascrip<span style="color:red">t</span>                                        | /t$/                       |
| x(?=y)  | look ahead           | <span style="color:red">Jack</span> Sprat                                        | /Jack(?=\sSprat\|\sFrost)/ |
| x(?!y)  | NEGATIVE look ahead  | Jack Frost                                                                       | /Jack(?!\sSprat\|\sFrost)/ |
| (?<=y)x | look behind          | Jack <span style="color:red">Sprat</span>                                        | (?<=Jack\s\|Tom\s)Sprat    |
| (?<!y)x | NEGATIVE look behind | Jack Sprat                                                                       | (?<!Jack\s\|Tom\s)Sprat    |
| \b      | word boundary        | Bojack's <span style="color:red">jacket</span>                                   | \bjack                     |
| \B      | NONE word boundary   | Boja<span style="color:red">ck</span>'s CK ja<span style="color:red">ck</span>et | /\Bck/gi                   |

### Grouping Constructs

Group the <strong style="color:red"> characters </strong>

| char         | function                         | example                                                                                                      | Regex                            |
| ------------ | -------------------------------- | ------------------------------------------------------------------------------------------------------------ | -------------------------------- |
| x\|y         | or                               | <span style="color:red">red</span> apple                                                                     | /green\|red/                     |
| [xyz][a-c]   | any enclosed                     | J<span style="color:red">a</span>vascript                                                                    | /[abcd]/                         |
| [^xyz][^a-c] | NONE enclosed                    | <span style="color:red">J</span>avascript                                                                    | /[^abcd]/                        |
| (x)          | match groups (matchAll)          | foo <span style="color:red">bar</span> <span style="color:red">bar</span> <span style="color:red">bar</span> | /(bar)/                          |
| \k<Name>     | matching the Named capture group | Do you copy? <span style="color:red">Sir, yes Sir</span>                                                     | /(?\<title>\w+), yes \k\<title>/ |

### Quantifiers

| char   | function             | example                                                                             | Regex                            |
| ------ | -------------------- | ----------------------------------------------------------------------------------- | -------------------------------- |
| x\*    | 0 or more repetition | <span style="color:red">boooooed</span> or <span style="color:red">bird</span>      | /bo\*/                           |
| x+     | 1 or more repetition | <span style="color:red">boooooed</span> but NOT <span style="color:red">bird</span> | /bo+/                            |
| x?     | 0 or 1               | `no one cares if is here`                                                           | /no one cares if( Ben)? is here/ |
| x{n,m} | repeat times         | See bracket expressions                                                             | -                                |

### Bracket Expressions

| Bracket | function                   | example                                                                                                                                                         | Regex                      |
| ------- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| []      | a set of character         | Eleph<span style="color:red">a</span>nt                                                                                                                         | /[a-d]/                    |
| {}      | match times (2 to 4 times) | <span style="color:red">Ba-ba-ba-</span><span style="color:green">ba-</span><span style="color:green">ba-</span>nana                                            | /(ba\\-){1,3}/             |
| ()      | remembered matches         | 'Firsty McLastname''Firsty McLastname'.match(/([A-Za-z]+)\s([A-Za-z]+)/) // -> matches 'First McLastname' with 'Firsty' remembered as $1 and 'McLastname' as $2 | /([A-Za-z]+)\s([A-Za-z]+)/ |

### The OR Operator

| Bracket | function | example                                           | Regex        |
| ------- | -------- | ------------------------------------------------- | ------------ |
| (\|)    | or       | <span style="color:red">One Two</span> three four | /(one\|two)/ |

### Flags

Flags are declared after / to allow for special functionalities
Common flags are as follow ...

| function                               | Flag |
| -------------------------------------- | ---- |
| multiline                              | m    |
| global                                 | g    |
| case-insensitive                       | i    |
| Generate indices for substring matches | d    |

### Character Escapes

The backslash in a regular expression precedes a literal character.
Certain letters that represent common character classes can be escaped, such as \w for a word character or \s for a space.

| escaped characters | Flag                                        |
| ------------------ | ------------------------------------------- |
| \\                 | a single backslash \                        |
| \/                 | a single forwardslash \                     |
| \A                 | start of a string                           |
| \b                 | word boundary                               |
| \B                 | not word boundary                           |
| \d                 | [0-9]                                       |
| \D                 | [^0-9]                                      |
| \l                 | [a-z]                                       |
| \L                 | [^a-z]                                      |
| \u                 | `[^A-Z]`                                    |
| \U                 | `[^A-Z]`                                    |
| \w                 | `[a-Z0-9_]`                                 |
| \W                 | `[^a-Z0-9_]`                                |
| \r                 | return                                      |
| \s                 | space                                       |
| \S                 | NOT space                                   |
| \S                 | NOT space                                   |
| \Q                 | ignore escaped characters until \E is found |
| \E                 | stop processing escaped characters          |

## Author

hy -
https://github.com/heranYang93
