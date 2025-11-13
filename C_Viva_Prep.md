# C Language Viva Preparation Guide (Units I-III)

This guide covers the essential topics for your C language viva, focusing on Units I, II, and III of your syllabus, including Recursion.

---

## Unit I: Introduction to Computing

### Basic Computer Organization
**Brief:** A computer system is composed of hardware and software. Hardware includes input devices, output devices, CPU (ALU, Control Unit, Registers), memory (RAM, ROM), and storage devices. Software includes operating systems and application programs.
**Example:**
- **Input Devices:** Keyboard, Mouse
- **Output Devices:** Monitor, Printer
- **CPU:** The "brain" that executes instructions.
- **Memory (RAM):** Volatile storage for active programs and data.
- **Storage (HDD/SSD):** Non-volatile storage for long-term data.

**Question:** What is the primary function of the CPU?
**Answer:** The CPU (Central Processing Unit) is responsible for executing instructions, performing arithmetic and logical operations, and managing the overall flow of data and control in a computer system.

### Evolution of Programming Languages
**Brief:** Programming languages have evolved through generations:
1.  **First Generation (1GL):** Machine Language (binary code, 0s and 1s).
2.  **Second Generation (2GL):** Assembly Language (mnemonics like ADD, MOV).
3.  **Third Generation (3GL):** High-level languages (C, C++, Java, Python) - more human-readable, machine-independent.
4.  **Fourth Generation (4GL):** Domain-specific languages, often for database management or report generation (e.g., SQL).
5.  **Fifth Generation (5GL):** AI-based languages, often used for problem-solving and constraint-based programming (e.g., Prolog, OPS5).
**Question:** Why are high-level languages preferred over machine language for programming?
**Answer:** High-level languages are preferred because they are more human-readable, easier to write, debug, and maintain. They are also machine-independent, meaning code written in a high-level language can be compiled and run on different types of computers with minimal changes, unlike machine language which is specific to a particular CPU architecture.

### Data Representation and Storage
**Brief:** Computers store and process data in binary format (bits: 0 or 1). Various schemes are used to represent different data types:
-   **Integers:** Signed magnitude, one's complement, two's complement (most common).
-   **Floating-point numbers:** IEEE 754 standard (single-precision float, double-precision double).
-   **Characters:** ASCII, Unicode.
**Example:**
-   The integer `5` in binary (8-bit) is `00000101`.
-   The character 'A' in ASCII is `01000001` (decimal 65).
**Question:** How are negative integers typically represented in computers?
**Answer:** Negative integers are most commonly represented using the **two's complement** method. This method allows for efficient arithmetic operations and avoids the issue of having two representations for zero.

### Basics of Programming Environment: Editors, Debuggers, Translators
**Brief:**
-   **Editors:** Software used to write and modify source code (e.g., VS Code, Vim, Emacs).
-   **Debuggers:** Tools used to find and fix errors (bugs) in programs by allowing step-by-step execution, inspecting variables, etc. (e.g., GDB for C).
-   **Translators:** Convert source code into machine-executable code.
    -   **Compilers:** Translate the entire program at once (e.g., GCC for C).
    -   **Interpreters:** Translate and execute code line by line.
    -   **Assemblers:** Translate assembly language into machine code.
**Question:** What is the difference between a compiler and an interpreter?
**Answer:** A **compiler** translates the entire source code into machine code before execution, creating an executable file. An **interpreter** translates and executes the source code line by line, without creating a separate executable file. Compilers generally result in faster execution, while interpreters offer more flexibility during development.

### Basics of Program Design and Execution
**Brief:**
-   **Design:** Involves understanding requirements, breaking down problems into smaller modules, and planning the logic (e.g., using algorithms, pseudocode, flowcharts).
-   **Execution:** The process of running a compiled or interpreted program. For compiled languages like C, it involves compilation, linking, and then running the executable.
**Question:** What are the main stages in the execution of a C program?
**Answer:** The main stages are:
1.  **Preprocessing:** Handles preprocessor directives (e.g., `#include`, `#define`).
2.  **Compilation:** Translates preprocessed code into assembly code.
3.  **Assembly:** Converts assembly code into machine code (object file).
4.  **Linking:** Combines object files with necessary library functions to create an executable file.
5.  **Execution:** The operating system loads the executable into memory and runs it.

### Algorithms, Pseudocode and Flowcharts
**Brief:**
-   **Algorithm:** A step-by-step procedure to solve a problem. It must be unambiguous, finite, and effective.
-   **Pseudocode:** An informal high-level description of an algorithm, using a mix of natural language and programming constructs.
-   **Flowchart:** A graphical representation of an algorithm, using standard symbols to depict steps and decision points.
**Example (Algorithm for adding two numbers):**
1.  Start
2.  Read num1
3.  Read num2
4.  Calculate sum = num1 + num2
5.  Print sum
6.  End
**Example (Pseudocode for adding two numbers):**
```
BEGIN
  READ num1
  READ num2
  SET sum = num1 + num2
  PRINT sum
END
```
**Question:** What is the purpose of an algorithm?
**Answer:** The purpose of an algorithm is to provide a clear, unambiguous, and finite set of instructions to solve a specific problem or perform a computation. It serves as a blueprint for writing programs.

