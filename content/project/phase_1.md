+++
title = "Phase 1"
weight = 10
template = "page.html"
+++
This phase consists of two segments: lexical analysis (aka scanning or lexing) and syntactic analysis (aka parsing).

> **Announcement:** There are three components you need to submit for this phase:
> 1. Your scanner and parser code, due at **10:00 PM on Monday, September 28**.
> 2. A short report, due at **10:00 PM on Monday, September 28**.
> 3. Ten additional test cases, due at **10:00 PM on Monday, September 28**.


## Getting Started

1. Read the [project introduction](@/project/_index.md#introduction).
2. Follow the [setup instructions](@/tutorials/setup.md#tl-dr) to set up your project skeleton.
3. Read and understand the [command-line interface](@/project/cli.md#interface).
4. Read the rest of this handout.


You **must** write your scanner by hand. In previous years, we also suggested using tools like ANTLR4 or flex to help generate the tokenizer code, but this should not be necessary anymore with current LLM coding agents.

You **must** write your parser by hand such as a recursive descent parser. You may not use parser generators. Other hand-written approaches like parser combinators are fine too.

Note that by hand here does not mean you can't use LLM's, just that you can't use external libraries. LLM's are allowed for this assignemnt.

## Language Grammar

### Lexical Considerations

Keywords and identifiers are case-sensitive. For example, **if** is a keyword, but `IF` is an identifier; `foo` and `Foo` are two different identifiers referring to two distinct variables.

The keywords are: **global if else while return fun true false None**

Comments are started by `//` and are terminated by the end of the line.

White space may appear between any lexical tokens (but not within a single token). White space is defined as one or more spaces, tabs, line-break characters (carriage return, line feed, form feed), and comments.

Keywords and identifiers must be separated by white space, or a token that is neither a keyword nor an identifier. For example, `intfortrue` is a single identifier, not three distinct keywords. If a sequence begins with an alphabetic character or an underscore, then it and the longest sequence of alphanumeric characters following it forms a token.

String literals are composed of ⟨char⟩s enclosed in double quotes.

If a sequence begins with a decimal digit, then the longest following sequence of decimal digits forms a decimal integer literal. A long sequence of digits (e.g., `123456789123456789123`) is scanned as a single token.

A ⟨char⟩ is any printable ASCII character (ASCII values between decimal value 32 and 126 inclusive) other than quote (`"`) or backslash (`\`), plus the 2-character sequences `\"` to denote quote, `\\` to denote backslash, `\t` to denote a literal tab, or `\n` to denote newline.

### Reference Grammar

<table>
<thead><tr><th>Notation</th><th>Meaning</th></tr></thead>
<tbody>
<tr><td>$\langle\text{foo}\rangle$</td><td>means foo is a nonterminal.</td></tr>
<tr><td>$\mathbf{foo}$</td><td>(in bold font) means that foo is a terminal.</td></tr>
<tr><td>$\bigl[x\bigr]$</td><td>means zero or one occurrence of x, i.e., x is optional;<br>note that brackets in quotes ′[′ ′]′ are terminals.</td></tr>
<tr><td>$x^{*}$</td><td>means zero or more occurrences of x.</td></tr>
<tr><td>$x^{+}_{\texttt{,}}$</td><td>a comma-separated list of one or more x.<br>note that there is no comma following the last of x.</td></tr>
<tr><td>$\Bigl\{\;\Bigr\}$</td><td>large braces are used for grouping;<br>note that braces in quotes ′{′ ′}′ are terminals.</td></tr>
<tr><td>$\mid$</td><td>separates alternatives.<br>The literal <code>|</code> is also a terminal: MITScript’s conditional OR operator, listed in ⟨cond_op⟩.</td></tr>
</tbody>
</table>

<div class="grammar-scroll" tabindex="0" role="region" aria-label="MITScript reference grammar">
$$
\newcommand{\nt}[1]{\langle\text{#1}\rangle}
\newcommand{\kw}[1]{\mathbf{#1}}
\newcommand{\term}[1]{\texttt{#1}}
\begin{array}{rcl}
\nt{program} &amp; \to &amp; \nt{statement}^{*} \\[0.7em]
\nt{statement} &amp; \to &amp; \nt{location}\;\term{=}\;\nt{expr}\;\term{;} \\
 &amp; | &amp; \nt{call}\;\term{;} \\
 &amp; | &amp; \kw{global}\;\nt{id}\;\term{;} \\
 &amp; | &amp; \kw{if}\;\term{(}\;\nt{expr}\;\term{)}\;\nt{block}\;\bigl[\kw{else}\;\nt{block}\bigr] \\
 &amp; | &amp; \kw{while}\;\term{(}\;\nt{expr}\;\term{)}\;\nt{block} \\
 &amp; | &amp; \kw{return}\;\nt{expr}\;\term{;} \\[0.7em]
\nt{block} &amp; \to &amp; {}'\term{\{}'\;\nt{statement}^{*}\;{}'\term{\}}' \\[0.7em]
\nt{expr} &amp; \to &amp; \kw{fun}\;\term{(}\;\bigl[\nt{id}^{+}_{\term{,}}\bigr]\;\term{)}\;\nt{block} \\
 &amp; | &amp; {}'\term{\{}'\;\Bigl\{\nt{id}\;\term{:}\;\nt{expr}\;\term{;}\Bigr\}^{*}\;{}'\term{\}}' \\
 &amp; | &amp; \nt{simple\_expr} \\[0.7em]
\nt{simple\_expr} &amp; \to &amp; \nt{location} \\
 &amp; | &amp; \nt{call} \\
 &amp; | &amp; \nt{literal} \\
 &amp; | &amp; \term{-}\;\nt{simple\_expr} \\
 &amp; | &amp; \term{!}\;\nt{simple\_expr} \\
 &amp; | &amp; \nt{simple\_expr}\;\nt{bin\_op}\;\nt{simple\_expr} \\
 &amp; | &amp; (\;\nt{simple\_expr}\;) \\[0.7em]
\nt{bin\_op} &amp; \to &amp; \nt{arith\_op}\mid\nt{comp\_op}\mid\nt{cond\_op} \\[0.7em]
\nt{arith\_op} &amp; \to &amp; \term{+}\mid\term{-}\mid\term{*}\mid\term{/} \\[0.7em]
\nt{comp\_op} &amp; \to &amp; \term{&lt;}\mid\term{&gt;}\mid\term{&lt;=}\mid\term{&gt;=}\mid\term{==} \\[0.7em]
\nt{cond\_op} &amp; \to &amp; \term{\&amp;}\mid\term{|} \\[0.7em]
\nt{call} &amp; \to &amp; \nt{location}\;\term{(}\;\bigl[\nt{expr}^{+}_{\term{,}}\bigr]\;\term{)} \\[0.7em]
\nt{location} &amp; \to &amp; \nt{id} \\
 &amp; | &amp; \nt{location}\;\term{.}\;\nt{id} \\
 &amp; | &amp; \nt{location}\;{}'\term{[}'\;\nt{expr}\;{}'\term{]}' \\[0.7em]
\nt{literal} &amp; \to &amp; \nt{int\_literal}\mid\nt{string\_literal}\mid\nt{bool\_literal}\mid\kw{None} \\[0.7em]
\nt{int\_literal} &amp; \to &amp; \nt{digit}\;\nt{digit}^{*} \\[0.7em]
\nt{string\_literal} &amp; \to &amp; \term{"}\;\nt{char}^{*}\;\term{"} \\[0.7em]
\nt{bool\_literal} &amp; \to &amp; \term{true}\mid\term{false} \\[0.7em]
\nt{id} &amp; \to &amp; \nt{alpha}\;\nt{alpha\_num}^{*} \\[0.7em]
\nt{alpha\_num} &amp; \to &amp; \nt{alpha}\mid\nt{digit} \\[0.7em]
\nt{alpha} &amp; \to &amp; \term{a}\mid\term{b}\mid\ldots\mid\term{z}\mid\term{A}\mid\term{B}\mid\ldots\mid\term{Z}\mid\term{\_} \\[0.7em]
\nt{digit} &amp; \to &amp; \term{0}\mid\term{1}\mid\term{2}\mid\ldots\mid\term{9}
\end{array}
$$
</div>

### Operator Precedence and Associativity

Operator precedence is a set of rules that determine the priority with which operators are evaluated in expressions containing multiple operators. Specifically, operators with higher precedence are grouped and applied before those with lower precedence, allowing accurate translation of written formulas into executable behavior without requiring explicit parentheses.

Operator associativity refers to the set of rules that determine the order in which operators of the same precedence are evaluated in an expression. For binary operators, this occurs either left to right or right to left.

Operator precedence is defined in the following order from highest to lowest:

<table>
<thead><tr><th>Operators</th><th>Comments</th></tr></thead>
<tbody>
<tr><td><code>-</code></td><td>unary minus</td></tr>
<tr><td><code>* /</code></td><td>multiplication, division</td></tr>
<tr><td><code>+ -</code></td><td>addition, subtraction</td></tr>
<tr><td><code>&lt; &lt;= &gt;= &gt; ==</code></td><td>relational</td></tr>
<tr><td><code>!</code></td><td>conditional not</td></tr>
<tr><td><code>&amp;</code></td><td>conditional and</td></tr>
<tr><td><code>|</code></td><td>conditional or</td></tr>
</tbody>
</table>

All binary operators are left associative in MITScript.

## Scanner

Your scanner must be able to identify tokens of the MITScript language, the imperative scripting language we will be compiling in 6.112. The scanner should filter out comments and whitespace not in string and character literals.

Your scanner should also note illegal characters, missing quotation marks, and other lexical errors with reasonable error messages. We recommand that your scanner find as many lexical errors as possible, and should be able to continue scanning after errors are found.

When you run the [`./run.sh scan` subcommand](@/project/cli.md#scan), your scanner should show a list of all the tokens it found. Each line shows:
- The line number where the token appears (starting from 1)
- The token type (if it has one)
- The actual text of the token

Use these exact names for the following token types: string literals (`STRINGLITERAL`), integer literals (`INTLITERAL`), boolean literals (`BOOLEANLITERAL`), and identifiers (`IDENTIFIER`).

For string literals, show the exact text as it appears in the code, including the quotes and any escape characters.

Here is an example corresponding to `if (true) {print("Hello, World!");}`:

```sh
1 if
1 (
1 BOOLEANLITERAL true
1 )
1 {
1 IDENTIFIER print
1 (
1 STRINGLITERAL "Hello, World!"
1 )
1 ;
1 }
```

We've provided test files in the `tests` repository. You'll find the expected output for each test file in `.mit.lex` files.

- For lexically valid files, including those with syntax errors: Your scanner output must match our expected output exactly.
- For lexically invalid files: Your scanner just needs to return an error code (non-zero).

## Parser

You need to implement a recursive descent parser. It should correctly parse any valid MITScript program. If a program doesn't follow the grammar rules, your parser should report at least one error.

The boilerplate provided in the skeleton is just there to help you get started, you're free to modify it in any way that fits your needs.

Your parser should construct an abstract syntax tree (AST) that represents the structure of the program. We recommend that your tree should have nodes for each of the following program elements (although you can choose to structure your code slightly differently):

```
Block ::= [Statement]
Global ::= Name
Assignment ::= LHS Expression
CallStatement ::= Expression
IfStatement ::= Condition ThenPart ElsePart
WhileLoop ::= Condition Body
Return ::= Expression
FunctionDeclaration ::= [Arguments] Body
BinaryExpression ::= LeftOperand Operator RightOperand
UnaryExpression ::= Operand Operator
FieldDereference ::= BaseExpression Field
IndexExpression ::= BaseExpression Index
Call ::= TargetExpression [Arguments]
Record ::= Map[String, Expression]
IntegerConstant
StringConstant
NoneConstant
BooleanConstant
```

Make sure arithmetic operators are left-associative. This means `(w+x+y+z)` should be grouped as `(((w+x)+y)+z)`.

You are free to implement your parser as you see fit, provided that you deliver an implementation that uses no additional parsing libraries outside of what you develop yourself.  For example, ANTLR4 (and many other tools and libraries) can be used to automatically generate parsers from a grammar specification. If you would like to use ANTLR4 (or these other tools) to automatically generate a reference, executable parser with which you then compare the outputs of which against that of your manually-developed implementation, then you are free to do so. However, your manually-developed implementation must not use any of the code from these tools in their operation. This restriction does not prevent you from implementing your own helper code, such as implementing your [own parser combinator library](https://theorangeduck.com/page/you-could-have-invented-parser-combinators).

When you run the [`./run.sh parse` subcommand](@/project/cli.md#parse), your parser should show a nicely formatted version of the AST if its valid:
- If the input is valid: Return exit code 0 (success)
- If there are syntax errors: Return a non-zero exit code

## Grading

The grade for this phase is divided into 3 components.

- **90%:** Passing the automated tests for your scanner and parser
- **5%:** Your 10 additional test cases
- **5%:** Your short report (about 3 paragraphs) explaining your approach

The public test cases are available at the [`6112-fa26/tests-fa-26` repository](https://github.com/6112-fa26/tests-fa-26).

**Important:** This year, we have decided to publish a much smaller amount of public tests, so make sure that you thoroughly tests all corner cases with your own testcases. If you have any questions about what the correct behavior of the program should be in certain cases, feel free to ask on Piazza or during Office Hours.

**Important:** Don't copy code from other teams. This counts as cheating. You can look at and discuss other solutions, but the code you submit must be your own work.

## Submission

### Code

Submit your code through Gradescope under Phase 1 using GitHub:

> Gradescope submission link: Will be announced

Check the course [late policy](@/syllabus.md#late-policy) for submission deadlines.

> **Warning:** Make sure the `./build.sh` and `./run.sh` scripts are located at the **root** of your repository.

### Tests

Create 10 test files that are syntactically valid MITScript programs, along with their expected lexer output. The files should be named `test1.mit` through `test10.mit`, with corresponding lexer output files named `test1.mit.lex` through `test10.mit.lex`. Submit all 20 files to the separate Phase 1 tests assignment on Gradescope.

> Gradescope submission link: Will be announced

### Report

Submit a short report (about 3 paragraphs) under Phase 1 Report on Gradescope.

> Gradescope submission link: Will be announced

As a soft rubric, your report should cover:

1. **Implementation.** Explain at a high level how you implemented this phase:
- What data structures did you use (e.g. ASTs)?
- How did you handle and report multiple errors?

2. **Testing and Debugging.** How did you check that your code works correctly?
- Did you write extra test cases? How did you make sure you tested enough?
- What tools or methods helped you find and fix bugs?

3. **Reflection and Project Status.** Be honest about your progress:
- Is everything working? Are there any failing tests or problems you know about?
- If you could start over, what would you do differently?
- Is there anything specific you'd like help with from the TAs?


## Implementation Tips

For this phase, you do not have to worry about reclaiming memory; we will implement garbage collection in a later phase. However, if you're comfortable with smart pointers, you can use them to allocate AST nodes, as they will manage the memory for you. We will review smart pointers in recitation.

Start small. This is true for every phase. Identify subtasks that you can complete end-to-end instead of trying to implement the entire phase for the entirety of MITScript. For example, in 6.102 you built an interpreter for arithmetic. MITScript has arithmetic as well and, therefore, you can check your understanding by implementing an end-to-end implementation of the phase for arithmetic (and whatever limited additional program constructs you need to get it through). For Phase 1, that means first developing a parser for just arithmetic to verify your understanding of the approach.

[s3]: https://studentlife.mit.edu/s3
