# Matching an Email Regex: Understanding the Components by Heather Summers


In this tutorial, we aim to provide a comprehensive understanding of the elements involved in regular expressions (regex) by
delving into practical examples and providing in-depth explanations. Our focus will be on email regex, where we will break down the components of regex patterns designed to validate email addresses. This tutorial is tailored for individuals who are new to the subject and seek a thorough understanding of regex concepts.


## Summary

This tutorial will consistently refer to the provided regular expression (regex) displayed below for the purpose of analyzing each regex component. The regex components discussed in this document include: anchors, quantifiers, grouping constructs, bracket expressions, character classes, and finally character escapes. 


```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```
<br>

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Escapes](#character-escapes)
- [Author](#author)

### Anchors

Regular expressions are powerful tools for identifying patterns in text. Anchors play a crucial role in determining the position of a pattern within an input string. In the context of email validation, as demonstrated by the regex pattern `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` in this tutorial, it is essential to ensure that the entire input string matches the specified pattern, rather than just a portion of it.

## Two Main Types of Anchors

1. Start Anchor `^`: The caret symbol anchors the match at the beginning of a string. In the email regex pattern, it ensures that the pattern starts matching from the start of the email address.
2. End Anchor `$`: The dollar sign anchors the match at the end of a string. It ensures that the pattern matches the entire email address and there are no additional characters following it.

<br>

Anchors define the boundaries of the text that the regular expression should match.
<br>

Example One: the regex `^hello$` will only match the string `"hello"` and nothing else. It will not match `"Hello. World!"` or `"Say Hello"` because the pattern does not occur at the beginning or end of the string.
<br>
Example Two: the regex pattern `^hello` is used to find strings in which the sequence of characters `"hello"` is located at the beginning of the string. It successfully matches the substring `"hello"` in the string `"hello world"`. It will not successfully match in the string `"world, hello"` because the string does not start with `"hello"`.


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
