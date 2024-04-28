# My Regex Tutorial

Regular expressions, often abbreviated as regex or regexp, are sequences of characters that define a search pattern. These patterns are used to perform operations like finding, matching, and manipulating text based on specific rules.

At its core, a regular expression is a way to describe a set of strings (sequences of characters) using a concise syntax. This syntax consists of various elements, such as literal characters, character classes, quantifiers, and other constructs, which allow you to define complex patterns.

Regular expressions can be powerful and expressive, but they can also become complex and difficult to read and maintain, especially for intricate patterns. It's essential to strike a balance between the complexity of the pattern and readability, often favoring simpler and more maintainable solutions when possible.
Overall, regular expressions are a valuable tool in the programmer's toolkit, providing a concise and flexible way to work with text data and patterns across various domains and programming languages.

## Summary

Code /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/

The code we will be using will be regular expression which can be useful for validating passwords or other strings that need to meet specific complexity requirements, such as containing a mix of uppercase and lowercase letters, digits, and special characters, with a minimum length.

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

validation code =  /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/


### Anchors
/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/
^ and $: Anchors that ensure the entire string matches the pattern.
(?=.*[a-z]): Positive lookahead that asserts the presence of at least one lowercase letter.
(?=.*[A-Z]): Positive lookahead that asserts the presence of at least one uppercase letter.
(?=.*\d): Positive lookahead that asserts the presence of at least one digit.
(?=.[@$!%?&]): Positive lookahead that asserts the presence of at least one special character from the set [@$!%*?&].
[A-Za-z\d@$!%*?&]{8,}: Matches any combination of letters (uppercase and lowercase), digits, and the specified special characters, with a minimum length of 8 characters.


### Quantifiers

/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/

Quantifiers in regular expressions are used to specify how many times a particular pattern or character should be matched. They provide control over the number of occurrences of a particular element in a pattern.
Here are the commonly used quantifiers in regular expressions:

? (Question Mark): Matches the preceding element zero or one time. It makes the preceding element optional.

Example: colou?r matches both "color" and "colour".


* (Asterisk): Matches the preceding element zero or more times.

Example: a*b matches "b", "ab", "aab", "aaab", and so on.


+ (Plus): Matches the preceding element one or more times.

Example: a+b matches "ab", "aab", "aaab", but not "b".


{n}: Matches the preceding element exactly n times.

Example: a{3}b matches "aaab" but not "ab" or "aaaab".


{min,max}: Matches the preceding element at least min times but not more than max times.

Example: a{2,4}b matches "aab", "aaab", and "aaaab", but not "ab" or "aaaaaaab".


{n,}: Matches the preceding element at least n times.

Example: a{2,}b matches "aab", "aaab", "aaaab", and so on.


{,m}: Matches the preceding element at most m times (0 to m times).

Example: a{,3}b matches "b", "ab", "aab", and "aaab", but not "aaaab".



These quantifiers can be combined with other regular expression elements to create more complex patterns. Here are a few examples:

