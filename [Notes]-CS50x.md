# Harvard CS50 - Intro to Computer Science

---

## Lecture 1: Introduction to C Programming

### Compilation Process

- **Source code**: Human-readable code written in C
- **Compiler**: Converts source code into machine-readable binary (executable)
- Machine executes the binary directly

### Data Types

- `bool` - Boolean values (true/false)
- `char` - Single characters
- `int` - Integer values
- `long` - Larger integer values
- `float` - Floating-point numbers
- `double` - Double-precision floating-point numbers
- `string` - Sequences of characters

### Variable Declaration & Initialization

```c
int counter = 0;
string answer = "Hello";
char c = 'Y';
float price = 99.99;
long population = 7800000000;
```

- Variables have **scope**: defined where accessible in code
- Function parameters receive copies of values, not original variables

### Operators

**Arithmetic Operators:**

```c
int sum = 5 + 3;        // Addition: 8
int diff = 10 - 4;      // Subtraction: 6
int product = 6 * 7;    // Multiplication: 42
int quotient = 20 / 4;  // Division: 5
int remainder = 17 % 5; // Modulo: 2
```

**Comparison Operators:**

```c
if (x < y)   // Less than
if (x > y)   // Greater than
if (x <= y)  // Less than or equal
if (x >= y)  // Greater than or equal
if (x == y)  // Equal to (comparison)
if (x != y)  // Not equal to
```

**Logical Operators:**

```c
if (x > 0 && x < 10)  // AND operator
if (c == 'y' || c == 'Y')  // OR operator
if (!(x == y))  // NOT operator
```

**Increment/Decrement:**

```c
counter++;      // Increment by 1
counter--;      // Decrement by 1
counter += 5;   // Add 5 to counter
counter -= 3;   // Subtract 3 from counter
```

### Format Specifiers for printf

```c
printf("%c", 'A');          // Character
printf("%i", 42);           // Integer
printf("%li", 123456789);   // Long integer
printf("%f", 3.14159);      // Float
printf("%s", "Hello");      // String
```

**Example usage:**

```c
int age = 25;
string name = "Alice";
printf("Hello, %s! You are %i years old.\n", name, age);
```

### Conditionals

**If-Else Statements:**

```c
if (x < y)
{
    printf("x is less than y\n");
}
else if (x > y)
{
    printf("x is greater than y\n");
}
else
{
    printf("x equals y\n");
}
```

**Character Comparison:**

```c
char c = 'y';
if (c == 'y' || c == 'Y')
{
    printf("Agreed.\n");
}
else if (c == 'n' || c == 'N')
{
    printf("Not agreed.\n");
}
```

- Single characters use **single quotes** (`'a'`)
- Strings use **double quotes** (`"hello"`)

### Loops

**While Loop:**

```c
int i = 0;
while (i < 5)
{
    printf("Iteration %i\n", i);
    i++;
}
```

**For Loop:**

```c
for (int i = 0; i < 5; i++)
{
    printf("Number: %i\n", i);
}
```

- Initialization: `int i = 0`
- Condition: `i < 5`
- Update: `i++`

**Do-While Loop:**

```c
int n;
do
{
    n = get_int("Enter positive number: ");
}
while (n < 1);
```

- Executes at least once before checking condition
- Useful for input validation

**Loop Control:**

```c
for (int i = 0; i < 10; i++)
{
    if (i == 5)
        break;     // Exit loop completely
    if (i % 2 == 0)
        continue;  // Skip to next iteration
    printf("%i\n", i);
}
```

### Functions

**Function Declaration (Prototype):**

```c
void printMessage(int times);
int add(int a, int b);
```

**Function Definition:**

```c
void printMessage(int times)
{
    for (int i = 0; i < times; i++)
    {
        printf("Hello, World!\n");
    }
}

int add(int a, int b)
{
    return a + b;
}
```

**Complete Example:**

```c
#include <stdio.h>

int square(int n);

int main(void)
{
    int result = square(5);
    printf("Square: %i\n", result);
    return 0;
}

int square(int n)
{
    return n * n;
}
```

