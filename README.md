⚙️ Mini-Compiler for $\text{Mini-L}$ (TEC Compiler Design 5KS02)Project OverviewThis repository contains the source code for a Mini-Compiler developed as part of the Compiler Design Teaching Evaluation Component (TEC, Sub Code: 5KS02). The project focuses on building the front-end of a compiler for a custom, simplified language named $\text{Mini-L}$.The primary goal is to translate $\text{Mini-L}$ source code through Lexical and Syntax analysis into Three-Address Code (TAC), a crucial intermediate representation, demonstrating the practical application of formal language theory.🚀 Key ImplementationsThe project successfully implements the following core compiler phases:Lexical Analysis (Scanner): Implemented using Flex. Converts raw source code into a stream of structured tokens using Regular Expressions.Syntax Analysis (Parser): Implemented using Bison. Validates the grammatical structure based on the Context-Free Grammar (CFG).Intermediate Code Generation (ICG): Integrated directly into the parser's semantic actions to generate Three-Address Code (TAC) instructions, managing temporary variables and labels.Symbol Table Management: Basic management of identifier metadata (name, type, scope) is included.$\text{Mini-L}$ Language SpecificationThe custom language $\text{Mini-L}$ is designed to test core compilation concepts. It supports:Data Type: intStatements: Variable declaration, Assignment (=).Expressions: Standard Arithmetic (+, -, *, /).Control Flow: Conditional branching (if-else).📁 Repository ContentsFile NameDescriptionRole in Compilertest.lFlex Input FileDefines the Regular Expressions for all tokens (keywords, identifiers, operators).test.yBison Input FileDefines the CFG rules and contains all semantic actions for TAC generation.custom_functions.cC Source FileContains helper functions for ICG (e.g., generate_TAC(), new_temp()) and Symbol Table logic.test.mlSample Input FileExample source code written in the $\text{Mini-L}$ language for testing.🛠️ Build and Execution Instructions (Linux/WSL)The project requires the Flex and Bison tools, along with the GCC compiler, commonly available on Linux, macOS, or Windows Subsystem for Linux (WSL).1. Generate Compiler ComponentsThe first step is using the compiler construction tools to generate the C source files:Bash# 1. Generate the parser code (y.tab.c and y.tab.h)
bison -d test.y

# 2. Generate the scanner code (lex.yy.c)
flex test.l
2. Compile the ExecutableUse the GCC compiler to link the generated files and the custom C logic into a single executable:Bash# Link all components using GCC (flags -ly and -ll are for Flex/Bison libraries)
gcc -o mini_compiler lex.yy.c y.tab.c custom_functions.c -ly -ll
3. Run the CompilerExecute the compiler by piping the sample $\text{Mini-L}$ source code (test.ml) as input:Bash# Execute the compiler with the test code input
./mini_compiler < test.ml
Expected OutputIf the test.ml file is syntactically correct, the console will display the resulting Three-Address Code (TAC):--- Generated Three-Address Code (TAC) ---
// Example TAC Output:
t1 = 5 * 2
t2 = x + t1
y = t2
if y > 15 goto L1
goto L2
L1: x = 0
L2: x = 1
L3: 
