# Experiment 2
# Designing and Implementing Regular Expressions for Regular Languages

---

## Course Information

| Item | Details |
|------|---------|
| **Course Name** | Principles of Compiler Design Lab |
| **Course Code** | 231ITUCL72 |
| **Experiment No.** | 2 |
| **Experiment Title** | Designing and Implementing Regular Expressions for Regular Languages |
| **CO Mapping** | CO1 |
| **Tools Required** | Regex101 (Online Regex Tester) |
| **Prerequisite** | Knowledge of Finite Automata and Regular Languages |

---

# Aim

To design, test, and validate regular expressions for various regular languages using an online regular expression testing tool.

---

# Learning Objectives

After completing this experiment, students will be able to:

- Understand the concept of Regular Expressions.
- Design Regular Expressions for different regular languages.
- Validate Regular Expressions using an online Regex testing tool.
- Differentiate between valid and invalid strings.
- Relate Regular Expressions with Finite Automata.

---

# Software and Tools Required

- Regex101 (https://regex101.com)

---

# Introduction

A **Regular Expression (Regex)** is a sequence of characters that defines a search pattern. Regular Expressions are widely used in Compiler Design during the **Lexical Analysis** phase to identify tokens such as identifiers, keywords, constants, operators, and delimiters.

Instead of checking each character manually, a compiler uses Regular Expressions to efficiently recognize valid patterns in the source program.

For example,

Input:

```text
int total = 100;
```

The lexical analyzer identifies

| Lexeme | Token |
|---------|-------|
| int | Keyword |
| total | Identifier |
| = | Assignment Operator |
| 100 | Integer Constant |
| ; | Delimiter |

Regular Expressions provide the patterns required to identify these tokens automatically.

---

# Relationship Between Regular Expressions and Finite Automata

In the previous experiment, we implemented **Finite Automata**.

Both concepts are closely related.

```
Regular Expression
        ⇅
Finite Automaton
        ⇅
Lexical Analyzer
```

Every Regular Expression can be converted into a Finite Automaton, and every Finite Automaton recognizes a Regular Language.

---

# About Regex101

Regex101 is an online Regular Expression testing tool that allows users to:

- Test Regular Expressions instantly
- Highlight matching text
- Explain every component of the Regular Expression
- Verify valid and invalid inputs
- Debug Regular Expressions interactively

Open the following website in your browser:

> https://regex101.com

---

# Basic Regular Expression Symbols

| Symbol | Meaning | Example |
|----------|---------|----------|
| `.` | Any single character | `a.b` |
| `*` | Zero or more occurrences | `ab*` |
| `+` | One or more occurrences | `ab+` |
| `?` | Zero or one occurrence | `ab?` |
| `[]` | Character Class | `[abc]` |
| `[^ ]` | Negated Character Class | `[^0-9]` |
| `[a-z]` | Lowercase letters | `[a-z]+` |
| `[A-Z]` | Uppercase letters | `[A-Z]+` |
| `[0-9]` | Digits | `[0-9]+` |
| `|` | OR Operator | `cat|dog` |
| `()` | Grouping | `(ab)+` |
| `^` | Beginning of string | `^abc` |
| `$` | End of string | `xyz$` |

---

# Character Classes

## Lowercase Letters

```regex
[a-z]
```

Examples

```
a
m
z
```

---

## Uppercase Letters

```regex
[A-Z]
```

Examples

```
A
M
Z
```

---

## Digits

```regex
[0-9]
```

Examples

```
0
5
9
```

---

## Alphabets

```regex
[a-zA-Z]
```

Examples

```
Compiler
Regex
Student
```

---

## Alphanumeric Characters

```regex
[a-zA-Z0-9]
```

Examples

```
abc123
Student01
IT2026
```

---

# Quantifiers

## Zero or More (*)

```regex
ab*
```

Matches

```
a
ab
abb
abbb
```

---

## One or More (+)

```regex
ab+
```

Matches

```
ab
abb
abbb
```

Does NOT Match

```
a
```

---

## Zero or One (?)

```regex
colou?r
```

Matches

```
color
colour
```

---

# Anchors

## Beginning of String

```regex
^abc
```

Matches

```
abcdef
```

Does NOT Match

```
xabc
```

---

## End of String

```regex
xyz$
```

Matches

```
123xyz
```

Does NOT Match

```
xyz123
```

---

# Complete Match

To match the entire string,

use both anchors.

Example

```regex
^[0-9]+$
```

Matches

```
12345
67890
```

Does NOT Match

```
abc123
123abc
12A45
```

---

# Procedure

1. Open your web browser.
2. Navigate to **https://regex101.com**
3. Select the default Regular Expression flavor.
4. Enter the Regular Expression in the left panel.
5. Enter sample test strings in the right panel.
6. Observe whether each string matches.
7. Modify the expression if required.
8. Record your observations.

---

# Guidelines

- Carefully understand the problem statement before writing the Regular Expression.
- Test both valid and invalid strings.
- Use anchors (`^` and `$`) whenever complete string validation is required.
- Verify the Regular Expression using multiple test cases.
- Record all observations.

---

# Experiment Tasks

In this experiment, students will design and test Regular Expressions for various practical applications.

The tasks are divided into multiple sections.

- Task 1 : Basic Character Matching
- Task 2 : Identifier Recognition
- Task 3 : Integer Recognition
- Task 4 : Floating Point Numbers
- Task 5 : Email Validation
- Task 6 : Mobile Number Validation
- Task 7 : PIN Code Validation
- Task 8 : Date Validation
- Task 9 : Password Validation
- Task 10 : Student Challenge

Each task should be verified using Regex101 with both valid and invalid test cases.

---

---

# Task 1: Match Lowercase Alphabets

## Objective

Design a Regular Expression to recognize strings containing **only lowercase English alphabets**.

---

## Regular Expression

```regex
^[a-z]+$
```

---

## Explanation

| Symbol | Meaning |
|---------|---------|
| `^` | Beginning of string |
| `[a-z]` | Any lowercase alphabet |
| `+` | One or more occurrences |
| `$` | End of string |

---

## Test Cases

| Input | Expected Result |
|---------|----------------|
| compiler | ✅ Match |
| regex | ✅ Match |
| student | ✅ Match |
| Compiler | ❌ No Match |
| abc123 | ❌ No Match |
| 123 | ❌ No Match |

---

## Screenshot

> **Insert Screenshot of Regex101 Output**

---

# Task 2: Match Uppercase Alphabets

## Objective

Design a Regular Expression to recognize strings containing **only uppercase English alphabets**.

---

## Regular Expression

```regex
^[A-Z]+$
```

---

## Test Cases

| Input | Expected Result |
|---------|----------------|
| COMPUTER | ✅ Match |
| IT | ✅ Match |
| DYPATIL | ✅ Match |
| Compiler | ❌ No Match |
| abc | ❌ No Match |
| 123ABC | ❌ No Match |

---

## Screenshot

> **Insert Screenshot of Regex101 Output**

---

# Task 3: Match Integer Numbers

## Objective

Design a Regular Expression to recognize **positive integers**.

---

## Regular Expression

```regex
^[0-9]+$
```

---

## Test Cases

| Input | Expected Result |
|---------|----------------|
| 25 | ✅ Match |
| 100 | ✅ Match |
| 987654 | ✅ Match |
| 12A | ❌ No Match |
| abc | ❌ No Match |
| 10.5 | ❌ No Match |

---

## Screenshot

> **Insert Screenshot of Regex101 Output**

---

# Task 4: Match Valid Identifiers

## Objective

Design a Regular Expression to recognize valid C identifiers.

### Rules

- First character must be a letter or underscore.
- Remaining characters may contain letters, digits or underscore.

---

## Regular Expression

```regex
^[a-zA-Z_][a-zA-Z0-9_]*$
```

---

## Explanation

| Pattern | Meaning |
|----------|---------|
| `[a-zA-Z_]` | First character |
| `[a-zA-Z0-9_]*` | Remaining characters |

---

## Test Cases

| Input | Expected Result |
|---------|----------------|
| total | ✅ Match |
| student1 | ✅ Match |
| _count | ✅ Match |
| roll_no | ✅ Match |
| 1student | ❌ No Match |
| @name | ❌ No Match |
| roll-no | ❌ No Match |

---

## Screenshot

> **Insert Screenshot of Regex101 Output**

---

# Task 5: Match Floating Point Numbers

## Objective

Design a Regular Expression to recognize floating point numbers.

---

## Regular Expression

```regex
^[+-]?[0-9]+\.[0-9]+$
```

---

## Explanation

| Pattern | Meaning |
|----------|---------|
| `[+-]?` | Optional sign |
| `[0-9]+` | Integer part |
| `\.` | Decimal point |
| `[0-9]+` | Fractional part |

---

## Test Cases

| Input | Expected Result |
|---------|----------------|
| 3.14 | ✅ Match |
| -25.50 | ✅ Match |
| +12.75 | ✅ Match |
| 100 | ❌ No Match |
| abc | ❌ No Match |
| 12. | ❌ No Match |

---

## Screenshot

> **Insert Screenshot of Regex101 Output**

---


# Task 6: Match Email Address

## Objective

Design a Regular Expression to recognize valid email addresses.

---

## Regular Expression

```regex
^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```

---

## Explanation

| Pattern | Meaning |
|----------|---------|
| `[a-zA-Z0-9._%+-]+` | Username |
| `@` | Separator |
| `[a-zA-Z0-9.-]+` | Domain Name |
| `\.` | Dot |
| `[a-zA-Z]{2,}` | Domain Extension |

---

## Test Cases

| Input | Expected Result |
|---------|----------------|
| student@gmail.com | ✅ Match |
| abc123@yahoo.com | ✅ Match |
| compiler.lab@rait.ac.in | ✅ Match |
| student@gmail | ❌ No Match |
| @gmail.com | ❌ No Match |
| student.com | ❌ No Match |

---

## Screenshot

> **Insert Screenshot of Regex101 Output**

---

# Task 7: Match Indian Mobile Number

## Objective

Design a Regular Expression to recognize a valid 10-digit Indian mobile number.

---

## Regular Expression

```regex
^[6-9][0-9]{9}$
```

---

## Explanation

| Pattern | Meaning |
|----------|---------|
| `[6-9]` | First digit |
| `[0-9]{9}` | Remaining nine digits |

---

## Test Cases

| Input | Expected Result |
|---------|----------------|
| 9876543210 | ✅ Match |
| 9123456789 | ✅ Match |
| 8234567890 | ✅ Match |
| 5234567890 | ❌ No Match |
| 987654321 | ❌ No Match |
| 98765432101 | ❌ No Match |

---

## Screenshot

> **Insert Screenshot of Regex101 Output**

---

# Task 8: Match Indian PIN Code

## Objective

Design a Regular Expression to recognize a valid six-digit Indian PIN Code.

---

## Regular Expression

```regex
^[1-9][0-9]{5}$
```

---

## Test Cases

| Input | Expected Result |
|---------|----------------|
| 400706 | ✅ Match |
| 421301 | ✅ Match |
| 110001 | ✅ Match |
| 040070 | ❌ No Match |
| 12345 | ❌ No Match |
| 1234567 | ❌ No Match |

---

## Screenshot

> **Insert Screenshot of Regex101 Output**

---

# Task 9: Match Date (DD/MM/YYYY)

## Objective

Design a Regular Expression to recognize dates in the format **DD/MM/YYYY**.

---

## Regular Expression

```regex
^(0[1-9]|[12][0-9]|3[01])/(0[1-9]|1[0-2])/[0-9]{4}$
```

---

## Note

This Regular Expression checks only the **format** of the date.

It does **not** verify whether the date is logically valid.

For example,

```
31/02/2026
```

matches the Regular Expression but is **not** a valid calendar date.

---

## Test Cases

| Input | Expected Result |
|---------|----------------|
| 15/08/2026 | ✅ Match |
| 01/01/2025 | ✅ Match |
| 31/12/2024 | ✅ Match |
| 32/01/2024 | ❌ No Match |
| 15-08-2026 | ❌ No Match |
| 1/1/2026 | ❌ No Match |

---

## Screenshot

> **Insert Screenshot of Regex101 Output**

---

# Task 10: Password Validation

## Objective

Design a Regular Expression for a password satisfying the following conditions:

- Minimum 8 characters
- At least one uppercase letter
- At least one lowercase letter
- At least one digit
- At least one special character

---

## Regular Expression

```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

---

## Test Cases

| Input | Expected Result |
|---------|----------------|
| Password1@ | ✅ Match |
| Compiler@2026 | ✅ Match |
| Admin123# | ❌ No Match (`#` not included in allowed special characters) |
| password1 | ❌ No Match |
| PASSWORD1 | ❌ No Match |
| Pass123 | ❌ No Match |

---

## Screenshot

> **Insert Screenshot of Regex101 Output**

---

# Challenge Exercise

Design Regular Expressions for the following.

1. Vehicle Registration Number

Example

```
MH43AB1234
```

---

2. Roll Number

Example

```
23IT1001
```

---

3. College Email Address

Example

```
student.it@dypatil.edu
```

---

4. PAN Number

Example

```
ABCDE1234F
```

---

5. Aadhaar Number

Example

```
123412341234
```

---

# Observation Table

| Task | Regular Expression Tested | Successful (Yes/No) |
|------|---------------------------|---------------------|
| 1 | Lowercase Alphabets | |
| 2 | Uppercase Alphabets | |
| 3 | Integer Numbers | |
| 4 | Identifiers | |
| 5 | Floating Point Numbers | |
| 6 | Email Address | | |
| 7 | Mobile Number | | |
| 8 | PIN Code | | |
| 9 | Date | | |
| 10 | Password | | |

---

# Conclusion

In this experiment, various Regular Expressions were designed and tested using Regex101.

Different categories of strings such as identifiers, numbers, email addresses, mobile numbers, PIN codes, dates, and passwords were successfully recognized. The experiment demonstrated how Regular Expressions can efficiently describe patterns and how they form the foundation of lexical analysis in compiler design.

---

# Viva Questions

1. What is a Regular Expression?
2. Define a Regular Language.
3. What is the difference between `*` and `+`?
4. What is the purpose of `^` and `$`?
5. What is a Character Class?
6. What is the purpose of Quantifiers?
7. Why are Regular Expressions used in Compiler Design?
8. Which phase of a compiler uses Regular Expressions?
9. What is the difference between a Regular Expression and a Finite Automaton?
10. Can every Regular Expression be converted into a Finite Automaton? Justify your answer.

---

# Submission Requirements

Students must submit:

- Handwritten theory and conclusion page.
- Printed or handwritten Regular Expressions for all tasks.
- Screenshots of Regex101 output for each task.
- Observation tables.

---