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
- [Character Escapes](#character-escapes)
- [Grouping and Capturing](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)

- [Author](#author)

### Anchors
Regular expressions are powerful tools for identifying patterns in text. Anchors play a crucial role in determining the position of a pattern within an input string. When it comes to email validation, as demonstrated by the regex pattern `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` in this tutorial, it is vital to ensure that the entire input string matches the specified pattern, rather than just a portion of it. Anchors help enforce constraints on the position of the email components within the string, ensuring accurate email validation.

By using anchors, we prevent partial matches or undesired outcomes by explicitly specifying that the pattern should start with the beginning of the string `(^)` and end with the end of the string `($)`. This ensures that the entire email address is checked against the pattern from start to finish. Anchors are essential for achieving accurate validation and ensuring that the email address adheres to the desired format and structure.


## Two Main Types of Anchors

1. Start Anchor `^`: The caret symbol anchors the match at the beginning of a string. In the email regex pattern, it ensures that the pattern starts matching from the start of the email address.
2. End Anchor `$`: The dollar sign anchors the match at the end of a string. It ensures that the pattern matches the entire email address and there are no additional characters following it.

<br>

Anchors define the boundaries of the text that the regular expression should match.
<br>

Example One: the regex `^hello$` will only match the string `"hello"` and nothing else. It will not match `"Hello. World!"` or `"Say Hello"` because the pattern does not occur at the beginning or end of the string.
<br>
Example Two: the regex pattern `^hello` is used to find strings in which the sequence of characters `"hello"` is located at the beginning of the string. It successfully matches the substring `"hello"` in the string `"hello world"`. It will not successfully match in the string `"world, hello"` because the string does not start with `"hello"`.
<br>
Example three: the regex `hello$` identifies at the end of the string that has `"hello"`. It successfully finds a match when `"hello"` is found at the end of the string `"world hello"`. However, it does not identify when `"hello"` is located at the end of the string `"hello world"` because the string does not conclude `"hello"`.

<br> 

This specific pattern of the regex will match email addresses that begin with one or more characters. dots, underscores, or hyphens followed by the `@` symbol.

<br>

**Examples in JavaScript**:

-const regex = `/^[a-zA-Z0-9._-]+@/;`
<br>
-console.log(regex.test`("heather@email.com"));`  // Output: true
<br>
-console.log(regex.test`("test123@domain.com"));` // Output: true
<br>
-console.log(regex.test`("@wrong.com"));`       // Output: false

<br>
In email validation, the `$` anchor is placed at the end of the regex pattern to indicate that the preceding pattern must match at the end of the string. This specific pattern of the regex ensures the email address ends with a specified pattern and will match email addresses that end with a dot followed by two or more alphabetical characters.
<br>

**Example:** (I struggled with figuring out how to format this)

-const regex = `/\.[a-zA-Z]{2,}$/;`
<br>
-console.log(regex.test`("heather@email.com"));`  // Output: true
<br>
-console.log(regex.test`("test456@domain.com"));` // Output: true
<br>
-console.log(regex.test`("wrong.com."));`       // Output: false

<br>

## Quantifiers

Quantifiers serve the purpose of indicating the desired number of matches for a pattern. These quantifiers are positioned after a character, character class, or group, enabling the specification of the min and max occurance range for the pattern. 
<br>
The `+` quantifier specifies that the preceding element must occur one or more times and is used after the pattern `[a-z0-9_\.-]`. For example, `[a-zA-Z0-9._-]+` matches one or more occurrences of alphanumeric characters, dots, underscores, or hyphens in the local part and domain part of the email address. Similarly, `([\da-z\.-]+)` matches one or more occurrences of digits, lowercase letters, dots, or hyphens in the domain part of the email address. `{2,6}` quantifier is used after the character class `[a-z\.]` the third capturing group `([a-z\.]{2,6})` that matches a sequence of 2 to 6 occurrences of lowercase letters or dots in the top-level domain part of the email address. 
<br>
These quantifiers help define the expected repetition of characters or character classes within the different components of an email address. They ensure that the email address adheres to specific patterns and length constraints.


## Character Classes

Character classes, known as character sets, are a short more concise regular expression that represent specific sets of characters. The regex featured in this tutorial also uses various regex elements including character classes, character sets, metacharacters, and repeating character classes. These elements ensure the regex are assessed and sourced accurately to match the email addresses.

- Character Classes: `[a-z0-9_\.-]`: This character class matches lowercase letters `(a-z)`, digits `(0-9)`, underscores `(_)`, dots `(.)`, and hyphens `(-)`. These sets represent multiple characters, allowing a singe character match from specified range. 
<br>

- Metacharacters: `[\da-z\.-]`: This character class matches digits `(\d)`, lowercase letters `(a-z)`, dots `(.)`, and hyphens `(-)` is used as a literal character without escaping because it is placed at the beginning or end of a character set and are placed inside character classes `[a-z0-9_\.-]`. Underscores would not be valid. 
<br>

Example:

<br>
1.`heather-summers@bootcamp.com` (valid) 
<br>
2.`heather@summers_bootcamp.com` (invalid) this is considered invalid because the underscore is in the domain part of the address. 
<br>
- Repeating Character Classes: The email regex employs quantifiers such as `+` and `{2,6}` to handle repeating character classes, as mentioned earlier. The plus sign `(+)` signifies that the preceding character class or set should occur one or more times, as seen in `[a-z0-9_.-]+` and `[\da-z.-]+`. On the other hand, the curly braces `({2,6})` establish a specific range of repetitions for the preceding character class or set. For instance, `[a-z.]{2,6}` matches between 2 and 6 occurrences of lowercase letters or literal periods (dots).
<br>
Conclusion: Character sets, metacharacters within character classes, and repeating character classes collaborate to form flexible regex patterns. Familiarizing ourselves with their usage empowers us to construct regex patterns that are both efficient and powerful for different scenarios. This tutorial showcases the application of these elements in creating a regex pattern specifically designed for matching email addresses. By mastering these concepts, we can enhance our ability to construct regex patterns that meet our specific requirements with precision and effectiveness.

## Character Escapes

When matching an email address, character escapes can be employed to represent certain characters or character classes. The `\.` character escape is used to match a literal (`.`) character within the email address. This will ensure that the regex correctly matches valid email addresses, as seen in the first example, while it is not mtching the invalid email address in the second example. 
<br>
Consider the following two email addresses:
1. heather.summers@bootcamp.edu (valid)
2. heather@invalid@bootcamp.edu (invalid)

<br>
If the dot (.) is not escaped in a regular expression, it becomes a wildcard character that can match any character in its place. This can lead to incorrect matching of invalid email addresses.

To avoid this issue, we escape the dot (.) by using a backslash (\), like this: \\. By escaping the dot, we enforce that the regex pattern only matches valid email addresses with literal periods in the correct positions. This prevents the dot from functioning as a wildcard and ensures more precise and accurate pattern matching for email validation.


## Grouping and Capturing

Grouping constructs in regular expressions (regex) allow us to group characters or sub-expressions together and treat them as a single unit within the expression. They are denoted by parentheses () and serve several important purposes:

1. Applying quantifiers: By grouping characters or sub-expressions within parentheses, we can apply quantifiers such as +, *, or {} to specify how many times the grouped elements should occur. This allows us to control the repetition of a specific pattern.
2. Capturing matches: Grouping constructs also enable us to capture the matched content for later use. By enclosing a portion of the regex pattern in parentheses, we create a capturing group. The matched value within that group can be retrieved and used in subsequent operations or replacements.
3. Creating backreferences: Capturing groups can be referenced later in the regex pattern using backreferences. This allows us to match the same content again, ensuring consistency within the string. Backreferences are represented by a backslash followed by a number, indicating the corresponding capturing group.
4. Applying alternation: Grouping constructs can be used to apply alternation, denoted by the pipe symbol (|), within the parentheses. This allows us to define multiple alternative options for matching. Only one of the alternatives needs to match for the overall pattern to be considered a match.

By utilizing grouping constructs in regular expressions, we gain more control over the behavior of the pattern, enable capture and reuse of matched content, and provide flexibility for matching alternative patterns. 
<br>

The regular expression featured in this tutorial contains 3 grouping contructs enclosed amoung parentheses (). Each group captures a different part of the email address: 1. Local-Part `([a-z0-9_\.-]+)`matches the username of the email address, 2. Domain `([\da-z\.-]+)` corresponds and matches the domain name, 3. Top-level Domain `([a-z\.]{2,6})`aligns and matches the top-level domain. By utilizing these grouping constructs within the regex pattern, each component of the email address is effectively captured and validated individually. This approach ensures that the email address as a whole adheres to the accepted standards and validates its different parts accurately.

## Bracket Expressions

The bracket expression `[a-z\.]{2,6}` matches any singe character in the range a-z or the literal (`.`) character. The expression is then followed by the quantifier {2,6} , matched characters must occur between 2 and 6 times, inclusive. 
<br>
Breakdown of the expression:
<br>
-`heath.er` contains lowercase letters matching `a-z` part of the expression
<br>
-`\.` is the literal period character matching this expression
<br>
-`heath.er` matches `{2,6}` quantifier, as it consists of 6 characters in total (5 letters, 1 (`.`) )
<br>


## Author

Follow me on GitHub at [codingprincess111](https://github.com/codingprincess111)
<br>
Deployed GitHub-Gist Link: [Deployed GitHub-Gist Link: Click Here]()