---

## Unit II: C Programming Fundamentals

### Data Types and Type Conversion
**Brief:** C has basic data types:
-   **Integer types:** `int`, `short`, `long`, `long long` (signed/unsigned variants).
-   **Floating-point types:** `float`, `double`, `long double`.
-   **Character type:** `char`.
-   **Void type:** `void` (for functions that return nothing, or generic pointers).
**Type Conversion:**
-   **Implicit (Coercion):** Done automatically by the compiler (e.g., `int` to `float`).
-   **Explicit (Casting):** Done by the programmer using a cast operator (e.g., `(float)int_var`).
**Code Example:**
```c
#include <stdio.h>

int main() {
    int a = 10;
    float b = 3.5;
    float sum_implicit = a + b; // int 'a' is implicitly converted to float
    int sum_explicit = a + (int)b; // float 'b' is explicitly converted to int

    printf("Implicit sum: %.2f\n", sum_implicit); // Output: 13.50
    printf("Explicit sum: %d\n", sum_explicit);   // Output: 13
    return 0;
}
```
**Output:**
```
Implicit sum: 13.50
Explicit sum: 13
```
**Error Finding Practice:**
```c
#include <stdio.h>

int main() {
    char c = 'A';
    int i = 10;
    float f = 20.5;
    double d = 30.75;

    // What will be the output of these?
    printf("Result 1: %d\n", c + i);
    printf("Result 2: %f\n", i + f);
    printf("Result 3: %lf\n", f + d);
    printf("Result 4: %c\n", i + c); // Potential error/unexpected behavior
    return 0;
}
```
**Analysis:**
-   `c + i`: 'A' (ASCII 65) + 10 = 75. Prints as `int`.
-   `i + f`: 10 (converted to float) + 20.5 = 30.5. Prints as `float`.
-   `f + d`: 20.5 (converted to double) + 30.75 = 51.25. Prints as `double`.
-   `i + c`: 10 + 'A' (65) = 75. Prints as `char`. This will print the character corresponding to ASCII 75, which is 'K'. Not an error, but might be unexpected if one thought it would print 'A' then '10'.
**Corrected Output:**
```
Result 1: 75
Result 2: 30.500000
Result 3: 51.250000
Result 4: K
```
**Question:** Explain the concept of "data type promotion" in C.
**Answer:** Data type promotion (or implicit type conversion) occurs when an operation involves operands of different data types. The compiler automatically converts the "smaller" or "lower" data type to the "larger" or "higher" data type to prevent loss of data. For example, if an `int` and a `float` are involved in an operation, the `int` will be promoted to a `float`.

### Variables (declaration vs definition, local vs global), Keywords, Header Files, Structure of a C Program
**Brief:**
-   **Declaration:** Announces the name and type of a variable to the compiler (e.g., `extern int count;`).
-   **Definition:** Allocates memory for the variable and optionally initializes it (e.g., `int count = 0;`). A variable can be declared multiple times but defined only once.
-   **Local Variables:** Declared inside a function or block; scope is limited to that block.
-   **Global Variables:** Declared outside any function; scope is throughout the program.
-   **Keywords:** Reserved words with special meaning (e.g., `int`, `if`, `while`, `return`).
-   **Header Files:** Contain function declarations, macro definitions, and type definitions (e.g., `stdio.h` for input/output functions). Included using `#include`.
-   **Structure of a C Program:**
    1.  Preprocessor Directives (`#include`, `#define`)
    2.  Global Declarations (variables, functions)
    3.  `main()` function (entry point)
    4.  Other User-Defined Functions