- `void` functions don't return values
- Functions with return types must include `return` statement
- Prototypes declare function before `main()`

### Type Casting

```c
int x = 5;
int y = 2;

// Integer division truncates
printf("%i\n", x / y);  // Outputs: 2

// Type casting for floating-point division
printf("%f\n", (float) x / y);  // Outputs: 2.500000
```

### Integer Overflow

```c
int max = 2147483647;  // Maximum signed int value
max++;  // Overflow: wraps to negative value

// Use long for larger values
long big_number = 3000000000;
```

### Nested Loops

**Creating a Grid:**

```c
for (int i = 0; i < 3; i++)
{
    for (int j = 0; j < 3; j++)
    {
        printf("#");
    }
    printf("\n");
}
```

**Output:**
```
###
###
###
```

**Triangle Pattern:**

```c
int height = 5;
for (int i = 1; i <= height; i++)
{
    for (int j = 0; j < i; j++)
    {
        printf("#");
    }
    printf("\n");
}
```

**Output:**
```
#
##
###
####
#####
```

### Constants

```c
const int MAX_SIZE = 100;
const float PI = 3.14159;

// MAX_SIZE = 200;  // Error: cannot modify constant
```

---

## Lecture 2: Arrays, Strings & Debugging

### Debugging Techniques

**1. Printf Debugging:**

```c
int x = 10;
printf("DEBUG: x = %i\n", x);

for (int i = 0; i < 5; i++)
{
    printf("DEBUG: Loop iteration %i\n", i);
}
```

**3. Debugger Tools:**
- Set breakpoints to pause execution
- Step through code line-by-line
- Inspect variable values at specific points

### Compilation Stages

1. **Preprocessing**: Process `#include` directives, copy header contents
2. **Compiling**: Convert source code to assembly language
3. **Assembling**: Transform assembly to machine code (binary)
4. **Linking**: Combine your code with library code into executable

### Arrays

**Declaration and Initialization:**

```c
// Declare array of 5 integers
int numbers[5];

// Initialize values
numbers[0] = 10;
numbers[1] = 20;
numbers[2] = 30;
numbers[3] = 40;
numbers[4] = 50;

// Declare and initialize simultaneously
int scores[3] = {72, 85, 91};
```

**Accessing Elements:**

```c
printf("First score: %i\n", scores[0]);
printf("Second score: %i\n", scores[1]);
```

- Arrays are **zero-indexed**: first element at index 0
- Elements stored sequentially in memory

**Looping Through Arrays:**

```c
int scores[5] = {85, 90, 78, 92, 88};
int sum = 0;

for (int i = 0; i < 5; i++)
{
    sum += scores[i];
}

float average = sum / 5.0;
printf("Average: %.2f\n", average);
```

**Arrays as Function Parameters:**

```c
float calculate_average(int array[], int length)
{
    int sum = 0;
    for (int i = 0; i < length; i++)
    {
        sum += array[i];
    }
    return sum / (float) length;
}

int main(void)
{
    int scores[4] = {85, 92, 78, 95};
    float avg = calculate_average(scores, 4);
    printf("Average: %.2f\n", avg);
}
```

### Strings

**String Fundamentals:**

- Strings are arrays of characters (`char` type)
- End with null terminator `\0` (NUL character)
- Marks where string ends in memory

```c
string name = "Alice";
// Memory: ['A']['l']['i']['c']['e']['\0']

// Access individual characters
printf("%c\n", name[0]);  // Outputs: A
printf("%c\n", name[1]);  // Outputs: l
```

**String as Character Array:**

```c
char greeting[] = "Hello";
printf("%c%c%c%c%c\n", greeting[0], greeting[1],
       greeting[2], greeting[3], greeting[4]);
// Outputs: Hello
```

**String Length:**

```c
#include <string.h>

string text = "Programming";
int length = strlen(text);
printf("Length: %i\n", length);  // Outputs: 11
```

**Iterating Through Strings:**

```c
string word = "CODE";
for (int i = 0; i < strlen(word); i++)
{
    printf("%c\n", word[i]);
}
```

**Optimized String Iteration:**

