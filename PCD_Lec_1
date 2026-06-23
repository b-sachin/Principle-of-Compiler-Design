# Principles of Compiler Design

## Lecture 0: Introduction to Compiler Design

# 1. Introduction

Whenever we write a program in a programming language such as C, C++, Java, or Python, the computer cannot directly understand it.

Computers understand only machine language (binary instructions consisting of 0s and 1s).

Therefore, a translator is required to convert human-readable programs into machine-readable instructions.

This translator is known as a **Compiler**.

---

# 2. Why Do We Need a Compiler?

Consider the following C program:

```c
int a = 10;
int b = 20;
int c = a + b;
```

Humans can easily understand this code.

However, the CPU cannot understand statements such as:

```c
int a = 10;
```

The CPU understands only machine instructions.

Therefore:

```text
Source Program
      ↓
Compiler
      ↓
Machine Code
      ↓
CPU Execution
```

A compiler acts as a bridge between programmers and computers.

---

# 3. Real-Life Analogy

Suppose a person speaks English and another person understands only Marathi.

A translator is required.

```text
English
    ↓
Translator
    ↓
Marathi
```

Similarly,

```text
C Program
     ↓
Compiler
     ↓
Machine Code
```

Thus, a compiler is a language translator.

---

# 4. What is a Compiler?

## Definition

A compiler is a system software that translates a program written in a high-level programming language into an equivalent machine language program.

### Examples

* GCC Compiler (C/C++)
* Clang Compiler
* Java Compiler (javac)
* Go Compiler
* Rust Compiler

---

# 5. Compiler vs Interpreter

Both are language translators.

Their method of execution differs.

## Compiler

A compiler translates the entire program before execution.

```text
Source Program
       ↓
Compiler
       ↓
Executable File
       ↓
Execution
```

### Examples

* C
* C++
* Go
* Rust

### Advantages

* Faster execution
* Optimized machine code
* Executable can run independently

---

## Interpreter

An interpreter translates and executes the program step by step.

```text
Source Program
       ↓
Interpreter
       ↓
Execution
```

### Examples

* Python
* JavaScript

### Advantages

* Easier debugging
* Platform independent

---

## Comparison

| Compiler                       | Interpreter                          |
| ------------------------------ | ------------------------------------ |
| Translates entire program      | Translates statement by statement    |
| Generates executable file      | Usually does not generate executable |
| Faster execution               | Slower execution                     |
| Errors shown after compilation | Errors shown immediately             |
| Example: C, C++                | Example: Python, JavaScript          |

---

# 6. Modern View of Language Translation

In reality, modern programming languages use a combination of compilation and interpretation.

### Java

```text
Java Source Code
        ↓
javac Compiler
        ↓
Bytecode
        ↓
JVM
        ↓
Machine Code
```

### Python

```text
Python Source Code
        ↓
Bytecode Compilation
        ↓
Python Virtual Machine
        ↓
Execution
```

For simplicity, Java is often called a compiled language and Python an interpreted language.

---

# 7. What Will We Learn in This Course?

Compiler construction is divided into multiple stages.

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

Each module of this course focuses on one stage of this process.

---

# 8. Course Modules Overview

## Module 1

### Lexical Analysis

Topics:

* Tokens
* Lexemes
* Regular Expressions
* Finite Automata
* LEX Tool

---

## Module 2

### Syntax Analysis

Topics:

* Context Free Grammar
* Parse Trees
* Top Down Parsing
* Bottom Up Parsing
* LR Parsing

---

## Module 3

### Syntax Directed Translation

Topics:

* Syntax Directed Definitions
* Syntax Trees
* Attributes
* Translation Schemes

---

## Module 4

### Type Checking and Intermediate Code Generation

Topics:

* Type Systems
* Type Checking
* Intermediate Languages
* Three Address Code

---

## Module 5

### Runtime Environment and Code Generation

Topics:

* Storage Allocation
* Symbol Tables
* Basic Blocks
* Flow Graphs
* Register Allocation
---

## Module 6

### Machine Independent Optimization

Topics:

* Code Optimization
* Data Flow Analysis
* Optimization Techniques

---

# 9. Applications of Compiler Design

Compiler concepts are widely used in:

* Programming Language Development
* IDEs and Code Editors
* Static Code Analysis
* Search Engines
* SQL Query Optimization
* Artificial Intelligence Systems
* Auto-completion Tools
* Operating Systems
* Embedded Systems
---

# Summary

* Computers understand only machine language.
* Compilers translate high-level programs into machine code.
* Interpreters execute programs step-by-step.
* Compiler Design studies how this translation process works.
* The subject consists of six major modules covering lexical analysis, parsing, translation, code generation, and optimization.

---