**Code Example:**
```c
#include <stdio.h> // Header file

int global_var = 100; // Global variable definition

void myFunction() {
    int local_var = 50; // Local variable definition
    printf("Inside myFunction - local_var: %d, global_var: %d\n", local_var, global_var);
}

int main() { // main function
    int main_local_var = 10; // Local variable definition
    printf("Inside main - main_local_var: %d, global_var: %d\n", main_local_var, global_var);
    myFunction();
    // printf("%d\n", local_var); // Error: local_var is not accessible here
    return 0;
}
```
**Output:**
```
Inside main - main_local_var: 10, global_var: 100
Inside myFunction - local_var: 50, global_var: 100
```
**Error Finding Practice:**
```c
#include <stdio.h>

// int x; // Global declaration

void func1() {
    int y = 20;
    printf("y in func1: %d\n", y);
}

void func2() {
    // printf("y in func2: %d\n", y); // Error: y is local to func1
    int x = 30; // Local variable, shadows global x if it existed
    printf("x in func2: %d\n", x);
}

int main() {
    // printf("x in main: %d\n", x); // Error: x is not defined globally or locally here
    func1();
    func2();
    return 0;
}
```
**Analysis:**
-   The commented `int x;` if uncommented, would make `x` a global variable.
-   `y` is local to `func1` and cannot be accessed in `func2`.
-   `x` inside `func2` is a local variable, distinct from any potential global `x`.
-   `x` in `main` would be an error if no global `x` is defined.
**Corrected Code (assuming global `x` is intended):**
```c
#include <stdio.h>

int x = 10; // Global variable definition

void func1() {
    int y = 20;
    printf("y in func1: %d\n", y);
    printf("x in func1: %d\n", x); // Accessing global x
}

void func2() {
    // printf("y in func2: %d\n", y); // Still an error
    int x = 30; // Local variable, shadows global x
    printf("Local x in func2: %d\n", x);
    printf("Global x in func2 (if accessed via scope resolution, not directly in C): %d\n", x); // This line is misleading, C doesn't have direct scope resolution for shadowed globals like C++
}

int main() {
    printf("x in main: %d\n", x); // Accessing global x
    func1();
    func2();
    return 0;
}
```
**Question:** What is the purpose of a header file in C?
**Answer:** Header files (`.h` files) in C contain declarations of functions, macros, and data types that are used across multiple source files. They allow for modular programming by providing interfaces to libraries and other parts of the code, ensuring consistency and making compilation more efficient.

### Operators: types of operators, operator precedence and associativity
**Brief:**
-   **Arithmetic:** `+`, `-`, `*`, `/`, `%`
-   **Relational:** `==`, `!=`, `>`, `<`, `>=`, `<=`
-   **Logical:** `&&` (AND), `||` (OR), `!` (NOT)
-   **Bit-wise:** `&` (AND), `|` (OR), `^` (XOR), `~` (NOT), `<<` (left shift), `>>` (right shift)
-   **Increment/Decrement:** `++`, `--` (prefix/postfix)
-   **Assignment:** `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `&=`, `|=`, `^=`, `<<=`, `>>=`
-   **`sizeof`:** Returns the size of a variable or type.
-   **Ternary (Conditional):** `condition ? expression1 : expression2`
**Precedence:** Determines the order in which operators are evaluated (e.g., `*` before `+`).
**Associativity:** Determines the order of evaluation for operators of the same precedence (e.g., left-to-right for `+`, right-to-left for assignment).
**Code Example:**
```c
#include <stdio.h>

int main() {
    int a = 10, b = 5, c = 2;
    int result;

    // Arithmetic
    result = a + b * c; // 10 + (5 * 2) = 20 (precedence: * before +)
    printf("a + b * c = %d\n", result); // Output: 20

    // Relational and Logical
    if (a > b && b != c) { // (true && true) = true
        printf("a is greater than b AND b is not equal to c\n");
    }

    // Ternary
    result = (a > b) ? a : b; // 10 > 5 is true, so result = a (10)
    printf("Max of a and b: %d\n", result); // Output: 10

    // Bitwise
    int x = 5; // 0101
    int y = 3; // 0011
    result = x & y; // 0001 (1)
    printf("x & y = %d\n", result); // Output: 1

    return 0;
}
```
**Output:**
```
a + b * c = 20
a is greater than b AND b is not equal to c
Max of a and b: 10
x & y = 1
```
**Error Finding Practice:**
```c
#include <stdio.h>

int main() {
    int p = 10, q = 3;
    float r;

    r = p / q; // Integer division, then assigned to float
    printf("r = %f\n", r); // Expected: 3.000000

    int s = 5;
    int t = s++; // Post-increment
    printf("s = %d, t = %d\n", s, t); // Expected: s=6, t=5

    int u = 5;
    int v = ++u; // Pre-increment
    printf("u = %d, v = %d\n", u, v); // Expected: u=6, v=6

    if (p == 10 || q = 5) { // Logical OR, but assignment instead of comparison
        printf("Condition met\n");
    } else {
        printf("Condition not met\n");
    }

    return 0;
}
```
**Analysis:**
-   `r = p / q;`: `p / q` performs integer division (10 / 3 = 3), then 3 is assigned to `r` and promoted to `3.0`.
-   `t = s++;`: `t` gets the value of `s` (5) *before* `s` is incremented. So `t=5`, `s=6`.
-   `v = ++u;`: `u` is incremented *before* its value is assigned to `v`. So `u=6`, `v=6`.
-   `if (p == 10 || q = 5)`: This is a common error. `q = 5` is an assignment, not a comparison. It assigns 5 to `q`, and the result of the assignment (5) is treated as `true` in a boolean context. This condition will always be true. It should be `q == 5`.
**Corrected Output (with `q == 5` fix):**
```
r = 3.000000
s = 6, t = 5
u = 6, v = 6
Condition met
```
**Question:** Explain the difference between `++i` and `i++`.
**Answer:**
-   `++i` (pre-increment): The value of `i` is incremented *before* it is used in the expression.
-   `i++` (post-increment): The value of `i` is used in the expression *before* it is incremented.

### Conditional Statements: if, else, switch-case, break, continue, goto, label. Loops: for, while and do-while.
**Brief:**
-   **`if-else`:** Executes a block of code based on a condition.
-   **`switch-case`:** Multi-way branch statement, useful for selecting one of many code blocks to execute based on the value of an expression.
-   **`break`:** Exits the innermost loop or `switch` statement.
-   **`continue`:** Skips the rest of the current iteration of a loop and proceeds to the next iteration.
-   **`goto` and `label`:** Unconditional jump statement. Generally discouraged due to making code hard to read and maintain.
-   **`for` loop:** Used when the number of iterations is known.
-   **`while` loop:** Executes as long as a condition is true; condition checked at the beginning.
-   **`do-while` loop:** Executes at least once, then continues as long as a condition is true; condition checked at the end.
**Code Example:**
```c
#include <stdio.h> 

