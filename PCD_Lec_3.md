# Principles of Compiler Design
# Lecture 3: Role of Lexical Analyzer, Symbol Table and Input Buffering

**Course:** B.Tech Information Technology (Semester VII)  
**Lecture:** 3

---

## Today's Topic

- Explain the role of the Lexical Analyzer.
- Describe the Symbol Table.
- Explain Input Buffering.
- Understand Single Buffer and Double Buffer schemes.
- Explain the purpose of EOF (Sentinel).

---

# 1. Role of the Lexical Analyzer

The Lexical Analyzer is the first phase of the compiler. It reads the source program, scans it character by character, groups characters into meaningful units called **tokens**, and passes these tokens to the Syntax Analyzer.

## Functions

- Reads the source program.
- Generates tokens.
- Removes white spaces.
- Removes comments.
- Maintains the Symbol Table.
- Reports lexical errors.

---

# 2. Why Character-by-Character Scanning?

Consider:

```c
result = a + b * c;
```

The compiler does **not** receive words. It receives only a stream of characters.

```text
r e s u l t   =   a   +   b   *   c ;
```

The compiler scans characters until it finds the end of a token.

Example:

```text
r
re
res
resu
resul
result
(space)
```

When the space is encountered, the compiler concludes that **result** is an identifier and generates:

```text
<ID, result>
```

### Why not read word by word?

Example:

```c
a+b*c;
```

There are no spaces.

If the compiler tried to read words, it would read:

```text
a+b*c;
```

as one word, which is incorrect.

Similarly,

```c
count++;
```

must be recognized as:

```text
count
++
```

and

```c
x<=10;
```

must recognize `<=` as a single operator.

Hence, lexical analysis always scans **character by character**.

---

# 3. Token Generation

Input:

```c
result = a + b * c;
```

Output:

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

# 4. Symbol Table

The Symbol Table stores information about identifiers.

Example:

```c
int result;
int a;
int b;
```

| Identifier | Type | Scope |
|------------|------|-------|
| result | int | Global |
| a | int | Global |
| b | int | Global |

### Difference Between Token and Symbol Table

| Token | Symbol Table |
|-------|--------------|
| Represents category | Stores detailed information |
| Example: `result → ID` | Name, Type, Scope, Address |

---

# 5. Lexical Errors

Example:

```c
int @result;
```

Output:

```text
Lexical Error: Invalid Symbol '@'
```

---

# 6. Input Buffering

Reading one character from the disk at a time is slow because every read requires an operating system call.

Instead, the compiler loads a large block of characters into memory.

```text
Source File
      │
      ▼
Input Buffer
      │
      ▼
Lexical Analyzer
```

The compiler **fetches data in blocks** but **processes it character by character**.

---

# 7. Single Buffer

```text
+----------------+
|    Buffer      |
+----------------+
        │
        ▼
Lexical Analyzer
```

When the buffer becomes empty, the compiler waits until it is refilled.

---

# 8. Double Buffer

```text
+------------+    +------------+
| Buffer A   |    | Buffer B   |
+------------+    +------------+

        │
        ▼
Lexical Analyzer
```

While one buffer is processed, the other is refilled.

Advantages:

- Reduces waiting time.
- Improves compilation speed.

---

# 9. EOF (Sentinel)

After loading the last part of the source program into memory, the compiler places a special marker called **EOF (End of File)**.

Conceptually:

```text
result = a + b * c ; EOF
```

EOF is **not written by the programmer**. It is added internally by the compiler/runtime system.

Purpose:

- Indicates the end of input.
- Eliminates repeated end-of-buffer checking.
- Improves efficiency.

---

# 10. Complete Working

```text
Source Program
      │
      ▼
Input Buffer
      │
      ▼
Lexical Analyzer
 ├──────────────► Token Stream
 ├──────────────► Symbol Table
 └──────────────► Error Messages
      │
      ▼
Syntax Analyzer
```

---

# Key Points

- The Lexical Analyzer is the first phase of the compiler.
- It scans the source code character by character.
- It generates tokens and maintains the Symbol Table.
- Input buffering improves efficiency by reducing disk access.
- Double buffering reduces waiting time.
- EOF is an internal marker indicating the end of input.

---

# Questions

## Viva

1. Define Lexical Analyzer.
2. What is a Symbol Table?
3. What is Input Buffering?
4. Define EOF.

## 5 Marks

1. Explain the functions of the Lexical Analyzer.
2. Explain the Symbol Table.
3. Explain Input Buffering.

## 10 Marks

1. Explain the role of the Lexical Analyzer with a neat diagram.
2. Explain the Double Buffer Scheme with the Sentinel (EOF) technique.

---

# Assignment

For the following program:

```c
int sum;
sum = a + b;
```

1. Identify all tokens.
2. List the Symbol Table entries.
3. Explain why character-by-character scanning is necessary.
4. State the advantages of input buffering.
