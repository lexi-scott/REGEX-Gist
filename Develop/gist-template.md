# Matching an Email with REGEX 

Regular expressions, or regex for short, are a series of special characters that define a search pattern. It is useful in software engineering, data science and beyond. It comes in handy when processing strings and finding matches.


## Summary

REGEX is a powerful tool that can be used to match emails. The following pattern can be used to find an email match:

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

What is seen here is: 
`^` matches the start of a string
`[a-z0-9_\.-]` matches one or more characters that can be lowercase letters, then numbers 0-9, then underscores, then the slash tells REGEX to then looks for a period and a dash
`@` matches the @ for emails
`([\da-z\.-]+)` matches one or more characters that can be digits, lowercase letters, period, or hyphen. This is the domain name part of the email, before the top-level domain.
`\.` matches a period character
`([a-z\.]{2,6})` matches two to six lowercase letters or periods. This is the top-level domain of the email.
`$` matches the end of the string

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

### Anchors
In regular expressions, an anchor is a metacharacter that matches a specific position in a string, rather than matching a character. There are two main anchors in regex:

^ - The caret symbol ^ matches the beginning of a line or string. When used at the start of a regular expression, it specifies that the pattern must match at the beginning of a line. For example, the pattern ^hello would match any line that starts with the word "hello".

$ - The dollar sign $ matches the end of a line or string. When used at the end of a regular expression, it specifies that the pattern must match at the end of a line. For example, the pattern world$ would match any line that ends with the word "world".

These anchors are useful for specifying where in a string a pattern should match. By using anchors, you can make sure that a pattern matches only at the beginning or end of a line or string, or both.

### Quantifiers
Quantifiers are used to specify the number of times that a character or group of characters can occur. Here are some of the most commonly used quantifiers in regex:

* - The asterisk quantifier matches zero or more occurrences of the preceding character or group. For example, the pattern ab* would match "a", "ab", "abb", "abbb", and so on.

+ - The plus quantifier matches one or more occurrences of the preceding character or group. For example, the pattern ab+ would match "ab", "abb", "abbb", and so on, but not "a".

? - The question mark quantifier matches zero or one occurrence of the preceding character or group. For example, the pattern ab? would match "a" or "ab".

{n} - The exact quantifier matches exactly n occurrences of the preceding character or group. For example, the pattern a{3} would match "aaa".

{n,m} - The range quantifier matches between n and m occurrences of the preceding character or group. For example, the pattern a{2,4} would match "aa", "aaa", or "aaaa".

{n,} - The minimum quantifier matches at least n occurrences of the preceding character or group. For example, the pattern a{2,} would match "aa", "aaa", "aaaa", and so on.

Quantifiers are useful for matching patterns with varying lengths or for specifying the minimum and maximum number of characters that should be matched.

### OR Operator
The OR operator is denoted by the pipe character |. It is used to match either one expression or another. Here's an example:

cat|dog

This regex pattern will match either "cat" or "dog" in a string. So if you apply this pattern to the string "I have a cat and a dog", it will match "cat" and "dog".

The OR operator is useful when you want to match one of several possible expressions. You can use parentheses to group expressions and apply the OR operator to the group, like this:

(cats|dogs) are cute

This pattern will match "cats are cute" or "dogs are cute", but not "birds are cute".

The OR operator can also be used with other regular expression constructs, such as character classes and quantifiers, to create more complex patterns.

### Character Classes
A character class is a way to match a single character from a set of possible characters. Character classes are denoted by enclosing a set of characters in square brackets [ ]. Here are some examples:

[abc] - matches either "a", "b", or "c"
[0-9] - matches any digit from 0 to 9
[A-Za-z] - matches any uppercase or lowercase letter
[aeiou] - matches any vowel
You can also use the caret ^ character as the first character inside the square brackets to match any character that is not in the set. For example, [^0-9] would match any character that is not a digit.

You can use character classes within regular expressions to create more complex patterns. For example, the pattern [A-Za-z]+ would match one or more consecutive letters, while the pattern [0-9]{3}-[0-9]{2}-[0-9]{4} would match a Social Security number in the format XXX-XX-XXXX.
### Flags

Flags are optional modifiers that can be added to the end of a regex pattern to change how it is interpreted or executed. Here are some commonly used flags:

i - The "ignore case" flag makes the pattern case-insensitive. For example, /hello/i would match "hello", "Hello", "heLLo", and so on.

g - The "global" flag causes the pattern to match all occurrences in the input string, not just the first one. For example, /cat/g would match all occurrences of "cat" in the string.

m - The "multiline" flag changes the behavior of the caret ^ and dollar sign $ anchors to match the beginning and end of each line, rather than the beginning and end of the whole string.

s - The "dotall" flag allows the dot . character to match any character, including newlines.

u - The "unicode" flag enables support for Unicode characters in the pattern.

y - The "sticky" flag forces the pattern to only match at the current position in the input string.

To use a flag, simply append it to the end of the pattern. For example, /hello/i uses the "ignore case" flag to match "hello" in a case-insensitive manner.

Flags can be combined by simply listing them together without any spaces. For example, /cat/gi would match all occurrences of "cat" in a case-insensitive manner.
### Grouping and Capturing
Grouping and capturing is a way to capture and remember specific parts of a pattern that you want to extract or manipulate. Grouping is done by enclosing a subexpression in parentheses (). Capturing refers to the process of saving the matched substring in memory for later use.

### Bracket Expressions
Brackets can be used to create character classes that match a set of characters. Brackets are denoted by enclosing a set of characters in square brackets [ ].