```c
// Calculate length once instead of every iteration
string word = "Programming";
int len = strlen(word);
for (int i = 0; i < len; i++)
{
    printf("%c ", word[i]);
}
```

### String Manipulation

**Converting to Uppercase:**

```c
#include <ctype.h>
#include <string.h>

string text = "hello world";
int len = strlen(text);

for (int i = 0; i < len; i++)
{
    if (islower(text[i]))
    {
        printf("%c", toupper(text[i]));
    }
    else
    {
        printf("%c", text[i]);
    }
}
// Outputs: HELLO WORLD
```

**Simplified Version:**

```c
for (int i = 0; i < strlen(text); i++)
{
    printf("%c", toupper(text[i]));
}
```

**Character Classification Functions (ctype.h):**

```c
islower(c)   // Check if lowercase letter
isupper(c)   // Check if uppercase letter
isalpha(c)   // Check if alphabetic character
isdigit(c)   // Check if digit
isspace(c)   // Check if whitespace

toupper(c)   // Convert to uppercase
tolower(c)   // Convert to lowercase
```

### Arrays of Strings

```c
string words[3];
words[0] = "Hello";
words[1] = "World";
words[2] = "Program";

// Access characters: words[row][column]
printf("%c\n", words[0][1]);  // 'e' from "Hello"
printf("%c\n", words[1][0]);  // 'W' from "World"
```

**Iterating 2D String Array:**

```c
for (int i = 0; i < 3; i++)
{
    printf("Word %i: %s\n", i, words[i]);
}
```

### Command-Line Arguments

**argc and argv:**

```c
int main(int argc, string argv[])
{
    printf("Argument count: %i\n", argc);

    for (int i = 0; i < argc; i++)
    {
        printf("Argument %i: %s\n", i, argv[i]);
    }
    return 0;
}
```

- `argc`: Argument count (number of arguments)
- `argv`: Argument vector (array of strings)
- `argv[0]`: Program name
- `argv[1]`, `argv[2]`, etc.: User-provided arguments

**Practical Example:**

```c
int main(int argc, string argv[])
{
    if (argc != 2)
    {
        printf("Usage: ./program name\n");
        return 1;
    }

    printf("Hello, %s!\n", argv[1]);
    return 0;
}
```

**Running the program:**
```
$ ./greet Alice
Hello, Alice!

$ ./greet
Usage: ./program name
```

### Exit Status

```c
int main(void)
{
    // Success
    return 0;
}

int main(int argc, string argv[])
{
    if (argc != 2)
    {
        printf("Error: Missing argument\n");
        return 1;  // Error exit code
    }

    // Process argument...
    return 0;  // Success
}
```

- `return 0`: Indicates success
- `return 1` (or non-zero): Indicates error
- Check exit status in terminal: `echo $?`

---

## Lecture 3: Algorithms & Data Structures

### Algorithm Fundamentals

**Definition:**
- Algorithm: Step-by-step procedure to solve a problem
- Input → Black Box (Algorithm) → Output

**Pseudocode:**
- Human-readable instructions before actual code
- Plan logic without syntax constraints
- Example: "For each element, if target found, return position"

### Search Algorithms

**Linear Search:**

```c
// Function to search array
int linear_search(int arr[], int n, int target)
{
    for (int i = 0; i < n; i++)
    {
        if (arr[i] == target)
        {
            return i;  // Return index if found
        }
    }
    return -1;  // Return -1 if not found
}
```

- Examines each element sequentially
- Works on unsorted data
- **Time complexity**: O(n)
- **Best case**: Ω(1) if element is first
- **Worst case**: O(n) if element is last or missing

**Binary Search:**

```c
int binary_search(int arr[], int n, int target)
{
    int left = 0;
    int right = n - 1;

    while (left <= right)
    {
        int middle = (left + right) / 2;

        if (arr[middle] == target)
        {
            return middle;  // Found
        }
        else if (arr[middle] < target)
        {
            left = middle + 1;  // Search right half
        }
        else
        {
            right = middle - 1;  // Search left half
        }
    }
    return -1;  // Not found
}
```

