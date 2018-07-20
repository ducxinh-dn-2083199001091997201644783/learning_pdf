## White-space characters 
1. Table
|Decimal| Hexadecimal| Octal| Name|
|-|-|-|-|
|0      | 00         | 000  | Null (NUL)|
|9      | 09         | 011  | HORIZONTAL TAB (HT)|
|10     | 0A         | 012  | LINE FEED (LF)|
|12     | 0C         | 014  | FORM FEED (FF)|
|13     | 0D         | 015  | CARRIAGE RETURN (CR)|
|32     | 20         | 040  | SPACE (SP)|


## Delimiter characters
1. table
|Glyph| Decimal | Hexadecimal| Octal| Name                |
|-----|---------|------------|------|---------------------|
|(    | 40      | 28         | 50   | LEFT PARENTHESIS    |
|)    | 41      | 29         | 51   | RIGHT PARENTHESIS   |
|<    | 60      | 3C         | 60   | LESS-THAN SIGN      |
|>    | 62      | 3E         | 62   | GREATER-THAN SIGN   |
|[    | 91      | 5B         | 133  | LEFT SQUARE BRACKET |
|]    | 93      | 5D         | 135  | RIGHT SQUARE BRACKET|
|{    | 123     | 7B         | 173  | LEFT CURLY BRACKET  |
|}    | 125     | 7D         | 175  | RIGHT CURLY BRACKET |
|/    | 47      | 2F         | 57   | SOLIDUS             |
|%    | 37      | 25         | 45   | PERCENT SIGN        |

## Regular characters


## Comments
1.  Any occurrence of the PERCENT SIGN (25h) outside a string or stream introduces a comment
```
abc% comment ( /%) blah blah blah
123
```

## Escape sequences in literal strings

|Sequence| Meaning|
|--------|--------|
|\n      |LINE FEED (0Ah) (LF)|
|\r      |CARRIAGE RETURN (0Dh) (CR)|
|\t      |HORIZONTAL TAB (09h) (HT)|
|\b      |BACKSPACE (08h) (BS)|
|\f      |FORM FEED (FF)|
|`\(`    |LEFT PARENTHESIS (28h)|
|`\)`    |RIGHT PARENTHESIS (29h)|
|`\\`    |REVERSE SOLIDUS (5Ch) (Backslash) |
|\ddd    |Character code ddd (octal)        |


##  Examples of literal names
|Syntax for Literal name   |  Resulting Name|
|--------------------------|----------------|
|/1.2                      |1.2             |
|/$$                       | $$             |
|/@pattern                 |@pattern        |
|/.notdef                  |.notdef         |
|/lime#20Green             |Lime Green      |
|/paired#28#29parentheses  |paired()parentheses|
|/The_Key_of_F#23_Minor    |The_Key_of_F#_Minor|
|/A#42                     |AB              |

