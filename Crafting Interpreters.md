#booknote
# Chapter 1
# Chapter 2
- [[Lexical Analysis]] processes the characters in the source code of programming language and converts them into "tokens", groups of characters that are useful in the context of the programming language
- Parsing takes in a flat sequence of tokens from [[Lexical Analysis]] and builds a tree structure, commonly known as [[Abstract Syntax Tree]] based on the programming language's grammar. Parsers also report syntax errors, which are errors when the source code do not abide by the programming language's grammatical rules
- [[Static Analysis]]
	- Every identifier will be linked with its definition, while considering scope
	- If the programming language is statically typed, type checking also happens and type errors are reported
	- Semantic analysis will be stored either as attributes in the [[Abstract Syntax Tree]], or as key-value pairs in a [[Symbol Table]], to match identifiers to what they are referring to
- [[Intermediate Representations]] is not tightly tied to either the source or destination forms
	- Useful for reducing the number of source-destination programming language compiler combinations (i.e. $2N$ frontend and backend implementations instead of $N^2$ source-destination compiler implementations)
	- Optimization is also possible on the [[Intermediate Representations]] (e.g. [[Constant Folding]], where if an expression always evaluates to the same value, the expression can be evaluated once at compile time and have the expression replaced with the result), replacing the original program with another one that has the same semantics and is more efficient
- [[Code Generation]]
	- From the [[Intermediate Representations]], we can either generate machine code, for a real (e.g. [[x86]] or [[ARM]] CPU) or virtual CPU (e.g. [[p-code]] (portable code))
- [[Virtual Machine]]
	- As there are no CPUs that can understand [[p-code]], you will either have to write a compiler to translate the [[p-code]] into native assembly code that targets the CPU, or you can write a [[Virtual Machine]], which is a program that emulates a CPU that supports your [[p-code]]
	- For native code, it will be loaded by the operating system and executed by the CPU. However, for [[p-code]], its runtime will be within the [[Virtual Machine]] that emulates the CPU that supports it
- [[Single-Pass Compilers]] are compilers that combine parsing, [[Static Analysis]] and [[Code Generation]] and produce output code directly, without creating any [[Intermediate Representations]] for multiple passes. This was also likely be due to historic restrictions (i.e. lack of memory to copy entire source file in) in computer specifications
- [[Tree-walk Interpreters]] begin execution of the code right after the [[Abstract Syntax Tree]]s are created during [[Static Analysis]]. The interpreter traverses the [[Abstract Syntax Tree]] and evaluates each node as it goes along
- [[Transpilers]] 