int main() {
    int choice = 2;
    int i = 0;

    // Switch-case
    switch (choice) {
        case 1:
            printf("Choice is 1\n");
            break;
        case 2:
            printf("Choice is 2\n");
            // No break here, will fall through to default
        default:
            printf("Default choice\n");
    }

    // For loop with continue
    for (i = 0; i < 5; i++) {
        if (i == 2) {
            continue; // Skip printing for i=2
        }
        printf("For loop i: %d\n", i);
    }

    // While loop
    i = 0;
    while (i < 3) {
        printf("While loop i: %d\n", i);
        i++;
    }

    // Do-while loop
    i = 0;
    do {
        printf("Do-while loop i: %d\n", i);
        i++;
    } while (i < 0); // Condition is false, but executes once

    return 0;
}
```
**Output:**
```
Choice is 2
Default choice
For loop i: 0
For loop i: 1
For loop i: 3
For loop i: 4
While loop i: 0
While loop i: 1
While loop i: 2
Do-while loop i: 0
```
**Error Finding Practice:**
```c
#include <stdio.h>

int main() {
    int x = 10;

    if (x = 5) { // Assignment instead of comparison
        printf("x is 5\n");
    } else {
        printf("x is not 5\n");
    }

    int j = 0;
    while (j < 5) {
        printf("j: %d\n", j);
        // Missing increment for j, infinite loop
    }

    int k = 0;
    switch (k) {
        case 0:
            printf("Case 0\n");
        case 1:
            printf("Case 1\n"); // Missing break
        default:
            printf("Default\n");
    }

    return 0;
}
```
**Analysis:**
-   `if (x = 5)`: This assigns 5 to `x`, and the result (5) is true, so "x is 5" will always print. Should be `x == 5`.
-   `while (j < 5)`: `j` is never incremented, leading to an infinite loop.
-   `switch (k)`: Missing `break` statements in `case 0` and `case 1` will cause "fall-through", printing "Case 0", "Case 1", and "Default".
**Corrected Code:**
```c
#include <stdio.h>

int main() {
    int x = 10;

    if (x == 5) { // Corrected comparison
        printf("x is 5\n");
    } else {
        printf("x is not 5 (it's %d)\n", x);
    }

    int j = 0;
    while (j < 5) {
        printf("j: %d\n", j);
        j++; // Added increment
    }

    int k = 0;
    switch (k) {
        case 0:
            printf("Case 0\n");
            break; // Added break
        case 1:
            printf("Case 1\n");
            break; // Added break
        default:
            printf("Default\n");
    }

    return 0;
}
```
**Question:** When would you use a `do-while` loop instead of a `while` loop?
**Answer:** A `do-while` loop is used when you need to ensure that the loop body executes at least once, regardless of whether the condition is initially true or false. The condition is checked *after* the first iteration. A `while` loop, on the other hand, checks the condition *before* the first iteration, so its body might not execute at all if the condition is initially false.

---

## Unit III: Array and Function

### Array
**Brief:** A collection of elements of the same data type, stored in contiguous memory locations. Elements are accessed using an index (0-based).
**Declaration:** `dataType arrayName[size];`
**Initialization:** `int arr[5] = {10, 20, 30, 40, 50};` or `int arr[] = {10, 20, 30};`
**Code Example:**
```c
#include <stdio.h>

int main() {
    int numbers[5]; // Declare an integer array of size 5

    // Initialize elements
    numbers[0] = 10;
    numbers[1] = 20;
    numbers[2] = 30;
    numbers[3] = 40;
    numbers[4] = 50;

    // Access and print elements
    printf("Elements of the array: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n"); // Output: 10 20 30 40 50 

    // Array initialization at declaration
    float grades[] = {90.5, 88.0, 92.3};
    printf("Grades: %.1f, %.1f, %.1f\n", grades[0], grades[1], grades[2]); // Output: 90.5, 88.0, 92.3

    return 0;
}
```
**Output:**
```
Elements of the array: 10 20 30 40 50 
Grades: 90.5, 88.0, 92.3
```
**Error Finding Practice:**
```c
#include <stdio.h>