For example, the pattern [aeiou] matches any of the vowels "a", "e", "i", "o", or "u". Similarly, the pattern [0-9] matches any digit from 0 to 9.

In addition to character classes, brackets can be used to create alternation expressions, which match any one of a set of alternatives. Alternation expressions are denoted by enclosing a set of alternatives in parentheses and separating them with the pipe character |.

### Greedy and Lazy Match
Greedy and lazy matching refer to different ways of matching patterns that involve repetition, such as quantifiers (*, +, ?, etc.) and curly braces ({m,n}).

Greedy matching is the default behavior in most regex engines. It matches as much of the pattern as possible while still allowing the overall pattern to match. This means that if there are multiple matches for a pattern, the greedy match will try to match as much of the input as possible, while still ensuring that the pattern as a whole can match.

For example, consider the pattern a.+b and the input string aabab. The greedy match will match the entire string aabab since it matches the first a and then tries to match as much as possible until it reaches the final b.

Lazy matching, also known as non-greedy or minimal matching, matches as little of the pattern as possible while still allowing the overall pattern to match. This means that if there are multiple matches for a pattern, the lazy match will try to match as little of the input as possible while still ensuring that the pattern as a whole can match.

For example, consider the pattern a.+?b and the input string aabab. The lazy match will match only the substring aab because it matches the first a and then tries to match as little as possible until it reaches the final b.

To make a quantifier or curly brace match lazy instead of greedy, you can add a question mark ? after it. For example, the pattern a+? will match one or more a characters, but will match as few as possible to still satisfy the pattern.

Overall, greedy and lazy matching are useful tools for fine-tuning regular expressions to match specific patterns in input text.

### Boundaries
Boundaries are used to specify the beginning or end of a word, line, or string. They help ensure that patterns are matched only in specific contexts, which can be useful for tasks like searching for specific words or phrases in text.

There are several types of boundaries that can be used in regex:

Word boundary: \b
A word boundary matches the position between a word character (\w) and a non-word character (\W). This can be used to match whole words, for example, \bcat\b would match the word "cat" but not "catch" or "category".

Not-word boundary: \B
A not-word boundary matches the position where two word characters (\w) or two non-word characters (\W) are next to each other. This can be used to match patterns that occur within words, for example, \Bcat\B would match "cat" within "catch" or "category".

Line start: ^
The ^ symbol matches the beginning of a line. This can be used to match patterns that occur at the start of a line.

Line end: $
The $ symbol matches the end of a line. This can be used to match patterns that occur at the end of a line.

String start and end: \A and \Z
The \A symbol matches the beginning of a string, while the \Z symbol matches the end of a string. These can be used to match patterns that occur only at the beginning or end of an entire string.

For example, the pattern \bhello\b would match the word "hello" only when it appears as a whole word, while the pattern ^\d would match any line that starts with a digit. 

### Back-references
Back-references in regular expressions refer to matching a previously captured group in the pattern.

To create a back-reference, you use a backslash followed by the number of the capturing group you want to reference. For example, if you wanted to match a repeated word, you could use the following regular expression:

\b(\w+)\b\s+\1

In this example, \b matches a word boundary, (\w+) captures one or more word characters, \b matches another word boundary, \s+ matches one or more whitespace characters, and \1 references the first capturing group (i.e., the first set of parentheses) which matches the same text as the first word. This regular expression would match strings like "hello hello" or "world world".

Back-references are useful for matching repeated patterns, such as repeated words, or for validating input where you want to ensure that a certain pattern occurs multiple times in a row.

### Look-ahead and Look-behind

Look-ahead and look-behind are special types of assertions in regular expressions that allow you to match patterns based on the context around them, without including that context in the match.

A look-ahead assertion is written as (?=pattern), where pattern is the regular expression you want to match after the current position. For example, the regular expression foo(?=bar) would match any occurrence of "foo" that is immediately followed by "bar", but it would not include "bar" in the match.

A negative look-ahead assertion is written as (?!pattern), and matches any position where pattern does not appear after the current position.

A look-behind assertion is written as (?<=pattern) and matches the current position if it is immediately preceded by pattern. For example, the regular expression (?<=\$)\d+ would match any sequence of digits that is immediately preceded by a dollar sign, but it would not include the dollar sign in the match.

A negative look-behind assertion is written as (?<!pattern) and matches any position that is not immediately preceded by pattern.

Look-ahead and look-behind assertions are useful for matching patterns that depend on the context around them, without including that context in the match. They can also be used to validate input by ensuring that a certain pattern appears in a specific context. However, it's important to note that look-ahead and look-behind assertions can be more computationally expensive than regular expressions that don't use assertions, so they should be used judiciously.

## Author

Lexi Scott is a passionate web developer with a keen interest in new technology. She enjoys developing full-stack web applications, from the front-end to the back-end, to create dynamic and interactive user experiences. Her love for technology extends beyond web development and she is always eager to explore new tools and techniques to improve her skills.

In addition to her work in technology, Lexi has a strong passion for agriculture and FemTech. She believes in the power of technology to create a more sustainable and equitable future and is committed to using her skills to contribute to these fields. She is dedicated to creating applications that can help farmers to improve their crop yield and reduce waste. She is also passionate about using technology to advance women's health and well-being.

Overall, Lexi is a driven and creative developer who is always looking for ways to use technology to make a positive impact on the world. Her expertise in web development and her passion for agriculture and FemTech make her a valuable asset to any team she works with.
