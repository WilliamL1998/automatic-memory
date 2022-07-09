# Regex Tutorial

Regex, short for Regular Expressions, is a sequence of characters that is used to match/locate/modify contents of a string.


## Summary

A commonly used regex is:\
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`\
This is used to validate an email address. In this tutorial, I will break down this regex to demonstrate the basics of regular expressions. First of all, regex is structured as two forward slashes enclosing the specified search. As you can see in the regex above, two forward slashes `/` encloses the entire expression. Below are some of the regex components that make up the specified search.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Grouping](#grouping)
- [Bracket Expressions](#bracket-expressions)
- [Email regex breakdown](#email-regex-breakdown)

## Regex Components

### Anchors
Anchors are tokens/symbols that asserts the match process.
- `^` asserts that the regex matches the beginning of a string
- `$` asserts that the regex matches the end of a string\
For example, given a string of my name: "William Liao",
- `/^William/` would match the beginning of the string and return true because "William Liao" does indeed begin with William
- `/^Liao/` would return false because "William Liao" does not begin with "Liao"\
Likewise,
- `/William$/` would return false because the string does not end with "William"
- `/Liao$/` would return true because the string does end with "Liao"\
For a complete match of my name, we would use:
- `/^William Liao$/`

### Quantifiers
Quantifiers specify how many characters, groups, or character classes are to be matched against the string.\
The simplest quantifier is `{n, m}`. `{n, m}` indicates that the string must match the given expression n to m times. Below are some other quanitfiers to elaborate.
- `?` must match either 0 or 1 time, can be written as {0, 1}
- `+` must match 1 or more times, can be written as {1, }
- `*` must match 0 or more times, can be written as {0, }
- `{n}` must match exactly n times
- `.` is the catch-all, meaning it will match anything

### OR Operator
`|` is the symbol used as the OR operator, just like in JavaScript.
- `(c|b|d|p|t)an` would match for: can, ban, dan, pan, or tan

### Character Classes
Character classes define a class of characters.\
- `\d` matches any number
- `\D` matches anything NOT a number
- `\w` matches any alphanumeric character, including the underscore
- `\W` matches anything NOT an alphanumeric character, such as `%` or a Chinese character
- `\` is the escaping character. For example, if you were to search for a period `.`, you must use `\.` to denote the search or else the regex will recognize the `.` as the catch-all quantifier

### Grouping
Grouping, as it suggests, groups expressions so that a specificity can be applied to them. It is denoted with parentheses. For example:
- `foo+` would match foo, fooo, foooo, fooooo... etc
- `(foo)+` would match foo, foofoo, foofoofoo, foofoofoofoo... etc

### Bracket Expressions
Bracket expressions are used to match anything within the square brackets.
- `[abc]` or `[a-c]` matches any one of the characters in the brackets
- `[^abc]` or `[^a-c]` matches anything NOT the characters in the brackets

### Email Regex Breakdown
Now that we have some of the basics, let's take a look at the email validation regex again:\
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Let's break this down group by group.\
We can see that there are two forward slashes `/` that encloses the search.\
There is a `^` anchor that asserts that `([a-z0-9_\.-]+)` is at the beginning of the email.\
`([a-z0-9_\.-]+)` is a bracket expression followed by the `+` quantifier. Specifically, this group checks for the username of the email.\
This bracket expression is searching for all lowercase letters, all numbers, underscores, periods (using the escape character `\`), and hyphens, repeated however many times.

Then it includes a `@` symbol.

The next group is `([\da-z\.-]+)`, another bracket expression followed by the `+` quantifier. This group is checking for the domain of the email.\
Again, this is searching for all digits, all lowercase letters, periods, and hyphens, repeated however many times.

Then it includes a `\.` period.

The next and final group is `([a-z\.]{2,6})`, it is a bracket expression that will be searched through 2 to 6 times. Specifically, this is checking for the top level domain of the email.\
The bracket expression searches for all lowercase letters and periods.

At the end of it all, is the `$` anchor, asserting that the final group is positioned at the end of the end of the email.


## Author

My name is William Liao. Check out some of my other works at https://github.com/WilliamL1998