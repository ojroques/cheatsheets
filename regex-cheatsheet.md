# REGEX cheatsheet

From [regexone.com](https://regexone.com/) and [regexr.com](https://regexr.com/).


## Contents

* [Characters Classes](#character-classes)
* [Positions](#positions)
* [Quantifiers](#quantifiers)
* [Escaped Characters](#escaped-characters)
* [Capture Groups](#capture-groups)


## Character Classes

| Expression | Pattern                                                                   |
| ---------- | ------------------------------------------------------------------------- |
| `abc...`   | Letters                                                                   |
| `123...`   | Digits                                                                    |
| `[abc]`    | Any character in the set                                                  |
| `[^abc]`   | Any character not in the set                                              |
| `[a-z]`    | Characters having a code between the two specified characters (inclusive) |
| `.`        | Any character                                                             |
| `\w`       | Any alphanumeric (*A-Z*, *a-z*, *0-9*) character                          |
| `\W`       | Any non-alphanumeric character                                            |
| `\d`       | Any digit                                                                 |
| `\D`       | Any non-digit characters                                                  |
| `\s`       | Any whitespace (spaces, tabs, line breaks)                                |
| `\S`       | Any non-whitespace character                                              |


## Positions

| Expression | Pattern                                                  |
| ---------- | -------------------------------------------------------- |
| `^`        | Start of the string                                      |
| `$`        | End of the string                                        |
| `\b`       | Boundary between a word character and non-word character |
| `\B`       | Any position that is not a word boundary                 |


## Quantifiers

| Expression   | Pattern                  |
| ------------ | ------------------------ |
| `*`          | Zero or more repetitions |
| `+`          | One or more repetitions  |
| `?`          | Optional character       |
| `{m}`        | *m* repetitions          |
| `{m,}`       | *m* or more repetitions  |
| `{m, n}`     | *m* to *n* repetitions   |
| `(abc\|def)` | *abc* or *def*           |


## Escaped Characters

| Expression | Pattern                        |
| ---------- | ------------------------------ |
| `\+`       | Character with special meaning |
| `\xFF`     | Character in hexadecimal form  |
| `\t`       | Tab character                  |
| `\n`       | Line feed character            |
| `\r`       | Carriage return character      |
| `\0`       | Null character                 |


## Capture Groups

| Expression | Pattern                   |
| ---------- | ------------------------- |
| `(abc)`    | Capture group             |
| `\1`       | Result of a capture group |