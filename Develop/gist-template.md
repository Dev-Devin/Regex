# RegEx to matching an Email

RegEx, short for regular expression, is a pattern made up of characters that is utilized to search for specific text strings. It is commonly used to locate generic character sequences, and one example of its application is in identifying email addresses.

## Summary

Matching an email using regex involves verifying that the characters inputted by a user conform to the structure of a legitimate email address. In the following text, I will elaborate on the various elements of this regex and its practical application. Here's a sample regex that can be used for matching an email,

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

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

Regexes are enclosed in "/" characters to indicate their literal form. These regexes consist of different parts, which will be elucidated in the following sections.

### Anchors

In order to initiate a regex, the "^" character must be used, indicating that any matching string will start with the specified characters or range following the "^". Similarly, to conclude a regex, the "$" character must be used, signaling that the matching string must end with that particular character or range. In the given code snippet, the entirety of the expression must match, as it has a "^" immediately following the opening slash and a "$" immediately preceding the closing slash.

"/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/", uses the caret and dollar sign to specify the exact format of the email address that it will match. The first part of the expression matches the username portion of the email address, the second part matches the domain name, and the third part matches the top-level domain

### Quantifiers

Quantifiers are used in regular expressions to limit the scope of the string that will be matched. These quantifiers specify a minimum and maximum number of times the pattern should appear in order to be considered a match. Some examples of quantifiers include the asterisk symbol "\*", which matches zero or more times, the plus symbol "+", which matches one or more times, the question mark symbol "?", which matches zero or one time, and the curly braces "{}", which can be used to specify a specific number of times to match, a minimum number of times to match, or a range of times to match.

In our code, the quantifier "{2,6}" has been used, which means that the pattern must be matched at least twice, but no more than six times.

### OR Operator

The purpose of the "or" operator in regular expressions is to inform the pattern that any of the characters enclosed within a group (represented by parentheses) may be matched, rather than requiring all of them to match. For instance, if we aim to locate the match of "gym," the text must contain the letters "g," "y," and "m." However, if we use the group "(g|y|m)" instead, it would match any of the following: "g," "y," "m," "gy," "ym," "gm," "gym," "ymg," "myg," and so on. It's important to note that our code does not employ this operator.

### Character Classes

Character classes are abbreviated codes that represent a specific grouping of characters. Some examples of character classes are:

"." which matches any character except for a newline
"\d" which matches any digit
"\D" which matches any non-digit character
"\w" which matches any uppercase or lowercase letter, digit, or underscore
"\s" which matches any whitespace character, such as tabs or line breaks.
In the second grouping of our code, we utilize the "\d" character class.

### Flags

To add extra functionality or constraints to a regular expression, we can append flags at the end of the expression (after the final "/"). The six flags can be used in any order and can be combined, and they are as follows:

"d": gives an index location for the matching piece of a string
"g": searches for all possible matches in the text
"i": ignores the case of letters
"m": treats each new line as a new match, instead of just one
"s": includes the newline character in the "." character class (which is excluded by default)
"u": provides various Unicode-related features
"y": sets the specific index at which to attempt a match.
In our code, no flag is used at the end, so there is no additional functionality or limitations imposed.

### Grouping and Capturing

When characters are enclosed in parentheses in a regular expression, they are treated as distinct groups. In the regex for matching an email that we've been using, the first set of parentheses represents one group of characters that must appear before the "@" symbol, while the subsequent characters must be between "@" and the "." symbol, and so on. The process of capturing enables us to treat multiple characters as a single unit.

In the email matching code, we have three groups:

Group One: /^([a-z0-9_.-]+)@/
Group Two: /([\da-z.-]+)./
Group Three: /([a-z.]{2,6})$/
These groups are defined by enclosing the relevant characters within parentheses, and the "^" and "$" symbols denote the beginning and end of the string, respectively.

### Bracket Expressions

Bracket expressions in regular expressions allow us to represent a range of characters. Inside the brackets, we can include multiple characters, and the regex will attempt to find a match to any of them. By adding a hyphen between any two letters or numbers, the regex will include all the characters in between as well.

In the regex "/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/", the first character(s) can be any letter from "a" to "z", any number from "0" to "9", an underscore, a backslash, a period, and/or a hyphen. The "+" symbol tells the expression that there can be one or more of these characters. After the "@" symbol, the next character(s) can be any number (which is the same as "[0-9]", as we learned in the character classes section above), any letter from "a" to "z", and/or a period and/or a hyphen. Again, the "+" symbol tells the expression that there can be one or more of these characters. After this, there will be a period, and following that will be any letter from "a" to "z" and/or a period. The "{2,6}" is one of the quantifiers we learned about earlier, which means that there must be at least 2 and at most 6 of these characters.

### Greedy and Lazy Match

The quantifiers section explained how curly brace quantifiers can determine the range for the number of times an expression should match. By default, the regex will try to match as many occurrences of the pattern as possible. However, by adding a "?" after the quantifier, it becomes "lazy," causing the expression to match the fewest possible occurrences.

It is worth noting that our code does not include a "?" after the quantifier, so it remains "greedy" and tries to match as many occurrences as possible.

### Boundaries

To include special characters such as "^" and "$" as literal characters in a regular expression, we use the escape syntax by preceding them with a backslash. In the example code for matching an email, we can see an example of this in the first grouping of characters where "$" is included as a literal character: /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/

### Back-references

Back-references are stored matches that can be referred to and used for various purposes, such as manipulating the string or making comparisons within the regex.

### Look-ahead and Look-behind

Different look-ahead and look-behind conditions are used for different purposes. For instance, a positive look-ahead condition will result in a match only if it is followed by a specific character or group of characters, whereas a negative look-ahead condition will match only if it is NOT followed by that specified character or group of characters. Look-behinds work similarly, but instead of considering the characters that follow the match, they look at the characters that precede it. A positive look-behind condition matches only if the match is preceded by that specific character or group of characters, and a negative look-behind condition matches only if the match is not preceded by that specific character or group of characters.

## Author

Devin Polichetti is a Columbia University student who is currently studying to become a full-stack software engineer. He is highly motivated and committed to learning as much as possible in order to excel in his new field. If you'd like to view his public repositories and projects, please visit https://github.com/Dev-Devin