\d{3}-\d{3}-\d{4}: Matches a pattern like "123-456-7890", which could be a phone number format.
\w+@\w+\.\w{2,4}: Matches an email address pattern like "example@mail.com" or "user@domain.co.uk".
(https?://)?(www\.)?example\.com: Matches "http://example.com", "https://example.com", "www.example.com", and "example.com".

Quantifiers add flexibility and control to regular expressions, allowing you to match patterns with varying numbers of occurrences. They are essential for working with patterns that have repeating or optional elements.

### Grouping Constructs

Grouping constructs in regular expressions are used to treat multiple characters or patterns as a single unit. They allow you to apply quantifiers, alternations, or other operations to the entire group rather than individual characters. There are several types of grouping constructs:

Parentheses (): This is the most common way to create a group. Parentheses define a capturing group, which captures the matched substring for use in backreferences or for retrieving the matched text.

Example: (ab)+ matches one or more occurrences of the string "ab", such as "ab", "abab", "ababab", etc.


Non-capturing group (?:): This construct groups patterns without capturing the matched substring for backreferences or retrieval. It's useful when you want to apply quantifiers or operations to a group without capturing it.

Example: (?:ab)+ matches one or more occurrences of "ab", like (ab)+, but doesn't capture the matched text.


Positive lookahead (?=): This construct asserts that the following pattern must be present, but it doesn't match or consume the pattern. It's useful for applying conditions on the pattern without including it in the match.

Example: \d+(?=px) matches digits followed by "px", like "200px", but doesn't include "px" in the match.


Negative lookahead (?!): This is the opposite of positive lookahead. It asserts that the following pattern must not be present.

Example: \b\w+(?!ing\b) matches words that don't end with "ing", like "walk" or "play", but not "playing" or "walking".


Positive lookbehind (?<=): This construct asserts that the preceding pattern must be present, but it doesn't match or consume the pattern.

Example: (?<=https?://)www.\w+ matches "www.example.com" in "http://www.example.com", but not in "example.com".


Negative lookbehind (?<!): This is the opposite of positive lookbehind. It asserts that the preceding pattern must not be present.

Example: (?<!re)\bbat\b matches the word "bat" when it's not preceded by "re", like in "bat" or "combat", but not in "rebat".


Named groups (?<name>): This construct allows you to assign a name to a group, which can make regular expressions more readable and maintainable, especially for complex patterns.

Example: (?<protocol>https?):\/\/(?<domain>\w+)\.\w+ defines two named groups: "protocol" and "domain".



Grouping constructs are essential for creating complex regular expressions and applying quantifiers, alternations, or other operations to groups of characters or patterns. They also enable more advanced features like backreferences, lookarounds, and named groups, which can enhance the power and flexibility of your regular expressions.

### Bracket Expressions

Bracket expressions, also known as character classes or character sets, are a way to define a set of characters that you want to match in a regular expression. They are enclosed in square brackets [ ].
Here are the different types of bracket expressions:

Positive Character Class [abc]: Matches any single character within the brackets. For example, [abc] matches "a", "b", or "c".
Negated Character Class [^abc]: Matches any single character that is not in the brackets. The caret ^ inside the brackets negates the character class. For example, [^abc] matches any character except "a", "b", or "c".
Range Expression [a-z]: Matches any character within the specified range. For example, [a-z] matches any lowercase letter, and [0-9] matches any digit.
Intersection [a-z&&[^bc]]: Matches any character that is present in both character classes. In this example, [a-z&&[^bc]] matches any lowercase letter except "b" and "c".
Subtraction [a-z&&[^m-p]]: Matches any character that is in the first character class but not in the second. In this example, [a-z&&[^m-p]] matches any lowercase letter except "m", "n", "o", and "p".
Special Characters [\s\d\w\.]: Bracket expressions can also include special characters like \s (whitespace), \d (digit), \w (word character), and \. (period). For example, [\s\d] matches any whitespace character or digit.
POSIX Character Classes [[:alpha:][:space:]]: POSIX character classes are predefined character classes that represent common character types. For example, [[:alpha:]] matches any alphabetic character, and [[:space:]] matches any whitespace character.
Unicode Properties \p{Script=Greek}\P{InGreek}: Unicode properties allow you to match characters based on their Unicode properties, such as script, category, or block. For example, \p{Script=Greek} matches any character in the Greek script, and \P{InGreek} matches any character not in the Greek block.

Bracket expressions are a powerful way to match specific characters or character ranges in your regular expressions. They can be combined with other regular expression constructs to create more complex patterns.
Here are a few examples:

[0-9]+: Matches one or more digits.
[^aeiou]: Matches any character that is not a vowel.
[\s\r\n]+: Matches one or more whitespace characters, including line breaks.
\b[a-zA-Z0-9]+\b: Matches whole words consisting of alphanumeric characters.
[[:digit:][:upper:]]+: Matches one or more digits or uppercase letters.

Bracket expressions provide a concise and flexible way to specify character sets, making regular expressions more expressive and precise.

### Character Classes

/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/

Character classes are a way to define a set of characters that you want to match in a regular expression. They are similar to bracket expressions, but they are pre-defined and use a slightly different syntax. Character classes are typically represented by a backslash followed by a special character or sequence.
Here are some common character classes in regular expressions:

. (Dot): Matches any single character except a newline character (\n).

Example: .at matches "bat", "cat", "hat", etc.


\d: Matches any digit character (0-9).

Example: \d+ matches one or more digits, like "123", "456", etc.


\D: Matches any non-digit character.

Example: \D+ matches one or more non-digit characters, like "abc", "xyz", etc.


\w: Matches any word character (alphanumeric characters and underscore _).

Example: \w+ matches one or more word characters, like "hello", "world_123", etc.


\W: Matches any non-word character.

Example: \W+ matches one or more non-word characters, like "!@#$%^&*()".


\s: Matches any whitespace character (space, tab, newline, carriage return, etc.).

Example: \s+ matches one or more whitespace characters.


\S: Matches any non-whitespace character.

Example: \S+ matches one or more non-whitespace characters.


[\b]: Matches a backspace character (not to be confused with the word boundary \b).

Example: [\b]+ matches one or more backspace characters.


\0: Matches a NULL character.

Example: \0 matches a NULL character.



These character classes provide a shorthand way to match specific types of characters without having to write out the full character set or range. They are widely used and can help make regular expressions more concise and readable.
Here are a few examples that demonstrate the use of character classes:

^[\d\s]+$: Matches strings that contain only digits and whitespace characters.
\w+@\w+\.\w{2,4}: Matches email addresses with alphanumeric characters, underscores, and periods.
[\s\r\n]+: Matches one or more whitespace characters, including line breaks.
[^\w\s]+: Matches one or more non-word and non-whitespace characters (e.g., punctuation).

Character classes can be combined with other regular expression constructs, such as quantifiers, groups, and alternations, to create more complex patterns and match specific text patterns efficiently.

### The OR Operator

/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/

The OR operator (|) in regular expressions is used to create an alternation or logical disjunction between multiple patterns. It allows you to match either one pattern or another pattern.
The syntax for using the OR operator is:
Copy codepattern1|pattern2|pattern3|...
The regular expression engine will attempt to match any of the provided patterns, and if any one of them matches, the overall match is successful.
Here are some examples:

Matching different words:
    cat|dog|bird
This pattern will match "cat", "dog", or "bird".
Matching different character classes:
    \d+|[a-zA-Z]+
This pattern will match either one or more digits (\d+) or one or more letters ([a-zA-Z]+).
Matching different types of URLs:
    https?://(www\.)?example\.com|ftp://\w+\.\w+
This pattern will match URLs starting with either "http://" or "https://" followed by "example.com" (optionally preceded by "www."), or URLs starting with "ftp://" followed by a word character (\w+) and a period (.), and another word character.

The OR operator can be combined with other regular expression constructs like grouping, character classes, and quantifiers to create more complex patterns. It's important to note that the alternation is evaluated from left to right, and the first matching pattern is used.
Here's another example:
    (cat|dog)|bird
In this case, the pattern will match either "cat", "dog", or "bird". However, due to the grouping, the alternation cat|dog is evaluated first, and if either "cat" or "dog" is matched, the overall pattern is considered a match, and "bird" is not evaluated.
The OR operator is a powerful tool for creating flexible regular expressions that can match multiple patterns or variations of a pattern. It is particularly useful when you need to handle different possible formats or cases within the same regular expression.


### Flags

/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/

In regular expressions, flags are modifiers that can be applied to the pattern to change its behavior or characteristics. Flags are typically added at the end of the regular expression literal or defined as part of the regular expression object in programming languages.
Here are some common flags used in regular expressions:

i (Case-insensitive): This flag makes the regular expression case-insensitive, meaning it will match both uppercase and lowercase letters.

Example: /hello/i matches "hello", "Hello", "HELLO", etc.


g (Global): This flag enables global matching, allowing the regular expression engine to find all matches in the input string instead of stopping after the first match.

Example: /\d/g matches all digits in the string "1a2b3c".


m (Multiline): This flag changes the behavior of the ^ and $ anchors to match the start and end of each line in a multiline string, instead of the start and end of the entire string.

Example: /^World/m matches "World" at the beginning of each line in a multiline string.


s (Dotall): This flag makes the dot (.) match newline characters as well, which is not the default behavior.

Example: /^.*$/s matches the entire string, including newlines.


u (Unicode): This flag enables full Unicode support, treating patterns as Unicode code point sequences.

Example: /\u{1F600}/u matches the Unicode code point for the grinning face emoji (🙂).


y (Sticky): This flag makes the regular expression match from the last index where a match was found, rather than starting from the beginning of the string.

Example: /\d/y matches the first digit in "1a2b3c", and subsequent calls to the exec() method will start searching from the position after the previous match.



Different programming languages and regular expression engines may support additional flags or have slightly different implementations of these flags. It's always a good idea to consult the documentation for the specific language or library you're using for the most up-to-date and accurate information.
Flags are powerful modifiers that can enhance the functionality and behavior of regular expressions to better suit your specific use case. They can be combined to achieve more complex matching scenarios.

### Character Escapes

Character escapes are a way to represent special characters or characters with special meanings in regular expressions. Without escaping, these characters would be interpreted as part of the regular expression syntax rather than as literal characters to be matched.

In regular expressions, the backslash (`\`) is used as the escape character. When a backslash is placed before a character, it "escapes" the character, allowing it to be matched literally.

Here are some commonly used character escapes:

1. **`\d`**: Matches any digit character (`0-9`).
2. **`\D`**: Matches any non-digit character.
3. **`\w`**: Matches any word character (alphanumeric characters and underscore `_`).
4. **`\W`**: Matches any non-word character.
5. **`\s`**: Matches any whitespace character (space, tab, newline, carriage return, etc.).
6. **`\S`**: Matches any non-whitespace character.
7. **`\b`**: Matches a word boundary (position between a word character and a non-word character).
8. **`\B`**: Matches a non-word boundary.
9. **`\n`**: Matches a newline character.
10. **`\r`**: Matches a carriage return character.
11. **`\t`**: Matches a tab character.
12. **`\0`**: Matches a NULL character.
13. **`\xHH`**: Matches a character with the given hexadecimal code.
14. **`\uHHHH`**: Matches a Unicode character with the given hexadecimal code.
15. **`\.`**: Matches a literal period (since the period normally matches any character except newline).
16. **`\\`**: Matches a literal backslash.

These are just a few examples of character escapes. There are many more, depending on the regular expression engine and programming language you're using.

Character escapes are useful when you want to match characters that have special meanings in regular expressions, such as periods, parentheses, brackets, or backslashes. They allow you to treat these characters as literals rather than as part of the regular expression syntax.

Here are a few examples:

- `/\d+\.\d+/`: Matches one or more digits, followed by a literal period, followed by one or more digits (e.g., "3.14", "42.0").
- `/https?:\/\//`: Matches "http://" or "https://".
- `/\\\\/`: Matches a single backslash character.
- `/\u2665/`: Matches the Unicode character for a heart symbol (♥).

Character escapes are an essential part of regular expressions, as they provide a way to precisely match and handle special characters and patterns that would otherwise be interpreted differently by the regular expression engine.

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
