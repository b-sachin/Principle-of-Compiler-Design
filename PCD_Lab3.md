# Experiment 3
# Design of Lexical Analyzer to Recognize the Patterns of Strings using LEX

---

## Course Information

| Item | Details |
|------|---------|
| **Course Name** | Principles of Compiler Design Lab |
| **Course Code** | 231ITUCL72 |
| **Experiment No.** | 3 |
| **Experiment Title** | Design of Lexical Analyzer to Recognize the Patterns of Strings using LEX |
| **CO Mapping** | CO2 |

---

# Aim

To design and implement a lexical analyzer using **LEX (Flex)** for recognizing keywords, identifiers, and integer constants.

---

# Software Requirements

Students will perform this experiment on **Windows** using **Windows Subsystem for Linux (WSL)**.

Required Software:

- Windows 10 / Windows 11
- Windows Terminal or Command Prompt
- WSL (Ubuntu)
- Flex
- GCC Compiler
- Visual Studio Code (Recommended)

---

# Theory

The **Lexical Analyzer** is the first phase of a compiler.

It reads the source program character by character and groups them into meaningful units called **tokens**.

Examples of tokens include:

- Keywords
- Identifiers
- Constants
- Operators
- Delimiters

Instead of writing the scanner manually, compiler developers use **LEX (Flex)**.

LEX accepts **Regular Expressions** as input and automatically generates a C program that performs lexical analysis.

---

# LEX Workflow

```
Source Program
      │
      ▼
LEX Program (.l)
      │
      ▼
Flex
      │
      ▼
lex.yy.c
      │
      ▼
GCC Compiler
      │
      ▼
Executable Scanner
```

---

# One-Time Setup (Windows)

## Step 1: Install WSL

Open **PowerShell as Administrator**

Execute

```powershell
wsl --install
```

Restart the computer after installation.

---

## Step 2: Verify WSL Installation

Open Windows Terminal

Execute

```bash
wsl
```

If Ubuntu opens successfully,

the installation is complete.

---

## Step 3: Update Ubuntu

```bash
sudo apt update

sudo apt upgrade -y
```

---

## Step 4: Install Flex

```bash
sudo apt install flex -y
```

---

## Step 5: Install GCC

```bash
sudo apt install gcc -y
```

---

## Step 6: Verify Installation

```bash
flex --version
```

Example Output

```
flex 2.6.x
```

---

Verify GCC

```bash
gcc --version
```

---

# Creating the LEX Program

Open Visual Studio Code.

Create a folder

```
CompilerLab
```

Inside the folder,

create a file named

```
experiment3.l
```

---

# LEX Program

Copy the following program.

```lex
%{

#include<stdio.h>

%}

%%

int|float|char
{
    printf("Keyword : %s\n", yytext);
}

[a-zA-Z_][a-zA-Z0-9_]*
{
    printf("Identifier : %s\n", yytext);
}

[0-9]+
{
    printf("Integer : %s\n", yytext);
}

[ \t\n]+
{
    /* Ignore white spaces */
}

.
{
    printf("Unknown Token : %s\n", yytext);
}

%%

int main()
{
    printf("Enter Source Code:\n\n");

    yylex();

    return 0;
}

int yywrap()
{
    return 1;
}
```

---

# Explanation

The scanner recognizes

| Pattern | Token |
|----------|-------|
| int | Keyword |
| float | Keyword |
| char | Keyword |
| total | Identifier |
| number123 | Identifier |
| 100 | Integer Constant |

Any character that does not match the above rules is reported as an **Unknown Token**.

---

# Compiling the Program

Open Ubuntu (WSL).

Navigate to your project folder.

Example

```bash
cd /mnt/c/Users/<YourUserName>/Documents/CompilerLab
```

Generate C source code.

```bash
flex experiment3.l
```

A new file will be created.

```
lex.yy.c
```

---

Compile the generated C file.

```bash
gcc lex.yy.c -o scanner -lfl
```

This creates an executable named

```
scanner
```

---

Run the scanner.

```bash
./scanner
```

---

# Sample Input

```
int total = 100;

char grade;

float marks;
```

---

# Expected Output

