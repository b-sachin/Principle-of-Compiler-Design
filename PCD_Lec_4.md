# Principles of Compiler Design
# Lecture 4: Introduction to Regular Expressions

**Course:** B.Tech. Information Technology (Semester VII)  
**Subject:** Principles of Compiler Design  
**Lecture No.:** 4  
**Duration:** 60 Minutes

---

# Today's Topic

By the end of this lecture, students will be able to:

- Understand the need for Regular Expressions.
- Define a Regular Expression (RE).
- Explain the basic operators used in RE.
- Construct Regular Expressions for simple patterns.
- Understand the role of RE in Lexical Analysis.

---

# Recap

In the previous lecture, we studied:

- Role of the Lexical Analyzer
- Symbol Table
- Input Buffering
- EOF (Sentinel)

Recall that the Lexical Analyzer scans the source code and generates tokens.

But an important question remains:

> **How does the Lexical Analyzer recognize that a word is an Identifier, Number or Keyword?**

The answer is:

**Using Regular Expressions.**

---

# Introduction

Suppose the compiler reads:

```c
result = a + b * c;
```

It identifies:

```text
result
```

as an Identifier.

But how does it know that "result" is an Identifier?

Because it follows a rule.

That rule is called a **Regular Expression**.

---

# What is a Regular Expression?

## Definition

A **Regular Expression (RE)** is a sequence of symbols that defines a search pattern.

In Compiler Design, a Regular Expression is used to describe the pattern of valid tokens in a programming language.

Simply,

> **Regular Expressions describe what a valid token should look like.**

---

# Real-Life Analogy

Suppose a college issues Roll Numbers.

Valid Roll Numbers:

```text
IT001
IT025
IT120
IT450
```

Invalid Roll Numbers:

```text
001IT
ABC12
IT
```

Instead of writing all valid roll numbers individually, we define a rule:

```text
IT followed by three digits
```

This rule is similar to a Regular Expression.

---

# Why Do We Need Regular Expressions?

Suppose a program contains:

```c
total = marks + bonus;
```

The compiler must identify:

| Lexeme | Token |
|---------|-------|
| total | Identifier |
| marks | Identifier |
| bonus | Identifier |

Instead of storing every possible identifier, the compiler stores a **pattern**.

Whenever a word matches the pattern, it is recognized as an Identifier.

---

# Basic Symbols Used in Regular Expressions

## 1. Literal Characters

A character represents itself.

Example:

```text
a
```

matches only

```text
a
```

---

## 2. Union Operator ( | )

Represents **OR**.

Example:

```text
a|b
```

Matches:

```text
a
```

or

```text
b
```

Examples:

✔ a

✔ b

✘ ab

---

## 3. Concatenation

Writing two expressions together means one follows the other.

Example:

```text
ab
```

Matches:

```text
ab
```

Only.

It does not match

```text
a

or

b
```

---

## 4. Kleene Star ( * )

Means

**Zero or More Occurrences**

Example:

```text
a*
```

Matches:

```text

(empty string)

a

aa

aaa

aaaa
```

All are valid.

---

## 5. Plus Operator ( + )

Means

**One or More Occurrences**

Example:

```text
a+
```

Matches:

```text
a

aa

aaa

aaaa
```

Does **not** match an empty string.

---

## 6. Optional Operator ( ? )

Means

**Zero or One Occurrence**

Example:

```text
a?
```

Matches:

```text

(empty)

a
```

Only.

---

# Understanding Through Examples

## Example 1

Regular Expression:

```text
ab
```

Matches:

```text
ab
```

Does not match:

```text
a

b

abc
```

---

## Example 2

Regular Expression:

```text
a|b
```

Matches:

```text
a

b
```

---

## Example 3

Regular Expression:

```text
a*
```

Matches:

```text

(empty)

a

aa

aaa

aaaa
```

---

## Example 4

Regular Expression:

```text
ab*
```

Meaning:

One **a**

followed by

Zero or More **b**

Matches:

```text
a

ab

abb

abbb

abbbb
```

---

## Example 5

Regular Expression:

```text
(a|b)*
```

Matches:

```text

a

b

ab

ba

aabb

abab

baba
```

Any combination of **a** and **b**.

---

# Regular Expression for Identifiers

General Rule:

```text
letter(letter|digit)*
```

Meaning:

- First character must be a letter.
- Remaining characters can be letters or digits.

Examples:

✔ result

✔ temp1

✔ student25

✔ a

Invalid:

✘ 123abc

✘ 1result

✘ @value

---

# Regular Expression for Integer Numbers

Rule:

```text
digit+
```

Examples:

✔ 10

✔ 25

✔ 1000

✔ 56789

Invalid:

✘ 12A

✘ ABC

---

# Regular Expression for Keywords

Keywords are fixed words.

Examples:

```text
if

while

for

int

return
```

Their Regular Expressions are simply:

```text
if

while

for

int

return
```

No variable pattern is required because keywords are predefined.

---

# Applications of Regular Expressions

Regular Expressions are used in:

- Compiler Design
- Lexical Analysis
- Text Searching
- Search Engines
- Linux grep Command
- Text Editors
- Data Validation
- Email Validation

---

# Advantages

- Easy to describe patterns.
- Simplifies token recognition.
- Used by LEX.
- Forms the basis for Finite Automata.

---

# Limitations

Regular Expressions cannot describe:

- Nested parentheses
- Balanced brackets
- Programming language grammar

These require **Context-Free Grammars**, which we will study later.

---

# Summary

- A Regular Expression describes a pattern.
- The Lexical Analyzer uses RE to recognize tokens.
- Important operators:

| Operator | Meaning |
|----------|----------|
| \| | OR |
| Concatenation | Sequence |
| * | Zero or More |
| + | One or More |
| ? | Optional |

---

# Quick Revision

| Pattern | Matches |
|----------|----------|
| a|b | a or b |
| ab | ab |
| a* | "", a, aa, aaa... |
| a+ | a, aa, aaa... |
| a? | "", a |
| (a|b)* | Any combination of a and b |
| digit+ | Integer Numbers |
| letter(letter\|digit)* | Identifiers |

---

# Questions

### Viva

1. Define Regular Expression.
2. What is Kleene Star?
3. What is Union Operator?
4. Write the Regular Expression for:
   - Identifier
   - Integer
   - Keyword
5. Differentiate between `*` and `+`.
6. What is the role of Regular Expressions in Lexical Analysis?

### 5 Marks

- Explain different operators used in RE.
- Write RE for identifiers and integers.

### 10 Marks

- Explain Regular Expressions with suitable examples.
- Explain the applications of Regular Expressions in Compiler Design.

---

# Assignment

Write Regular Expressions for:

1. Binary numbers
2. Decimal numbers
3. Even binary numbers
4. Identifiers
5. Floating-point numbers (basic form)

---

# Next Lecture

**Regular Expressions to Finite Automata (NFA)**