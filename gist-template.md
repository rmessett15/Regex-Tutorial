# Regular Expression - Matching an Email

Regular expressions, often referred to as regex, refers to a distinct string usually made up of various sets of characters that can be used as both a query tool and a validator in code bases, as well as traditional documents. They were dervied in the early 1950s out of the concept of regular language coined by the mathemitician Stephen Cole Kleene. They became widely used in 1968 within the theoretical computer science field as a way to match patterns within text files and support lexical analysis. Although regular expressions are known for being extremely cryptic looking, when broken down piece by piece, one can see they are not quite as complex as they look to the untrained eye, and one could start writing their own regex expressions fairly easily.

## Summary

This tutorial will be covering the regex expression used for both matching and validating an email:

`^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`

Imagine your a software developer tasked with finding all emails within a code base that were being utilized in a non-secure way. Searching through the code base and other documents using the regular expression shown above would help find all emails extremely quickly. The regular expression shown above can also be implemented as a string within a code base as a way of matching and validating an email. Making sure that when users fill out certain forms requiring a valid email address, the regex string can be implemented in a way that will not allow the user to continue until they have entered an unspecified number of characters, followed by an @ symbol, followed by a domain name an unspecified number of characters long, followed by the domain name system (in this example the domain name system needs to be between 2 and 6 characters long i.e. .com, .net, .dev, etc.).

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

The regex components that define this particular expression are anchors, quantifiers, meta escape characters, character classes, single character matches, grouping and capturing, and bracket expression. Regarding the example used in this tutorial: `^` and `$` are the anchors used, `+` and `{2, 6}` are the two quantifiers, `\d` represents the meta escape character utilized, `[a-z0-9_\.-]`, `[\da-z\.-]`, and `[a-z\.]` represent the character classes, `_`, `\.`, `-` represent the single character matches used, `()` represents the way this regex expression utilizes grouping and capturing, and `[]` delinates the bracket expression used.

### Anchors

Anchors within regex mark the start and end points of the expression. In regards to this expression, the `^` marks the start of the expression and the `$` marks the end of the expression. 

### Quantifiers

Quantifiers are meta characters that modify the previous character in the regex and say, how many of those do I want to match in a row.

Quantifiers allow the specification of how many character or character classes should be matched.

- The `+` sign matches one or more preceeding character
- `{min, max}` create a specific numerical quantifier range (you will notice this is used at the end of the regex expression     above at the end to give a specific range to the domain name system)

### OR Operator

There are no OR operators within this particular regex expression but in general OR operators are represented with the pipe `|` and specified under the regex type of alternation.

### Character Classes

Character classes are the attribute in a regex expression that allow us to define specific sets of characters that can be used in a search pattern.

The character classes utilized in this regex expression are `[a-z0-9_\.-]`, `[\da-z\.-]`, and `[a-z\.]`.

`[a-z0-9_\.-]`: `a-z` matches a single character in the range between a (index 97) and z (index 122) (case sensitive), `0-9` matches a single character in the range between 0 (index 48) and 9 (index 57) (case sensitive), `_` matches the character _ with index 9510 (5F16 or 1378) literally (case sensitive), `\.` matches the character . with index 4610 (2E16 or 568) literally (case sensitive), and `-` matches the character - with index 4510 (2D16 or 558) literally (case sensitive).

`[\da-z\.-]`: `\d` can be used to match any digit (0-9), `a-z` matches a single character in the range between a (index 97) and z (index 122) (case sensitive), `\.` matches the character . with index 4610 (2E16 or 568) literally (case sensitive), and `-` matches the character - with index 4510 (2D16 or 558) literally (case sensitive).

`[a-z\.]`: `a-z` matches a single character in the range between a (index 97) and z (index 122) (case sensitive), and `\.` matches the character . with index 4610 (2E16 or 568) literally (case sensitive)

Other examples of single characters:

`\d` can be used to match any digit (0-9), `\w` to match any alphanumeric character (a-zA-Z0-9), and `\s` any white space such as a space or a tab

### Flags

Regex flags are used to modify an expressions behavior -> case sensitivity, etc. There are only 6 of them in JavaScript -> i: case-sensitivity, g: looks for all matches, m: multiline mode, s: enables "dotall" mode that allows a dot `.` to match a newline character `\n`, u: enables full Unicode support, and y: "sticky" mode. 

The regex expression covered in this tutorial does not utilize flags.

### Grouping and Capturing

`()` creates a sequence or sub expression and is a way to treat multiple characters as a single unit. You will notice the regex expression being covered in this tutorial uses `()` to distinct groups of characters. The first set covers all characters before the `@` symbol. The second group coveres all characters before the `.`, and the last group covers all characters from the `.` to the end.

### Bracket Expressions

`[]` create a character or group range and represent a single character. In regards to the regex expression this tutorial is covering, the brackets are used to separate each character class. The character can be anything specified within the brackets.

Example: `[a-z0-9_\.-]` -> this character can be matched with any lowercase letters from `a-z`, and digit from `0-9`, an underscore `_`, a period `.`, or a dash `-`. 

### Greedy and Lazy Match

Greedy matching is a default behavior of regex where the regex engine will try to match a much of the string as possible, while lazy matching is the inverse and will try to match as little of the string as possible. 

- Greedy will keep searching until the condition is satisfied
- Lazy will stop searching once the condition is satisfied

In summary it is good practice to know that greedy matching can often times be slower than lazy matching because it greedy matching will not stop until it reaches the end of a string looking for all possible matches while lazy matching will stop as soon as it finds the first match.

### Boundaries

`\b` is an example of a word boundary. It usually represents matching positions on either side; where once side is a word character and the other is something other than a word character.

Word boundaries are particularlly useful when you want to match a sequence of letters or digits on their own, to ensure they occur at the beginnning or end of a specific sequence of characters.

### Back-references

Back-references are commands which refer to a previous part of the matched regualr expression. They are generally specified with a backslash and a single digit `\2`

### Look-ahead and Look-behind

Usually represented with `?=foo`, look-ahead represents what immediately follows the string "foo", while look-behind, the inverse, is notated as `?<=foo` and represents what immediately precedes the string "foo".

## Author

Ryan Messett is a software engineer with a bachelors degree in geology whose interest in the evolution of technology serves to carry our past forawrd through further education and analysis, and into the cutting edge frontier of emerging modern technologies. He currently resides in Austin, TX.

Have additional questions? Click the links below to reach Ryan through his GitHub account or Email address.

[Link to Github](https://github.com/rmessett15)

<a href="mailto:rmessett15@gmail.com">rmessett15@gmail.com</a>