int main() {
    int data[3] = {1, 2, 3};

    // Accessing out-of-bounds
    printf("data[3] = %d\n", data[3]); // Error: Array index out of bounds

    // Trying to assign more elements than declared size
    // int small_arr[2] = {10, 20, 30}; // Compiler error: too many initializers

    // Incorrect loop condition
    for (int i = 0; i <= 3; i++) { // Loop goes one element too far
        printf("%d ", data[i]);
    }
    printf("\n");

    return 0;
}
```
**Analysis:**
-   `data[3]`: Accessing `data[3]` is out of bounds for an array of size 3 (valid indices are 0, 1, 2). This leads to undefined behavior (might print garbage or crash).
-   `int small_arr[2] = {10, 20, 30};`: This would be a compile-time error as you are trying to initialize an array of size 2 with 3 elements.
-   `for (int i = 0; i <= 3; i++)`: The loop condition `i <= 3` means it will try to access `data[3]`, which is out of bounds. Should be `i < 3`.
**Corrected Code:**
```c
#include <stdio.h>

int main() {
    int data[3] = {1, 2, 3};

    // Corrected access
    printf("data[2] = %d\n", data[2]); // Accessing last valid element

    // Corrected loop condition
    for (int i = 0; i < 3; i++) { // Loop iterates for indices 0, 1, 2
        printf("%d ", data[i]);
    }
    printf("\n");

    return 0;
}
```
**Question:** What is the significance of 0-based indexing in C arrays?
**Answer:** 0-based indexing means that the first element of an array is at index 0, the second at index 1, and so on. For an array of size `N`, the valid indices range from `0` to `N-1`. This is a fundamental convention in C and many other programming languages, closely tied to how memory addresses are calculated for array elements.

### Multi-dimensional Arrays
**Brief:** Arrays of arrays. Most commonly 2D arrays (matrices).
**Declaration:** `dataType arrayName[rowSize][colSize];`
**Initialization:** `int matrix[2][3] = {{1, 2, 3}, {4, 5, 6}};`
**Code Example:**
```c
#include <stdio.h>

