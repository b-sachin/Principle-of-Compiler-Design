# Principles of Compiler Design

# Lecture 1: Introduction to Compiler and Phases of Compiler

# 1. Recap of the Previous Lecture

## Discussion Questions

1. What is a compiler?
2. Why do computers require compilers?
3. What is the difference between a compiler and an interpreter?

---

# 2. Introduction

Consider the following statement:

```c
position = initial + rate * 60;
```

A programmer can easily understand this statement.

However, the CPU cannot understand high-level programming languages such as:

* C
* C++
* Java
* Python

The CPU understands only machine language.

Therefore, the source program must pass through several stages before becoming machine code.

These stages are called **Compiler Phases**.

---

# 3. What is a Compiler?

## Definition

A compiler is a system software that translates a program written in a high-level language into an equivalent machine language program.

---

## Basic Translation Process

```text
Source Program
       ↓
     Compiler
       ↓
 Machine Code
       ↓
      CPU
```

---

# 4. Why Multiple Compiler Phases?

Suppose the compiler receives:

```c
result = a + b * c;
```

The compiler must answer several questions:

1. What are the words in this statement?
2. Is the statement grammatically correct?
3. Does the statement make sense?
4. How can it be represented internally?
5. Can it be optimized?
6. What machine instructions should be generated?

To perform these tasks efficiently, the compiler is divided into phases.

---

# 5. Phases of a Compiler

## Compiler Structure

```text
Source Program
        ↓
Lexical Analysis
        ↓
Syntax Analysis
        ↓
Semantic Analysis
        ↓
Intermediate Code Generation
        ↓
Code Optimization
        ↓
Code Generation
        ↓
Target Program
```

---

# Phase 1: Lexical Analysis

## Definition

Lexical Analysis is the first phase of a compiler.

It reads the source program character by character and converts it into tokens.

---

## Example

Input:

```c
result = a + b * c;
```

Tokens:

```text
result
=
a
+
b
*
c
;
```

---

## Token Representation:

```text
<ID,result>
<ASSIGN,=>
<ID,a>
<PLUS,+>
<ID,b>
<MULT,*>
<ID,c>
<SEMICOLON,;>
```

---

## Analogy

English Sentence:

```text
I love Compiler Design
```

Breaking into words:

```text
I
love
Compiler
Design
```

Lexical Analysis performs a similar task.

---

## Functions of Lexical Analyzer

* Removes white spaces
* Removes comments
* Identifies tokens
* Maintains symbol table entries
* Reports lexical errors

---

# Phase 2: Syntax Analysis

## Definition

Syntax Analysis checks whether the token sequence follows the grammar rules of the language.

It is also known as Parsing.

---

Input:

```text
<ID,result>
<ASSIGN,=>
<ID,a>
<PLUS,+>
<ID,b>
<MULT,*>
<ID,c>
```

The parser verifies whether the statement structure is valid.

---

## Parse Tree

```text
             =
           /   \
      result     +
                / \
               a   *
                  / \
                 b   c
```

---

## Example of Syntax Error

```c
result = + * a b c;
```

The parser reports an error because the structure violates grammar rules.

---

## Functions

* Checks grammatical correctness
* Generates parse tree
* Reports syntax errors

---

# Phase 3: Semantic Analysis

## Definition

Semantic Analysis checks whether the program has meaningful statements.

Even if syntax is correct, meaning may be incorrect.

---

## Example

Correct:

```c
int x;
x = 10;
```

Incorrect:

```c
int x;
x = "Compiler";
```

---

## Why Error?

The variable x is declared as integer but assigned a string value.

---

## Functions

* Type checking
* Scope checking
* Variable declaration checking
* Semantic error detection

---

# Phase 4: Intermediate Code Generation

## Definition

Compiler generates an intermediate representation of the program.

This representation is machine independent.

---

## Example

Input:

```c
a = b + c * d;
```

Intermediate Code:

```text
t1 = c * d
t2 = b + t1
a = t2
```
This is called Three Address Code (TAC).

---

## Advantages

* Easier optimization
* Machine independent representation

---

# Phase 5: Code Optimization

## Definition

Code optimization improves the efficiency of intermediate code.

Goal:

* Faster execution
* Less memory usage

---

## Example

Suppose:

```c
result = a + 5 * 10;
```

Intermediate Code:

```text
t1 = 5 * 10
t2 = a + t1
result = t2
```

Optimized Version:

```text
result = a + 50
```

The compiler reduces unnecessary computations.

---

## Benefits

* Reduced execution time
* Improved performance
* Better memory utilization

---

# Phase 6: Code Generation

## Definition

The optimized intermediate code is translated into machine code.

---

## Example

Input:

```text
t1 = b * c
t2 = a + t1
result = t2
```

Possible Machine Instructions:

```text
LOAD R1,b
MUL R1,c

LOAD R2,a
ADD R2,R1

STORE result
```

Output:

```text
Machine Code
```

---

# 6. Symbol Table

The Symbol Table is a data structure used by the compiler to store information about program identifiers.

---

## Information Stored

| Identifier | Data Type | Scope  |
| ---------- | --------- | ------ |
| a          | int       | Local  |
| b          | float     | Global |

---

## Uses

* Variable lookup
* Type checking
* Memory allocation
* Scope management

---

# 7. Error Handler

Error handling occurs throughout the compilation process.

---

## Types of Errors

### Lexical Error

```c
int @a;
```

---

### Syntax Error

```c
int a =
```

---

### Semantic Error

```c
int a;
a = "Hello";
```

---

# 8. Complete Compiler Structure

```c
result = a + b * c;
```

↓

Lexical Analysis

```text
<ID,result>
<ASSIGN,=>
<ID,a>
<PLUS,+>
<ID,b>
<MULT,*>
<ID,c>
```

↓

Syntax Analysis

```text
Parse Tree Generated
```

↓

Semantic Analysis

```text
Meaning Verified
```

↓

Intermediate Code

```text
t1 = b * c
t2 = a + t1
result = t2
```

↓

Optimization

```text
Optimized Representation
```

↓

Code Generation

```text
Machine Instructions Generated
```

↓

```text
Executable Program
```

---

# 9. Real-World Analogy

Suppose a student writes an English essay.

### Step 1

Identify words.

Equivalent to:

```text
Lexical Analysis
```

### Step 2

Check grammar.

Equivalent to:

```text
Syntax Analysis
```

### Step 3

Check meaning.

Equivalent to:

```text
Semantic Analysis
```

### Step 4

Rewrite in standard format.

Equivalent to:

```text
Intermediate Code
```

### Step 5

Improve language quality.

Equivalent to:

```text
Optimization
```

### Step 6

Publish final version.

Equivalent to:

```text
Code Generation
```

---

# Important Examination Questions

1. Explain Lexical Analysis.
2. Explain Syntax Analysis.
3. Explain Semantic Analysis.
4. Explain Symbol Table.
5. Explain Error Handling.
6. Explain all phases of a compiler with neat diagram.
7. Explain compiler structure with Symbol Table and Error Handler.
8. Describe the functions of each compiler phase.

---

# Summary

* A compiler translates high-level language into machine language.
* Compilation is divided into multiple phases.
* Lexical Analysis generates tokens.
* Syntax Analysis checks grammar.
* Semantic Analysis checks meaning.
* Intermediate Code Generation produces machine-independent code.
* Optimization improves performance.
* Code Generation creates machine instructions.
* Symbol Table and Error Handler support all phases.

---
