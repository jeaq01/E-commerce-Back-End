# Explanation of matching an Email Regex

Regex, short for regular expression, is a sequence of characters that forms a search pattern. This pattern can be used to match, locate, and manage text. Regex is a powerful tool for string manipulation and validation, widely used in programming, data processing, text editing, and even web development, today we are going to focus on Validation, especificaly on how to validate a Email using a regex.

## Summary

Email validation is the process of verifying that an email address is formatted correctly and meets certain criteria before it is accepted or processed by a system. The goal is to ensure that the email address is likely to be valid and deliverable, minimizing errors and improving user experience.
This regular expression is used to validate email addresses:

 ``/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/``
 
 Let's brake it down:

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
- [Summary and examples](#Summary-and-examples)

## Regex Components

### Anchors
 `/^` - `$/`
  Indicates the start of the string or the end. This ensures that the entire input must match the regex pattern from the very beginning. This could be in one of two formats:
  
  Just as with the `^` character, it can be preceded by an exact string or a range of possible matches.

  The `$` anchor signifies a string that ends with the characters that precede it.


### Quantifiers
Quantifiers set the limits of the string that your regex matches, it specifies how many instances of a character, group, or character class must be present for a match. In this regex, the following quantifiers are used:

`+` This means "one or more" of the preceding element. It is used in three places:

`([a-z0-9_\.-]+)` Requires one or more characters in the local part of the email.
`([\da-z\.-]+)` Requires one or more characters in the domain part.
`([a-z\.]{2,6})` Specifies that the TLD must have between 2 and 6 characters.
`{2,6}` This is a specific quantifier indicating that the preceding element (characters in the TLD) must appear at least 2 times and at most 6 times.

### OR Operator
This regex does not explicitly use an OR operator `(|)`. However, it does allow for multiple characters within character classes, which can give the impression of an OR-like functionality. For example:
`[a-z\.-]` allows for either a lowercase letter, a dot, or a hyphen, but this is not the same as using `(|)`.

### Character Classes
Character classes define a set of characters that can match at that position in the string. In this regex, the following character classes are present:
`[a-z0-9_\.-]`: Matches any lowercase letter, digit, underscore, dot, or hyphen (used in the local part).
`[\da-z\.-]`: Matches any digit, lowercase letter, dot, or hyphen (used in the domain part).
`[a-z\.]{2,6}`: Matches any lowercase letter or dot (used for the TLD)

### Flags
A regex must be wrapped in slash characters. The one exception to this rule is with the component known as flags. Flags are placed at the end of a regex, after the second slash, and they define additional functionality or limits for the regex.
This regex does not use any flags in the given form. Common flags include `i` (case-insensitive), `g` (global search), and `m` (multiline). Since this regex operates on lowercase letters only, the absence of the `i` flag is notable.

### Grouping and Capturing
The primary way you group a section of a regex is by using parentheses `(())`. Each section within parentheses is known as a subexpression.
Grouping constructs have two primary categories: capturing and non-capturing. The important thing to understand is that capturing groups capture the matched character sequences for possible re-use.
This regex is capture in three parts:
`([a-z0-9_\.-]+)`: Captures the local part.
`([\da-z\.-]+)`: Captures the domain part.
`([a-z\.]{2,6})`: Captures the top-level domain.

### Bracket Expressions
Anything inside a set of square brackets `([])` represents a range of characters that we want to match. These patterns are known as bracket expressions, the Bracket expressions are used to specify a set of characters to match in this regex are:
`[a-z]`: Matches any lowercase letter.
`[0-9]`: Matches any digit.
`[._-]`: Matches a dot, underscore, or hyphen.
Combined in character classes, these allow for flexible matching of the valid characters in each part of the email.

### Greedy and Lazy Match
The quantifiers used in this regex are greedy, meaning they match as many characters as possible while still allowing the overall pattern to succeed. For example:
`+` will consume as many characters as it can while still satisfying the overall structure of the email.

### Boundaries
A boundary is a position where one side is a word character and the other side is not a word character or the start/end of a string. The key point to remember here is that a boundary is a position, not a character. Boundaries are represented by specific symbols in REGEX: \b for word boundaries, \B for non-word boundaries, and ^ and $ for the start and end of a string.
This regex uses `^` and `$` to assert boundaries:
`^` asserts that the match must start at the beginning of the string.
`$` asserts that the match must end at the end of the string.

## Summary and examples
The regex: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` is a well-structured pattern for validating email addresses, utilizing quantifiers, character classes, grouping, and boundary assertions. While it effectively checks for a valid email format, it has limitations and may not cover all possible valid email addresses according to the full specifications.
# Example Matches

* example@mail.com
* user.name@sub.domain.co
* first_last123@company.org

# Non-matches

* InvalidEmail@.com (no domain)
* user@domain.c (TLD too short)
* User@domain.com (uppercase letters not allowed in local part)

## Author

Hello! I am Julio and i am a junior web developer with experience in creating efficient and engaging digital solutions. I specialize in front-end and back-end, always looking to optimize the user experience. Passionate about innovation, I enjoy taking on new challenges and collaborating on projects that make a difference.

# Github link:
https://github.com/jeaq01/Matching-an-Email-Regex-explanation.git