int main() {
    int matrix[2][3] = {{1, 2, 3}, {4, 5, 6}};

    printf("Matrix elements:\n");
    for (int i = 0; i < 2; i++) { // Iterate through rows
        for (int j = 0; j < 3; j++) { // Iterate through columns
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    return 0;
}
```
**Output:**
```
Matrix elements:
1 2 3 
4 5 6 
```
**Question:** How are multi-dimensional arrays stored in memory in C?
**Answer:** In C, multi-dimensional arrays are stored in row-major order. This means that all elements of the first row are stored contiguously, followed by all elements of the second row, and so on.

### Strings
**Brief:** In C, strings are arrays of characters terminated by a null character (`\0`).
**Declaration:** `char str[size];`
**Initialization:** `char name[] = "John";` or `char city[10] = {'N', 'e', 'w', ' ', 'Y', 'o', 'r', 'k', '\0'};`
**Standard Library Functions (from `string.h`):** `strlen()`, `strcpy()`, `strcat()`, `strcmp()`.
**Code Example:**
```c
#include <stdio.h>
#include <string.h> // For string functions

int main() {
    char greeting[] = "Hello";
    char name[20]; // Declare a character array for name
    char full_message[50];

    printf("Enter your name: ");
    scanf("%s", name); // Read name (be careful with buffer overflow for scanf %s)

    printf("Greeting: %s\n", greeting); // Output: Hello
    printf("Name: %s\n", name);

    // Concatenate strings
    strcpy(full_message, greeting); // Copy "Hello" to full_message
    strcat(full_message, ", ");     // Concatenate ", "
    strcat(full_message, name);     // Concatenate name
    printf("Full message: %s\n", full_message);

    printf("Length of greeting: %lu\n", strlen(greeting)); // Output: 5

    return 0;
}
```
**Output (assuming user enters "Alice"):**
```
Enter your name: Alice
Greeting: Hello
Name: Alice
Full message: Hello, Alice
Length of greeting: 5
```
**Error Finding Practice:**
```c
#include <stdio.h> 
#include <string.h>

int main() {
    char s1[5] = "Hello"; // Error: "Hello" needs 6 bytes (5 for chars + 1 for \0)
    char s2[10];

    // strcpy(s2, "A very long string that won't fit"); // Buffer overflow
    // printf("%s\n", s1);

    if (s1 == "Hello") { // Incorrect string comparison
        printf("s1 is Hello\n");
    } else {
        printf("s1 is not Hello\n");
    }

    return 0;
}
```
**Analysis:**
-   `char s1[5] = "Hello";`: This is a buffer overflow. "Hello" requires 5 characters + 1 null terminator (`\0`), so 6 bytes. Declaring `s1` with size 5 will truncate the null terminator or cause undefined behavior.
-   `strcpy(s2, "A very long string that won't fit");`: This would cause a buffer overflow if `s2` is not large enough.
-   `if (s1 == "Hello")`: This compares the *memory addresses* of `s1` and the string literal "Hello", not their content. It will almost always be false. Use `strcmp()` for string comparison.
**Corrected Code:**
```c
#include <stdio.h>
#include <string.h>

int main() {
    char s1[6] = "Hello"; // Corrected size to accommodate null terminator
    char s2[50]; // Sufficient size for longer strings

    printf("%s\n", s1);

    if (strcmp(s1, "Hello") == 0) { // Corrected string comparison
        printf("s1 is Hello\n");
    } else {
        printf("s1 is not Hello\n");
    }

    strcpy(s2, "A short string"); // Example of safe copy
    printf("%s\n", s2);

    return 0;
}
```
**Question:** What is the role of the null character (`\0`) in C strings?
**Answer:** The null character (`\0`) marks the end of a string in C. It is crucial for string manipulation functions (like `strlen`, `strcpy`, `strcat`) to know where the string terminates. Without it, these functions would continue reading memory until they encounter a random null byte, leading to incorrect results or crashes.

### Function
**Brief:** A block of code that performs a specific task. Functions promote modularity, reusability, and readability.
**Components:**
-   **Function Declaration (Prototype):** Tells the compiler about the function's name, return type, and parameters.
-   **Function Definition:** Contains the actual code of the function.
-   **Function Call:** Invokes the function.
**Code Example:**
```c
#include <stdio.h> 

// Function Declaration (Prototype)
int add(int a, int b);

int main() {
    int num1 = 5, num2 = 3;
    int sum;

    // Function Call
    sum = add(num1, num2);
    printf("Sum: %d\n", sum); // Output: 8
    return 0;
}

// Function Definition
int add(int a, int b) {
    return a + b;
}
```
**Output:**
```
Sum: 8
```
**Question:** What is the purpose of a function prototype?
**Answer:** A function prototype (or declaration) informs the compiler about a function's existence, its return type, and the types and order of its parameters before the function is actually defined. This allows the compiler to perform type checking during function calls and ensures that the function is called correctly, even if its definition appears later in the file or in another file.

### Pass and Return by Value, Pass and Return by Reference
**Brief:**
-   **Pass by Value:** A copy of the argument's value is passed to the function. Changes to the parameter inside the function do not affect the original argument.
-   **Pass by Reference (using Pointers):** The memory address of the argument is passed to the function. The function can then use this address (pointer) to directly access and modify the original argument.
-   **Return by Value:** The function returns a copy of a value.
-   **Return by Reference (not directly supported for local variables in C, but can return pointers to dynamically allocated memory or global variables):** A function can return a pointer to a variable, allowing the caller to modify the original data.
**Code Example (Pass by Value vs. Reference):**
```c
#include <stdio.h>

// Pass by Value
void incrementByValue(int num) {
    num++; // Modifies the copy
    printf("Inside incrementByValue: %d\n", num);
}

// Pass by Reference (using pointer)
void incrementByReference(int *numPtr) {
    (*numPtr)++; // Modifies the original variable through its address
    printf("Inside incrementByReference: %d\n", *numPtr);
}

int main() {
    int x = 10;
    printf("Before incrementByValue: %d\n", x); // Output: 10
    incrementByValue(x);
    printf("After incrementByValue: %d\n", x);  // Output: 10 (original x is unchanged)

    int y = 20;
    printf("Before incrementByReference: %d\n", y); // Output: 20
    incrementByReference(&y); // Pass the address of y
    printf("After incrementByReference: %d\n", y); // Output: 21 (original y is changed)

    return 0;
}
```
**Output:**
```
Before incrementByValue: 10
Inside incrementByValue: 11
After incrementByValue: 10
Before incrementByReference: 20
Inside incrementByReference: 21
After incrementByReference: 21
```
**Question:** When would you choose to pass an argument by reference instead of by value?
**Answer:** You would choose to pass an argument by reference (using pointers) when:
1.  You need to modify the original value of the argument within the function.
2.  You want to avoid copying large data structures (like arrays or structs) to improve performance, as passing a pointer is more efficient.
3.  A function needs to "return" multiple values (by modifying multiple arguments passed by reference).

### Recursion
**Brief:** A function that calls itself, either directly or indirectly, to solve a problem. Each recursive call solves a smaller subproblem until a base case is reached, which stops the recursion.
**Key elements:**
-   **Base Case:** A condition that stops the recursion.
-   **Recursive Step:** The function calls itself with a modified input, moving closer to the base case.
**Code Example (Factorial):**
```c
#include <stdio.h> 

// Recursive function to calculate factorial
long long factorial(int n) {
    // Base case: if n is 0 or 1, factorial is 1
    if (n == 0 || n == 1) {
        return 1;
    }
    // Recursive step: n * factorial(n-1)
    return n * factorial(n - 1);
}

int main() {
    int num = 5;
    printf("Factorial of %d is %lld\n", num, factorial(num)); // Output: 120

    num = 0;
    printf("Factorial of %d is %lld\n", num, factorial(num)); // Output: 1

    return 0;
}
```
**Output:**
```
Factorial of 5 is 120
Factorial of 0 is 1
```
**Error Finding Practice:**
```c
#include <stdio.h>

// Function to print numbers recursively (missing base case)
void printNumbers(int n) {
    printf("%d ", n);
    printNumbers(n + 1); // Infinite recursion if no base case
}

// Function to calculate sum (incorrect base case or recursive step)
int sumNumbers(int n) {
    if (n == 0) {
        return 0;
    }
    return n + sumNumbers(n); // Error: n is not decreasing, infinite recursion
}

int main() {
    // printNumbers(1); // This would cause a stack overflow
    // printf("\n");

    // printf("Sum: %d\n", sumNumbers(3)); // This would also cause a stack overflow

    return 0;
}
```
**Analysis:**
-   `printNumbers(int n)`: Lacks a base case. `n` keeps increasing, leading to infinite recursion and a stack overflow.
-   `sumNumbers(int n)`: The recursive step `sumNumbers(n)` does not change `n`, so it never reaches the base case `n == 0` (unless `n` is initially 0). This also leads to infinite recursion and a stack overflow.
**Corrected Code:**
```c
#include <stdio.h>

// Corrected function to print numbers recursively
void printNumbers(int n) {
    if (n > 5) { // Base case: stop when n is greater than 5
        return;
    }
    printf("%d ", n);
    printNumbers(n + 1);
}

// Corrected function to calculate sum recursively
int sumNumbers(int n) {
    if (n == 0) { // Base case
        return 0;
    }
    return n + sumNumbers(n - 1); // Recursive step: n decreases
}

int main() {
    printf("Printing numbers: ");
    printNumbers(1);
    printf("\n"); // Output: 1 2 3 4 5 

    printf("Sum of numbers up to 3: %d\n", sumNumbers(3)); // Output: 6 (3+2+1+0)

    return 0;
}
```
**Question:** What is a stack overflow error in the context of recursion?
**Answer:** A stack overflow error occurs in recursion when a function calls itself too many times without reaching a base case, or if the base case is incorrect. Each function call consumes memory on the call stack. If the recursion is infinite or too deep, the call stack runs out of space, leading to a stack overflow error and program termination.

### Scope Rules
**Brief:** Determine the visibility and lifetime of identifiers (variables, functions) in a program.
-   **Block Scope (Local):** Variables declared inside a block `{}` are only visible and exist within that block.
-   **Function Scope:** Labels (`goto` labels) have function scope.
-   **File Scope (Global):** Variables declared outside any function are visible from their point of declaration to the end of the file.
-   **Program Scope:** Global variables and functions that are visible across multiple source files (if declared `extern` and defined once).
**Code Example:**
```c
#include <stdio.h> 

int global_var = 10; // File scope

void func() {
    int func_var = 20; // Block scope (function block)
    printf("In func: global_var = %d, func_var = %d\n", global_var, func_var);
    {
        int block_var = 30; // Inner block scope
        printf("In inner block: block_var = %d\n", block_var);
    }
    // printf("%d\n", block_var); // Error: block_var not visible here
}

int main() {
    int main_var = 40; // Block scope (main function block)
    printf("In main: global_var = %d, main_var = %d\n", global_var, main_var);
    func();
    // printf("%d\n", func_var); // Error: func_var not visible here
    return 0;
}
```
**Output:**
```
In main: global_var = 10, main_var = 40
In func: global_var = 10, func_var = 20
In inner block: block_var = 30
```
**Question:** Differentiate between the lifetime and scope of a variable.
**Answer:**
-   **Scope:** Refers to the region of the program where a variable can be accessed or referenced. It determines the visibility of the variable.
-   **Lifetime:** Refers to the period during which a variable exists in memory. For local variables, lifetime is typically from function entry to function exit. For global variables, lifetime is the entire duration of the program.

---

## Viva Questions (General)

### Unit I: Introduction to Computing
1.  **Q:** What is the difference between hardware and software?
    **A:** Hardware refers to the physical components of a computer system (e.g., CPU, memory, keyboard), while software refers to the programs and data that instruct the hardware (e.g., operating system, applications).
2.  **Q:** Can you name a 2GL and a 3GL language and briefly explain their characteristics?
    **A:** 2GL: Assembly language (uses mnemonics, machine-dependent, low-level control). 3GL: C (high-level, human-readable, machine-independent, requires compilation).
3.  **Q:** How does a computer represent text characters internally?
    **A:** Text characters are represented using character encoding schemes like ASCII or Unicode, where each character is mapped to a unique numerical value, which is then stored in binary.
4.  **Q:** What is the role of a linker in the program execution process?
    **A:** The linker combines the object files generated by the compiler with necessary library functions and other object files to produce a single executable program. It resolves references between different code modules.
5.  **Q:** When would you use a flowchart over pseudocode, or vice-versa?
    **A:** Flowcharts are good for visualizing the flow of control and decision points, especially for simpler algorithms, and are easily understood by non-programmers. Pseudocode is better for complex algorithms, detailed logic, and is closer to actual code, making it easier for programmers to translate into a specific language.

### Unit II: C Programming Fundamentals
1.  **Q:** What is a keyword in C? Give two examples.
    **A:** A keyword is a reserved word in C that has a predefined meaning to the compiler and cannot be used as an identifier (variable name, function name, etc.). Examples: `int`, `if`, `while`, `return`.
2.  **Q:** Explain the concept of operator precedence and associativity with an example.
    **A:** **Precedence** determines which operator is evaluated first in an expression with multiple operators (e.g., `*` has higher precedence than `+`, so `2 + 3 * 4` evaluates to `14`). **Associativity** determines the order of evaluation for operators of the same precedence (e.g., `+` is left-to-right, so `a - b + c` is `(a - b) + c`; assignment `=` is right-to-left, so `a = b = 5` means `b = 5` then `a = b`).
3.  **Q:** What is "fall-through" in a `switch` statement and how can it be prevented?
    **A:** "Fall-through" occurs in a `switch` statement when, after a `case` block is executed, the program continues to execute the code in the subsequent `case` blocks because there is no `break` statement. It can be prevented by explicitly adding a `break` statement at the end of each `case` block (unless fall-through is intentionally desired).
4.  **Q:** When is a `goto` statement useful, and why is it generally discouraged?
    **A:** `goto` can be useful in very specific scenarios like breaking out of deeply nested loops or handling error conditions by jumping to a cleanup section. However, it is generally discouraged because it makes code harder to read, debug, and maintain by creating unstructured "spaghetti code" that jumps arbitrarily, violating principles of structured programming.
5.  **Q: `int x = 5; int y = 2; float result = (float)x / y;` What is the value of `result` and why?**
    **A:** `result` will be `2.5`. The `(float)x` explicitly casts `x` to a float, making the division a floating-point division (`5.0 / 2`), which yields `2.5`. Without the cast, it would be integer division (`5 / 2 = 2`), and `result` would be `2.0`.

### Unit III: Array and Function
1.  **Q:** How do you declare and initialize a 2D array in C?
    **A:** Declaration: `int matrix[3][4];`. Initialization: `int matrix[2][3] = {{1, 2, 3}, {4, 5, 6}};`
2.  **Q:** What is the difference between `char name[] = "Alice";` and `char *name = "Alice";`?
    **A:**
    -   `char name[] = "Alice";`: `name` is an array of characters. The string "Alice" is stored in mutable memory (usually on the stack). You can modify individual characters (e.g., `name[0] = 'B';`).
    -   `char *name = "Alice";`: `name` is a pointer to a character. The string literal "Alice" is stored in read-only memory. `name` points to the first character of this literal. You cannot modify the string content through this pointer (e.g., `*name = 'B';` would result in a runtime error).
3.  **Q:** Explain the concept of a "dangling pointer" in C. (Though pointers are Unit IV, this can come up if discussing pass by reference or returning addresses).
    **A:** A dangling pointer is a pointer that points to a memory location that has been deallocated or no longer exists. If a function returns the address of a local variable (which is deallocated when the function exits), the pointer in the calling function becomes dangling. Accessing memory through a dangling pointer leads to undefined behavior.
4.  **Q:** What are the advantages of using functions in C programming?
    **A:** Functions offer several advantages:
    -   **Modularity:** Breaking down a large program into smaller, manageable functions.
    -   **Reusability:** Functions can be called multiple times from different parts of the program or even in other programs.
    -   **Readability:** Makes code easier to understand and follow.
    -   **Maintainability:** Easier to debug and modify specific parts of the code.
    -   **Abstraction:** Hides implementation details from the caller.
5.  **Q:** Write a recursive function to calculate the sum of natural numbers up to `n`.
    **A:**
    ```c
    int sum_recursive(int n) {
        if (n == 0) { // Base case
            return 0;
        }
        return n + sum_recursive(n - 1); // Recursive step
    }
    ```
    **Explanation:** If `n` is 0, the sum is 0. Otherwise, it's `n` plus the sum of numbers up to `n-1`.

---

Good luck with your viva! You've got this.

```