- Requires **sorted array**
- Divides search space in half repeatedly
- **Time complexity**: O(log n)
- Much faster than linear search for large datasets

**Binary Search Pseudocode:**
```
If no elements remain
    Return false
If middle element is target
    Return true
Else if target < middle element
    Search left half
Else if target > middle element
    Search right half
```

### Complexity Analysis

**Big O Notation (Upper Bound - Worst Case):**

- O(n²) - Quadratic time (nested loops)
- O(n log n) - Linearithmic time
- O(n) - Linear time
- O(log n) - Logarithmic time
- O(1) - Constant time

**Omega Notation (Lower Bound - Best Case):**

- Ω(n²), Ω(n), Ω(log n), Ω(1)

**Theta Notation:**

- Θ(n) - When best and worst cases are identical

**Common Complexities:**

```
O(n²)        Slowest (bubble sort, selection sort)
O(n log n)   Efficient sorting (merge sort)
O(n)         Linear scan
O(log n)     Binary search
O(1)         Fastest (direct access)
```

### Sorting Algorithms

**Selection Sort:**

```c
void selection_sort(int arr[], int n)
{
    for (int i = 0; i < n - 1; i++)
    {
        int min_index = i;

        // Find minimum element in unsorted portion
        for (int j = i + 1; j < n; j++)
        {
            if (arr[j] < arr[min_index])
            {
                min_index = j;
            }
        }

        // Swap minimum with first unsorted element
        int temp = arr[i];
        arr[i] = arr[min_index];
        arr[min_index] = temp;
    }
}
```

- Finds minimum element, places at beginning
- Repeats for remaining unsorted elements
- **Time complexity**: O(n²) worst case, Ω(n²) best case
- Not efficient for large datasets

**Bubble Sort:**

```c
void bubble_sort(int arr[], int n)
{
    for (int i = 0; i < n - 1; i++)
    {
        bool swapped = false;

        for (int j = 0; j < n - i - 1; j++)
        {
            // Swap adjacent elements if out of order
            if (arr[j] > arr[j + 1])
            {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = true;
            }
        }

        // If no swaps, array is sorted
        if (!swapped)
            break;
    }
}
```

- Swaps adjacent out-of-order elements repeatedly
- Larger elements "bubble" to end
- **Time complexity**: O(n²) worst case, Ω(n) best case
- Can detect already-sorted arrays

**Merge Sort:**

```c
void merge(int arr[], int left, int mid, int right)
{
    int n1 = mid - left + 1;
    int n2 = right - mid;

    int L[n1], R[n2];

    // Copy data to temp arrays
    for (int i = 0; i < n1; i++)
        L[i] = arr[left + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[mid + 1 + j];

    // Merge temp arrays back
    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2)
    {
        if (L[i] <= R[j])
        {
            arr[k] = L[i];
            i++;
        }
        else
        {
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    // Copy remaining elements
    while (i < n1)
    {
        arr[k] = L[i];
        i++;
        k++;
    }
    while (j < n2)
    {
        arr[k] = R[j];
        j++;
        k++;
    }
}

void merge_sort(int arr[], int left, int right)
{
    if (left < right)
    {
        int mid = left + (right - left) / 2;

        merge_sort(arr, left, mid);        // Sort left half
        merge_sort(arr, mid + 1, right);   // Sort right half
        merge(arr, left, mid, right);      // Merge sorted halves
    }
}
```

- Divides array recursively into halves
- Sorts each half, then merges
- **Time complexity**: O(n log n) worst and best case
- Most efficient of these algorithms
- Requires additional memory for merging

**Sorting Algorithm Comparison:**

| Algorithm      | Best Case | Worst Case | Space     |
|----------------|-----------|------------|-----------|
| Selection Sort | Ω(n²)     | O(n²)      | O(1)      |
| Bubble Sort    | Ω(n)      | O(n²)      | O(1)      |
| Merge Sort     | Ω(n log n)| O(n log n) | O(n)      |

### Recursion

**Fundamental Concept:**
- Function calls itself
- Must have base case (stopping condition)
- Must progress toward base case

**Simple Example - Countdown:**