```
Keyword : int

Identifier : total

Unknown Token : =

Integer : 100

Unknown Token : ;

Keyword : char

Identifier : grade

Unknown Token : ;

Keyword : float

Identifier : marks

Unknown Token : ;
```

---

# Observation

Notice that

```
=
```

and

```
;
```

are reported as

```
Unknown Token
```

This is because we have **not yet written rules** to recognize operators and delimiters.

Students will extend the scanner in future experiments.

---

---

# Activity 1: Recognizing Arithmetic Operators

Modify the **Rules Section** by adding the following rule **before** the `Unknown Token` rule.

```lex
"+"|"-"|"*"|"/"|"%"
{
    printf("Arithmetic Operator : %s\n", yytext);
}
```

---

## Test Input

```
a + b * c - 20 / 5
```

---

## Expected Output

```
Identifier : a

Arithmetic Operator : +

Identifier : b

Arithmetic Operator : *

Identifier : c

Arithmetic Operator : -

Integer : 20

Arithmetic Operator : /

Integer : 5
```

---

# Activity 2: Recognizing Delimiters

Add the following rule before the `Unknown Token` rule.

```lex
";"|","|"("|")"|"{"|"}"
{
    printf("Delimiter : %s\n", yytext);
}
```

---

## Test Input

```c
int main()
{
}
```

---

## Expected Output

```
Keyword : int

Identifier : main

Delimiter : (

Delimiter : )

Delimiter : {

Delimiter : }
```

---

# Activity 3: Testing the Scanner

Test the scanner using the following source code.

```c
int age = 20;

float salary = 25000;

char grade;
```

---

## Expected Output

```
Keyword : int

Identifier : age

Unknown Token : =

Integer : 20

Delimiter : ;

Keyword : float

Identifier : salary

Unknown Token : =

Integer : 25000

Delimiter : ;

Keyword : char

Identifier : grade

Delimiter : ;
```

---

# Student Exercise

Modify the scanner to recognize the following keywords.

```
if

else

while

for

return
```

Verify the output using suitable test cases.

---

# Additional Exercise

Add support for the following operators.

```
==

!=

<

>

<=

>=
```

Test your scanner with appropriate input.

---

# Observation Table

| Test Case | Description | Status (✓/✗) |
|-----------|-------------|--------------|
| 1 | Keyword Recognition | |
| 2 | Identifier Recognition | |
| 3 | Integer Recognition | |
| 4 | Arithmetic Operator Recognition | |
| 5 | Delimiter Recognition | |

---

# Precautions

- Ensure that Flex and GCC are installed correctly before compiling.
- Save the LEX program with the **`.l`** extension.
- Compile the program every time changes are made.
- Place keyword rules before identifier rules to obtain correct output.
- Verify the program using different input test cases.

---

# Common Errors and Troubleshooting

| Error | Possible Cause | Solution |
|--------|----------------|----------|
| `flex: command not found` | Flex is not installed | Install Flex using `sudo apt install flex` |
| `gcc: command not found` | GCC is not installed | Install GCC using `sudo apt install gcc` |
| `undefined reference to yywrap` | Missing `yywrap()` function | Add the `yywrap()` function to the program |
| Incorrect token identified | Rule order is incorrect | Place specific rules before general rules |

---

# Viva Questions

1. What is a lexical analyzer?
2. What is the purpose of LEX (Flex)?
3. What is a token?
4. What is the purpose of `yytext`?
5. What does the `yylex()` function do?
6. Why is the `yywrap()` function required?
7. Why should keyword rules be written before identifier rules?
8. What file is generated after executing the `flex` command?
9. Which compiler is used to compile the generated C program?
10. Name any four types of tokens recognized by a lexical analyzer.

---

# Result

A lexical analyzer was successfully designed and implemented using **LEX (Flex)**. The scanner correctly recognized keywords, identifiers, integer constants, arithmetic operators, and delimiters from the input source program.

---

# Conclusion

In this experiment, students learned the basic structure of a LEX program and successfully generated a lexical analyzer using Flex. The experiment demonstrated how Regular Expressions can be used to recognize different token types, providing the foundation for the lexical analysis phase of a compiler.

---