```c
void countdown(int n)
{
    // Base case
    if (n <= 0)
    {
        printf("Done!\n");
        return;
    }

    // Recursive case
    printf("%i\n", n);
    countdown(n - 1);
}

int main(void)
{
    countdown(5);
    // Outputs: 5 4 3 2 1 Done!
}
```

**Factorial Calculation:**

```c
int factorial(int n)
{
    // Base case
    if (n <= 1)
    {
        return 1;
    }

    // Recursive case
    return n * factorial(n - 1);
}

// factorial(5) = 5 * factorial(4)
//              = 5 * 4 * factorial(3)
//              = 5 * 4 * 3 * factorial(2)
//              = 5 * 4 * 3 * 2 * factorial(1)
//              = 5 * 4 * 3 * 2 * 1
//              = 120
```

**Fibonacci Sequence:**

```c
int fibonacci(int n)
{
    // Base cases
    if (n == 0)
        return 0;
    if (n == 1)
        return 1;

    // Recursive case
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// fibonacci(5) = fibonacci(4) + fibonacci(3)
//              = ... (expands recursively)
//              = 5
```

**Recursive Drawing Example:**

```c
void draw_pyramid(int height)
{
    // Base case
    if (height <= 0)
        return;

    // Recursive case: draw smaller pyramid first
    draw_pyramid(height - 1);

    // Draw current level
    for (int i = 0; i < height; i++)
    {
        printf("#");
    }
    printf("\n");
}

// draw_pyramid(4) outputs:
// #
// ##
// ###
// ####
```

**Key Recursion Principles:**
- **Base case**: Condition that stops recursion
- **Recursive case**: Function calls itself with modified input
- **Progress**: Each recursive call moves toward base case
- **Stack**: Each call stored in memory until base case reached

### Data Structures - Structs

**Defining Custom Types:**

```c
typedef struct
{
    string name;
    int age;
    string email;
} person;
```

**Creating and Using Structs:**

```c
person student;
student.name = "Alice";
student.age = 20;
student.email = "alice@example.com";

printf("Name: %s\n", student.name);
printf("Age: %i\n", student.age);
printf("Email: %s\n", student.email);
```

**Array of Structs:**

```c
person students[3];

students[0].name = "Alice";
students[0].age = 20;

students[1].name = "Bob";
students[1].age = 22;

students[2].name = "Charlie";
students[2].age = 21;

// Loop through array
for (int i = 0; i < 3; i++)
{
    printf("Student: %s, Age: %i\n",
           students[i].name, students[i].age);
}
```

**Phonebook Example:**

```c
typedef struct
{
    string name;
    string number;
} contact;

int main(void)
{
    contact phonebook[2];

    phonebook[0].name = "Alice";
    phonebook[0].number = "555-1234";

    phonebook[1].name = "Bob";
    phonebook[1].number = "555-5678";

    // Search for contact
    string search_name = "Alice";
    for (int i = 0; i < 2; i++)
    {
        if (strcmp(phonebook[i].name, search_name) == 0)
        {
            printf("Found: %s\n", phonebook[i].number);
            return 0;
        }
    }
    printf("Contact not found\n");
    return 1;
}
```

**Benefits of Structs:**
- Group related data together
- Create custom data types
- Improve code organization
- Enable complex data modeling
- Accessed via dot notation (`.`)

---

## Summary of Key Concepts

### Programming Fundamentals
- Data types, variables, operators
- Control flow: conditionals, loops
- Functions and modular code
- Type casting and constants

### Arrays & Strings
- Arrays store sequential data
- Strings are character arrays with `\0` terminator
- String manipulation with `string.h` and `ctype.h`
- Command-line arguments via `argc` and `argv`

### Algorithms
- Linear search: O(n), works on unsorted data
- Binary search: O(log n), requires sorted data
- Selection sort: O(n²)
- Bubble sort: O(n²) worst, Ω(n) best
- Merge sort: O(n log n), most efficient

### Advanced Concepts
- Recursion: base case + recursive case
- Structs: custom data types
- Big O notation: algorithm efficiency analysis
- Debugging:printf, debugger tools

---
