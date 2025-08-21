# MINGGU 4: TIPE DATA, VARIABEL, OPERATOR, EKSPRESI
## Mata Kuliah: Logika dan Algoritma Pemrograman

---

## **TUJUAN PEMBELAJARAN**

Setelah mengikuti pembelajaran pada minggu ini, mahasiswa diharapkan dapat:

1. **Memahami konsep identifiers dan keywords** dalam bahasa pemrograman
2. **Menguasai tipe data dasar** (int, float, char, double, boolean) dan penggunaannya
3. **Menggunakan variabel dan konstanta** dengan benar termasuk scope dan lifetime
4. **Mengaplikasikan berbagai jenis operator** (aritmatika, logika, relasional, bitwise)
5. **Mengevaluasi ekspresi** dengan memahami operator precedence dan associativity

---

## **BAGIAN 1: IDENTIFIERS DAN KEYWORDS**

### **1.1 Konsep Identifiers**

Identifiers adalah nama yang digunakan programmer untuk mengidentifikasi variabel, fungsi, konstanta, atau entitas program lainnya. Identifiers adalah fondamental dalam programming karena memungkinkan kita untuk memberi nama pada elemen-elemen program yang berbeda.

#### **Aturan Pembentukan Identifiers:**

**1. Aturan Dasar (Universal untuk Semua Bahasa):**
- **Harus dimulai dengan huruf atau underscore (_)**
- **Tidak boleh dimulai dengan angka**
- **Hanya boleh mengandung huruf, angka, dan underscore**
- **Case-sensitive** (huruf besar dan kecil dibedakan)
- **Tidak boleh menggunakan reserved words/keywords**

**Contoh Valid Identifiers:**
```
✅ Valid:
nama_mahasiswa
totalNilai
_counter
student1
PI_VALUE
calculateAverage
temp_var
isValid

❌ Invalid:
2ndNumber       // Dimulai dengan angka
total-nilai     // Mengandung tanda hubung
class           // Reserved word
my variable     // Mengandung spasi
@username       // Mengandung karakter khusus
```

**2. Aturan Spesifik Berdasarkan Bahasa:**

**C/C++:**
- Maximum length: biasanya 31-63 karakter (tergantung compiler)
- Underscore di awal umumnya reserved untuk sistem
- Contoh: `int studentAge;`, `float PI = 3.14159;`

**Java:**
- Unlimited length
- Dapat menggunakan Unicode characters
- Contoh: `String studentName;`, `boolean isValid;`

**Python:**
- Unlimited length
- Dapat menggunakan Unicode letters
- Convension: snake_case untuk variabel dan fungsi
- Contoh: `student_name`, `calculate_total`

#### **Best Practices untuk Naming:**

**1. Descriptive Names:**
```c
// Bad
int a, b, c;
float x;

// Good
int studentAge, numberOfStudents, maxScore;
float averageGrade;
```

**2. Consistent Naming Conventions:**
```c
// camelCase (Java, JavaScript)
int studentAge;
float averageGrade;
boolean isValidInput;

// snake_case (Python, C)
int student_age;
float average_grade;
bool is_valid_input;

// PascalCase (untuk classes/types)
struct StudentRecord;
class DatabaseManager;
```

**3. Meaningful Abbreviations:**
```c
// Acceptable abbreviations
int numStudents;    // num = number
float avgGrade;     // avg = average
bool isTemp;        // temp = temporary

// Avoid obscure abbreviations
int stdCnt;         // Unclear
float ag;           // Too short
```

### **1.2 Reserved Words dan Keywords**

Keywords adalah kata-kata yang memiliki makna khusus dalam bahasa pemrograman dan tidak dapat digunakan sebagai identifiers.

#### **Keywords dalam Bahasa C (32 keywords):**
```c
auto        break       case        char        const       continue
default     do          double      else        enum        extern
float       for         goto        if          int         long
register    return      short       signed      sizeof      static
struct      switch      typedef     union       unsigned    void
volatile    while
```

#### **Keywords dalam Bahasa C++ (tambahan dari C):**
```cpp
// C++ specific keywords
class       private     public      protected   virtual     friend
new         delete      this        operator    template    namespace
try         catch       throw       inline      explicit    mutable
typename    using       bool        true        false       dynamic_cast
static_cast const_cast  reinterpret_cast
```

#### **Keywords dalam Java:**
```java
// Access modifiers
public      private     protected   

// Class-related
class       interface   extends     implements  abstract    final
static      

// Control flow
if          else        switch      case        default     for
while       do          break       continue    return

// Exception handling
try         catch       finally     throw       throws

// Primitive types
boolean     byte        short       int         long        float
double      char        void

// Other
new         this        super       null        true        false
import      package     synchronized volatile    transient   native
strictfp    assert
```

#### **Contextual Keywords:**
Beberapa bahasa memiliki contextual keywords yang hanya reserved dalam konteks tertentu:

```java
// Java contextual keywords
var         // Hanya dalam local variable type inference
yield       // Dalam switch expressions
record      // Untuk record classes
sealed      // Untuk sealed classes
```

---

## **BAGIAN 2: TIPE DATA DASAR**

### **2.1 Konsep Fundamental Tipe Data**

Tipe data adalah jenis data yang dapat disimpan dalam variabel. Tipe data menentukan jenis data yang dimiliki variabel, seperti apakah itu teks atau angka. Tipe data yang kita set untuk variabel mempengaruhi apa yang bisa kita lakukan dengan variabel tersebut.

#### **Mengapa Tipe Data Penting:**

**1. Memory Management:**
- Setiap tipe data membutuhkan jumlah memori yang berbeda
- Compiler/interpreter dapat mengalokasikan memori yang tepat
- Optimasi penggunaan resource sistem

**2. Operation Validation:**
- Menentukan operasi apa yang valid untuk data tersebut
- Mencegah operasi yang tidak masuk akal (misal: "Hello" * 5)
- Type safety dalam programming

**3. Performance Optimization:**
- CPU dapat mengoptimalkan operasi berdasarkan tipe data
- Hardware-specific optimizations
- Cache efficiency

#### **Kategori Tipe Data:**

**1. Primitive Types (Tipe Primitif):**
- Built-in dalam bahasa pemrograman
- Directly supported oleh hardware
- Fixed size dan simple structure

**2. Composite Types (Tipe Komposit):**
- Dibuat dari kombinasi primitive types
- Arrays, structures, classes
- User-defined types

**3. Reference Types:**
- Menyimpan reference/alamat ke data
- Pointers, references, objects
- Dynamic memory allocation

### **2.2 Integer Data Types**

Integer types menyimpan bilangan bulat, positif atau negatif, tanpa desimal.

#### **Variasi Integer Types:**

**1. Berdasarkan Size (dalam bahasa C/C++):**
```c
char        // 1 byte  (-128 to 127)
short       // 2 bytes (-32,768 to 32,767)
int         // 4 bytes (-2,147,483,648 to 2,147,483,647)
long        // 8 bytes (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807)
long long   // 8 bytes (same as long in most systems)
```

**2. Signed vs Unsigned:**
```c
// Signed (default) - dapat menyimpan nilai negatif
signed int number = -100;

// Unsigned - hanya nilai positif, range dua kali lipat
unsigned int positiveNumber = 4000000000U;

// Range comparison
signed int:   -2,147,483,648 to 2,147,483,647
unsigned int:              0 to 4,294,967,295
```

**3. Platform Dependencies:**
```c
#include <limits.h>
#include <stdio.h>

int main() {
    printf("int range: %d to %d\n", INT_MIN, INT_MAX);
    printf("char range: %d to %d\n", CHAR_MIN, CHAR_MAX);
    printf("short range: %d to %d\n", SHRT_MIN, SHRT_MAX);
    printf("long range: %ld to %ld\n", LONG_MIN, LONG_MAX);
    
    printf("Size of int: %zu bytes\n", sizeof(int));
    printf("Size of long: %zu bytes\n", sizeof(long));
    return 0;
}
```

#### **Integer Literals dan Representations:**

**1. Decimal (Base 10):**
```c
int decimal = 42;
int negative = -156;
```

**2. Hexadecimal (Base 16):**
```c
int hex = 0x2A;        // 42 in decimal
int hexUpper = 0X2A;   // Same value
```

**3. Octal (Base 8):**
```c
int octal = 052;       // 42 in decimal
```

**4. Binary (C++14 dan newer):**
```cpp
int binary = 0b101010; // 42 in decimal
```

#### **Overflow dan Underflow:**
```c
#include <stdio.h>
#include <limits.h>

int main() {
    int max_int = INT_MAX;
    printf("Maximum int: %d\n", max_int);
    
    // Overflow demonstration
    max_int = max_int + 1;
    printf("After overflow: %d\n", max_int);  // Wraps to INT_MIN
    
    unsigned int max_uint = UINT_MAX;
    printf("Maximum unsigned int: %u\n", max_uint);
    
    // Unsigned overflow wraps to 0
    max_uint = max_uint + 1;
    printf("After unsigned overflow: %u\n", max_uint);  // Becomes 0
    
    return 0;
}
```

### **2.3 Floating-Point Data Types**

Float adalah bilangan desimal, seperti 3.14, -0.001, 2.71828, dll. Floating-point types merepresentasikan bilangan dengan bagian pecahan.

#### **IEEE 754 Standard:**

**1. Single Precision (float):**
```c
float pi = 3.14159f;    // 32-bit, ~7 decimal digits precision
float scientific = 1.23e-4f;  // Scientific notation
```

**Format Internal:**
- 1 bit sign
- 8 bits exponent  
- 23 bits mantissa
- Range: ±1.175494e-38 to ±3.402823e+38

**2. Double Precision (double):**
```c
double precisePI = 3.141592653589793;  // 64-bit, ~15 decimal digits
double largeNumber = 1.234567890123456e10;
```

**Format Internal:**
- 1 bit sign
- 11 bits exponent
- 52 bits mantissa  
- Range: ±2.225074e-308 to ±1.797693e+308

**3. Extended Precision (long double):**
```c
long double extraPrecise = 3.141592653589793238462643383279502884L;
// Size varies by platform (80-bit, 96-bit, or 128-bit)
```

#### **Floating-Point Precision Issues:**

**1. Representation Limitations:**
```c
#include <stdio.h>

int main() {
    float f1 = 0.1f;
    float f2 = 0.2f;
    float sum = f1 + f2;
    
    printf("0.1 + 0.2 = %.10f\n", sum);
    // Output: 0.3000000119 (not exactly 0.3!)
    
    // Safe floating-point comparison
    float tolerance = 1e-6f;
    if (sum - 0.3f < tolerance && 0.3f - sum < tolerance) {
        printf("Sum is approximately 0.3\n");
    }
    
    return 0;
}
```

**2. Special Values:**
```c
#include <stdio.h>
#include <math.h>

int main() {
    float positive_inf = 1.0f / 0.0f;    // +∞
    float negative_inf = -1.0f / 0.0f;   // -∞
    float not_a_number = 0.0f / 0.0f;    // NaN
    
    printf("Positive infinity: %f\n", positive_inf);
    printf("Negative infinity: %f\n", negative_inf);
    printf("Not a number: %f\n", not_a_number);
    
    // Checking for special values
    if (isinf(positive_inf)) printf("positive_inf is infinite\n");
    if (isnan(not_a_number)) printf("not_a_number is NaN\n");
    
    return 0;
}
```

### **2.4 Character Data Type**

Character type menyimpan single character atau small integer values.

#### **Character Representation:**

**1. ASCII Characters:**
```c
char letter = 'A';          // ASCII value 65
char digit = '5';           // ASCII value 53
char newline = '\n';        // ASCII value 10
char tab = '\t';            // ASCII value 9

printf("Character: %c, ASCII: %d\n", letter, letter);
// Output: Character: A, ASCII: 65
```

**2. Escape Sequences:**
```c
char backslash = '\\';      // Backslash
char quote = '\'';          // Single quote
char null_char = '\0';      // Null terminator
char bell = '\a';           // Alert (bell)
char backspace = '\b';      // Backspace
char form_feed = '\f';      // Form feed
char carriage_return = '\r'; // Carriage return
char vertical_tab = '\v';   // Vertical tab
```

**3. Numeric Values:**
```c
char numeric_char = 65;     // Same as 'A'
char arithmetic = 'A' + 1;  // Results in 'B'

// Character arithmetic
for (char c = 'A'; c <= 'Z'; c++) {
    printf("%c ", c);       // Prints A B C ... Z
}
```

#### **Extended Character Sets:**

**1. Wide Characters (wchar_t):**
```c
#include <wchar.h>
#include <locale.h>

wchar_t wide_char = L'€';   // Euro symbol
wchar_t chinese = L'中';    // Chinese character

setlocale(LC_ALL, "");
wprintf(L"Wide character: %lc\n", wide_char);
```

**2. Unicode Support:**
```c
// UTF-8 in C (as char arrays)
char utf8_string[] = "Hello 世界";  // Mixed ASCII and UTF-8

// UTF-16 (platform dependent)
char16_t utf16_char = u'€';

// UTF-32
char32_t utf32_char = U'🙂';
```

### **2.5 Boolean Data Type**

Boolean adalah tipe data yang hanya dapat memiliki dua nilai: True atau False.

#### **Boolean dalam Berbagai Bahasa:**

**1. C (sebelum C99):**
```c
// No built-in boolean, menggunakan int
#define TRUE 1
#define FALSE 0

int isValid = TRUE;
int isEmpty = FALSE;

// Conditional evaluation
if (isValid) {          // Non-zero = true
    printf("Valid\n");
}
```

**2. C99 dan C++ (dengan stdbool.h):**
```c
#include <stdbool.h>

bool isLoggedIn = true;
bool hasPermission = false;

bool result = isLoggedIn && hasPermission;
```

**3. C++ Native Boolean:**
```cpp
bool isReady = true;
bool isComplete = false;

// Boolean expressions
bool isInRange = (value >= 0 && value <= 100);
bool isEven = (number % 2 == 0);
```

#### **Boolean Operations dan Truth Tables:**

**1. Logical AND (&&):**
```
A     | B     | A && B
------|-------|-------
true  | true  | true
true  | false | false
false | true  | false
false | false | false
```

**2. Logical OR (||):**
```
A     | B     | A || B
------|-------|-------
true  | true  | true
true  | false | true
false | true  | true
false | false | false
```

**3. Logical NOT (!):**
```
A     | !A
------|------
true  | false
false | true
```

#### **Practical Boolean Examples:**
```c
#include <stdbool.h>
#include <stdio.h>

bool isLeapYear(int year) {
    return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
}

bool isValidGrade(float grade) {
    return grade >= 0.0 && grade <= 100.0;
}

bool isVowel(char c) {
    return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' ||
           c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U';
}

int main() {
    printf("2024 is leap year: %s\n", isLeapYear(2024) ? "true" : "false");
    printf("Grade 85.5 is valid: %s\n", isValidGrade(85.5) ? "true" : "false");
    printf("'e' is vowel: %s\n", isVowel('e') ? "true" : "false");
    return 0;
}
```

---

## **BAGIAN 3: VARIABEL DAN KONSTANTA**

### **3.1 Konsep Variabel**

Variabel adalah kontainer untuk menyimpan nilai data. Variabel memungkinkan program untuk menyimpan dan memanipulasi data selama eksekusi.

#### **Karakteristik Variabel:**

**1. Name (Identifier):**
- Unique name dalam scope yang sama
- Follows identifier naming rules
- Descriptive dan meaningful

**2. Type:**
- Menentukan jenis data yang dapat disimpan
- Affects memory allocation
- Determines valid operations

**3. Value:**
- Current data stored dalam variabel
- Can change during program execution
- Must be compatible dengan declared type

**4. Address:**
- Memory location dimana data disimpan
- Managed by compiler/runtime
- Can be accessed via pointers

#### **Variable Declaration vs Definition:**

**Declaration:** Memberitahu compiler tentang existence dan type dari variabel
```c
extern int globalCounter;    // Declaration only
```

**Definition:** Mengalokasikan memori untuk variabel
```c
int localVariable;           // Declaration + Definition
int initializedVar = 42;     // Declaration + Definition + Initialization
```

### **3.2 Variable Declaration dan Initialization**

#### **Basic Declaration Syntax:**

**1. Single Variable:**
```c
int age;                    // Uninitialized
float salary = 50000.0f;    // Initialized
char grade = 'A';           // Character with initial value
bool isActive = true;       // Boolean initialization
```

**2. Multiple Variables:**
```c
// Same type, multiple variables
int x, y, z;                        // All uninitialized
int a = 1, b = 2, c = 3;           // All initialized
float length, width, height = 10.0f; // Only height initialized

// Mixed initialization
int count = 0, sum, average = 0;
```

**3. Array Declarations:**
```c
int numbers[5];                     // Uninitialized array
int values[5] = {1, 2, 3, 4, 5};   // Fully initialized
int partial[5] = {1, 2};           // Partially initialized (rest = 0)
int auto_size[] = {1, 2, 3, 4, 5}; // Size determined by initializer
```

#### **Initialization Patterns:**

**1. Zero Initialization:**
```c
int zero_int = 0;
float zero_float = 0.0f;
char zero_char = '\0';
bool zero_bool = false;

// Array zero initialization
int zero_array[10] = {0};    // All elements = 0
int all_zero[10] = {};       // C++ style, all elements = 0
```

**2. Default Initialization (C++):**
```cpp
int default_int{};           // Zero initialized
float default_float{};       // Zero initialized  
string default_string{};     // Empty string

// Uniform initialization syntax
int value{42};
float pi{3.14159f};
char letter{'A'};
```

**3. Copy Initialization:**
```c
int original = 42;
int copy = original;         // Copy value from original

float source = 3.14f;
float target = source;       // Copy float value
```

### **3.3 Variable Scope dan Lifetime**

#### **Types of Scope:**

**1. Global Scope:**
```c
#include <stdio.h>

int globalCounter = 0;       // Global variable
const float PI = 3.14159f;   // Global constant

void incrementCounter() {
    globalCounter++;         // Accessible everywhere
}

int main() {
    printf("Global counter: %d\n", globalCounter);
    incrementCounter();
    printf("After increment: %d\n", globalCounter);
    return 0;
}
```

**2. Function Scope:**
```c
void calculateArea() {
    float length = 10.0f;    // Function scope
    float width = 5.0f;      // Only accessible within this function
    float area = length * width;
    
    printf("Area: %.2f\n", area);
}   // length, width, area destroyed here

int main() {
    calculateArea();
    // length, width, area not accessible here
    return 0;
}
```

**3. Block Scope:**
```c
int main() {
    int outer = 10;
    
    if (outer > 5) {
        int inner = 20;      // Block scope
        printf("Inner: %d\n", inner);
        
        {
            int nested = 30;  // Nested block scope
            printf("Nested: %d\n", nested);
        }   // nested destroyed here
        
        // printf("%d", nested);  // Error! nested not accessible
    }   // inner destroyed here
    
    // printf("%d", inner);      // Error! inner not accessible
    printf("Outer: %d\n", outer); // Still accessible
    return 0;
}
```

**4. File Scope (Static):**
```c
// file1.c
static int fileCounter = 0;  // Only accessible within this file

void incrementFileCounter() {
    fileCounter++;
}

int getFileCounter() {
    return fileCounter;
}
```

#### **Variable Lifetime:**

**1. Automatic Variables:**
```c
void function() {
    int automatic = 42;      // Created when function is called
    // ... use automatic
}   // Destroyed when function returns
```

**2. Static Variables:**
```c
void countCalls() {
    static int callCount = 0; // Initialized only once
    callCount++;              // Retains value between calls
    printf("Function called %d times\n", callCount);
}

int main() {
    countCalls();  // Output: Function called 1 times
    countCalls();  // Output: Function called 2 times
    countCalls();  // Output: Function called 3 times
    return 0;
}
```

**3. Dynamic Variables:**
```c
#include <stdlib.h>

int main() {
    int* dynamic = malloc(sizeof(int)); // Created on heap
    *dynamic = 42;
    
    // ... use dynamic variable
    
    free(dynamic);           // Must be explicitly freed
    dynamic = NULL;          // Good practice
    return 0;
}
```

### **3.4 Constants**

Jika Anda tidak ingin orang lain (atau diri Anda sendiri) menimpa nilai yang ada, gunakan kata kunci final (ini akan mendeklarasikan variabel sebagai "final" atau "constant", yang berarti tidak dapat diubah dan hanya dapat dibaca).

#### **Types of Constants:**

**1. Literal Constants:**
```c
int number = 42;             // Integer literal
float pi = 3.14159f;         // Float literal
char grade = 'A';            // Character literal
char* message = "Hello";     // String literal
bool flag = true;            // Boolean literal
```

**2. Named Constants (#define):**
```c
#define MAX_SIZE 100
#define PI 3.14159
#define COMPANY_NAME "TechCorp"

int array[MAX_SIZE];         // Uses defined constant
float area = PI * radius * radius;
```

**3. const Keyword:**
```c
const int MAX_STUDENTS = 50;
const float TAX_RATE = 0.08f;
const char GRADE_A = 'A';

// MAX_STUDENTS = 60;        // Error! Cannot modify const
```

**4. const with Pointers:**
```c
int value = 42;
int another = 100;

const int* ptr1 = &value;    // Pointer to const int
// *ptr1 = 50;               // Error! Cannot modify value through ptr1
ptr1 = &another;             // OK! Can point to different address

int* const ptr2 = &value;    // Const pointer to int
*ptr2 = 50;                  // OK! Can modify value
// ptr2 = &another;          // Error! Cannot change pointer address

const int* const ptr3 = &value; // Const pointer to const int
// *ptr3 = 50;               // Error! Cannot modify value
// ptr3 = &another;          // Error! Cannot change pointer
```

#### **Advantages of Using Constants:**

**1. Code Readability:**
```c
// Bad
if (age >= 18) {
    printf("Adult\n");
}

// Good  
const int LEGAL_AGE = 18;
if (age >= LEGAL_AGE) {
    printf("Adult\n");
}
```

**2. Maintainability:**
```c
const float SALES_TAX = 0.08f;
const float DISCOUNT_RATE = 0.15f;
const int MAX_ITEMS = 100;

float calculateTotal(float subtotal) {
    float tax = subtotal * SALES_TAX;
    float discount = subtotal * DISCOUNT_RATE;
    return subtotal + tax - discount;
}
```

**3. Prevention of Magic Numbers:**
```c
// Magic numbers (bad)
for (int i = 0; i < 12; i++) {
    monthlyRevenue[i] = 0;
}

// Named constants (good)
const int MONTHS_IN_YEAR = 12;
for (int i = 0; i < MONTHS_IN_YEAR; i++) {
    monthlyRevenue[i] = 0;
}
```

---

## **BAGIAN 4: OPERATOR**

### **4.1 Arithmetic Operators**

Arithmetic operators digunakan untuk melakukan operasi matematika umum.

#### **Basic Arithmetic Operators:**

**1. Addition (+):**
```c
int a = 10, b = 5;
int sum = a + b;             // Result: 15

float x = 3.5f, y = 2.1f;
float float_sum = x + y;     // Result: 5.6

// String concatenation (dalam beberapa bahasa)
// "Hello" + " World" = "Hello World"
```

**2. Subtraction (-):**
```c
int difference = a - b;      // Result: 5
float float_diff = x - y;    // Result: 1.4

// Unary minus
int negative = -a;           // Result: -10
```

**3. Multiplication (*):**
```c
int product = a * b;         // Result: 50
float area = length * width; // Calculate area

// Pointer multiplication (address arithmetic)
int* ptr = &a;
// int invalid = ptr * 2;    // Error! Invalid operation
```

**4. Division (/):**
```c
// Integer division
int int_division = a / b;    // Result: 2 (integer result)

// Floating-point division
float float_division = (float)a / b; // Result: 2.0
float precise_div = 10.0f / 3.0f;    // Result: 3.333333

// Division by zero
// int error = a / 0;        // Runtime error (crash)
// float inf = 10.0f / 0.0f; // May result in infinity
```

**5. Modulus (%):**
```c
int remainder = a % b;       // Result: 0 (10 % 5 = 0)
int odd_check = 7 % 2;       // Result: 1 (used for odd/even check)

// Modulus with negative numbers
int neg_mod1 = -10 % 3;      // Result: -1 (implementation-defined)
int neg_mod2 = 10 % -3;      // Result: 1 (implementation-defined)

// Common uses
bool isEven = (number % 2 == 0);
int lastDigit = number % 10;
int dayOfWeek = (dayNumber % 7);
```

#### **Advanced Arithmetic Operations:**

**1. Compound Assignment Operators:**
```c
int value = 10;

value += 5;    // value = value + 5;  Result: 15
value -= 3;    // value = value - 3;  Result: 12
value *= 2;    // value = value * 2;  Result: 24
value /= 4;    // value = value / 4;  Result: 6
value %= 5;    // value = value % 5;  Result: 1
```

**2. Increment dan Decrement Operators:**
```c
int counter = 5;

// Pre-increment: increment first, then use value
int pre_inc = ++counter;     // counter = 6, pre_inc = 6

// Post-increment: use value first, then increment
int post_inc = counter++;    // post_inc = 6, counter = 7

// Pre-decrement: decrement first, then use value
int pre_dec = --counter;     // counter = 6, pre_dec = 6

// Post-decrement: use value first, then decrement
int post_dec = counter--;    // post_dec = 6, counter = 5

// Practical example
for (int i = 0; i < 10; i++) {        // Post-increment in loop
    printf("%d ", i);
}

int arr[5] = {1, 2, 3, 4, 5};
int* ptr = arr;
printf("%d\n", *ptr++);               // Print 1, then move pointer
printf("%d\n", *++ptr);               // Move pointer, then print 3
```

#### **Mathematical Functions (math.h):**
```c
#include <math.h>
#include <stdio.h>

int main() {
    double x = 16.0, y = 2.5;
    
    printf("Square root of %.1f: %.2f\n", x, sqrt(x));        // 4.00
    printf("%.1f raised to %.1f: %.2f\n", x, y, pow(x, y));   // 1024.00
    printf("Absolute value of -5: %d\n", abs(-5));            // 5
    printf("Ceiling of 3.2: %.0f\n", ceil(3.2));             // 4
    printf("Floor of 3.8: %.0f\n", floor(3.8));              // 3
    printf("Natural log of %.1f: %.2f\n", x, log(x));         // 2.77
    printf("Log base 10 of %.1f: %.2f\n", x, log10(x));       // 1.20
    
    return 0;
}
```

### **4.2 Relational (Comparison) Operators**

Comparison operators digunakan untuk membandingkan dua nilai. Return value dari comparison adalah true atau false (Boolean values).

#### **Basic Comparison Operators:**

**1. Equality (==) dan Inequality (!=):**
```c
int x = 5, y = 3, z = 5;

bool equal = (x == z);       // true (5 == 5)
bool not_equal = (x != y);   // true (5 != 3)

// String comparison (perlu fungsi khusus)
char str1[] = "hello";
char str2[] = "hello";
// bool wrong = (str1 == str2);          // Wrong! Compares addresses
bool correct = (strcmp(str1, str2) == 0); // Correct string comparison

// Floating-point comparison (hati-hati dengan precision)
float f1 = 0.1f + 0.2f;
float f2 = 0.3f;
bool unsafe = (f1 == f2);    // May be false due to precision!

// Safe floating-point comparison
float tolerance = 1e-6f;
bool safe = (fabs(f1 - f2) < tolerance);
```

**2. Greater Than (>) dan Less Than (<):**
```c
int a = 10, b = 5;

bool greater = (a > b);      // true (10 > 5)
bool less = (b < a);         // true (5 < 10)

// Character comparison (ASCII values)
char ch1 = 'A', ch2 = 'B';
bool char_less = (ch1 < ch2); // true ('A' = 65, 'B' = 66)

// Lexicographical string comparison
bool str_compare = (strcmp("apple", "banana") < 0); // true (alphabetical order)
```

**3. Greater Than or Equal (>=) dan Less Than or Equal (<=):**
```c
int score = 85;
const int PASSING_GRADE = 70;
const int HONOR_GRADE = 90;

bool passed = (score >= PASSING_GRADE);     // true
bool honor = (score >= HONOR_GRADE);        // false
bool valid_grade = (score >= 0 && score <= 100);

// Range checking
int age = 25;
bool adult = (age >= 18);
bool senior = (age >= 65);
bool working_age = (age >= 18 && age <= 65);
```

#### **Advanced Comparison Techniques:**

**1. Chained Comparisons (careful!):**
```c
// Mathematical notation: 0 < x < 10
// Wrong way in C:
// bool wrong = (0 < x < 10);    // Always true! Why?
// Because: (0 < x) evaluates to 0 or 1, then (0 or 1) < 10 is always true

// Correct way:
bool correct = (x > 0 && x < 10);
```

**2. Complex Conditions:**
```c
int year = 2024;
bool isLeapYear = ((year % 4 == 0) && (year % 100 != 0)) || (year % 400 == 0);

float temperature = 25.5f;
bool comfortable = (temperature >= 18.0f && temperature <= 26.0f);

char grade = 'B';
bool passing = (grade == 'A' || grade == 'B' || grade == 'C');
```

### **4.3 Logical Operators**

Logical operators digunakan untuk menentukan logika antara variabel atau nilai, dan untuk menggabungkan kondisi.

#### **Basic Logical Operators:**

**1. Logical AND (&&):**
```c
bool condition1 = true;
bool condition2 = false;
bool result = condition1 && condition2;  // false

// Practical examples
int age = 25;
bool hasLicense = true;
bool canDrive = (age >= 18) && hasLicense;

// Short-circuit evaluation
bool safe_division = (divisor != 0) && (dividend / divisor > 0);
// If divisor is 0, second condition is NOT evaluated (prevents crash)
```

**2. Logical OR (||):**
```c
bool weekend = (day == "Saturday") || (day == "Sunday");
bool emergency = (fire_alarm == true) || (medical_emergency == true);

// Multiple conditions
char grade = 'B';
bool honor_roll = (grade == 'A') || (grade == 'A+') || (grade == 'A-');

// Short-circuit evaluation
bool valid_access = has_permission || is_admin || is_emergency;
// If has_permission is true, other conditions are NOT checked
```

**3. Logical NOT (!):**
```c
bool is_logged_in = true;
bool is_guest = !is_logged_in;          // false

// Double negation
bool is_not_empty = !empty;
bool has_data = !!data_pointer;         // Convert pointer to boolean

// Practical examples
bool is_valid_password = !is_password_weak;
bool access_denied = !has_permission;
```

#### **Truth Tables dan Logical Laws:**

**1. De Morgan's Laws:**
```c
// !(A && B) == (!A || !B)
bool a = true, b = false;
bool law1_left = !(a && b);              // true
bool law1_right = (!a) || (!b);          // true (equivalent)

// !(A || B) == (!A && !B)
bool law2_left = !(a || b);              // false
bool law2_right = (!a) && (!b);          // false (equivalent)
```

**2. Logical Equivalences:**
```c
// Double negation: !!A == A
bool original = true;
bool double_neg = !!original;            // true

// Absorption: A && (A || B) == A
bool absorption1 = a && (a || b);        // Same as a

// Distribution: A && (B || C) == (A && B) || (A && C)
bool c = true;
bool distrib_left = a && (b || c);
bool distrib_right = (a && b) || (a && c);
```

#### **Complex Logical Expressions:**
```c
// User authentication system
bool authenticate_user(char* username, char* password, bool two_factor_enabled, bool two_factor_passed) {
    bool basic_auth = (strlen(username) > 0) && (strlen(password) >= 8);
    bool two_factor_ok = !two_factor_enabled || two_factor_passed;
    
    return basic_auth && two_factor_ok;
}

// Access control system
bool has_access(int user_level, bool is_weekend, int current_hour, bool emergency) {
    bool business_hours = (current_hour >= 9) && (current_hour <= 17);
    bool weekend_access = is_weekend && (user_level >= 3);
    bool weekday_access = !is_weekend && business_hours && (user_level >= 1);
    
    return emergency || weekend_access || weekday_access;
}
```

### **4.4 Bitwise Operators**

Bitwise operators bekerja pada representasi biner dari angka, memanipulasi bit individual.

#### **Basic Bitwise Operations:**

**1. Bitwise AND (&):**
```c
int a = 12;    // Binary: 1100
int b = 10;    // Binary: 1010
int result = a & b;  // Binary: 1000, Decimal: 8

// Truth table for each bit position:
// 1 & 1 = 1
// 1 & 0 = 0  
// 0 & 1 = 0
// 0 & 0 = 0

// Practical use: Check if number is even
bool is_even = (number & 1) == 0;  // Check last bit

// Extract specific bits
int extract_lower_4_bits = value & 0x0F;  // Mask: 00001111
```

**2. Bitwise OR (|):**
```c
int a = 12;    // Binary: 1100
int b = 10;    // Binary: 1010
int result = a | b;  // Binary: 1110, Decimal: 14

// Set specific bits
int flags = 0;
flags |= 0x01;  // Set bit 0
flags |= 0x04;  // Set bit 2
// flags now has bits 0 and 2 set: 00000101
```

**3. Bitwise XOR (^):**
```c
int a = 12;    // Binary: 1100
int b = 10;    // Binary: 1010
int result = a ^ b;  // Binary: 0110, Decimal: 6

// XOR properties:
// A ^ A = 0
// A ^ 0 = A
// A ^ B ^ B = A (useful for encryption)

// Toggle specific bits
int toggle_bit_2 = value ^ 0x04;  // Toggle bit 2

// Swap variables without temporary variable
int x = 5, y = 7;
x = x ^ y;  // x = 5 ^ 7 = 2
y = x ^ y;  // y = 2 ^ 7 = 5
x = x ^ y;  // x = 2 ^ 5 = 7
// Now x = 7, y = 5
```

**4. Bitwise NOT (~):**
```c
int a = 12;    // Binary: 00001100 (assuming 8-bit)
int result = ~a;  // Binary: 11110011, Decimal: -13 (two's complement)

// Clear specific bits
int clear_bit_2 = value & (~0x04);  // Clear bit 2
```

**5. Left Shift (<<) dan Right Shift (>>):**
```c
int value = 5;     // Binary: 0101

// Left shift (multiply by 2^n)
int left1 = value << 1;   // 1010 = 10 (5 * 2^1)
int left2 = value << 2;   // 10100 = 20 (5 * 2^2)

// Right shift (divide by 2^n)
int right1 = value >> 1;  // 010 = 2 (5 / 2^1)
int right2 = value >> 2;  // 01 = 1 (5 / 2^2)

// Practical applications
int multiply_by_8 = value << 3;      // Faster than value * 8
int divide_by_4 = value >> 2;        // Faster than value / 4

// Extract specific bit
bool is_bit_3_set = (value >> 3) & 1;
```

#### **Advanced Bitwise Applications:**

**1. Bit Manipulation Techniques:**
```c
// Set bit n
int set_bit(int value, int n) {
    return value | (1 << n);
}

// Clear bit n
int clear_bit(int value, int n) {
    return value & (~(1 << n));
}

// Toggle bit n
int toggle_bit(int value, int n) {
    return value ^ (1 << n);
}

// Check if bit n is set
bool is_bit_set(int value, int n) {
    return (value & (1 << n)) != 0;
}

// Count number of set bits
int count_set_bits(int value) {
    int count = 0;
    while (value) {
        count += value & 1;
        value >>= 1;
    }
    return count;
}
```

**2. Practical Examples:**
```c
// Permission system using bit flags
#define READ_PERMISSION    0x01  // 00000001
#define WRITE_PERMISSION   0x02  // 00000010
#define EXECUTE_PERMISSION 0x04  // 00000100
#define ADMIN_PERMISSION   0x08  // 00001000

int user_permissions = READ_PERMISSION | WRITE_PERMISSION;

// Check permissions
bool can_read = (user_permissions & READ_PERMISSION) != 0;
bool can_write = (user_permissions & WRITE_PERMISSION) != 0;
bool can_execute = (user_permissions & EXECUTE_PERMISSION) != 0;

// Grant permission
user_permissions |= EXECUTE_PERMISSION;

// Revoke permission
user_permissions &= ~WRITE_PERMISSION;
```

---

## **BAGIAN 5: EKSPRESI DAN OPERATOR PRECEDENCE**

### **5.1 Konsep Ekspresi**

Ekspresi adalah kombinasi dari operator dan operand yang menghasilkan nilai. Ekspresi dapat sederhana (single value) atau kompleks (multiple operators dan operands).

#### **Jenis-Jenis Ekspresi:**

**1. Arithmetic Expressions:**
```c
int a = 5, b = 3, c = 2;

// Simple expressions
int sum = a + b;                    // 8
int product = a * b;                // 15

// Complex expressions
int complex = a + b * c - a / b;    // 5 + 6 - 1 = 10
float precise = (float)(a + b) / c; // 4.0 (type casting)
```

**2. Boolean Expressions:**
```c
bool simple = (a > b);                           // true
bool complex = (a > b) && (b > c) || (a == 5);  // true
bool nested = ((a + b) > c) && !(a < b);        // true
```

**3. Assignment Expressions:**
```c
int x;
x = a + b;           // Assignment expression, returns assigned value
int y = (x = a * b); // y gets the value assigned to x (15)

// Chained assignment
int p, q, r;
p = q = r = 10;      // All get value 10 (right-to-left associativity)
```

**4. Mixed Expressions:**
```c
int result = (a > b) ? a * 2 : b + c;  // Ternary operator
bool valid = (a != 0) && ((b / a) > 1); // Short-circuit evaluation
```

### **5.2 Operator Precedence**

Operator precedence menentukan urutan operasi yang dilakukan dalam ekspresi. Seperti dalam matematika, perkalian dilakukan sebelum penjumlahan.

#### **Operator Precedence Table (High to Low):**

```
Priority | Operators                    | Associativity | Description
---------|------------------------------|---------------|------------------
1        | () [] -> .                   | L to R        | Parentheses, array subscript, member access
2        | ! ~ ++ -- + - * & (type)     | R to L        | Unary operators, type casting
3        | * / %                        | L to R        | Multiplicative
4        | + -                          | L to R        | Additive  
5        | << >>                        | L to R        | Shift operators
6        | < <= > >=                    | L to R        | Relational
7        | == !=                        | L to R        | Equality
8        | &                            | L to R        | Bitwise AND
9        | ^                            | L to R        | Bitwise XOR
10       | |                            | L to R        | Bitwise OR
11       | &&                           | L to R        | Logical AND
12       | ||                           | L to R        | Logical OR
13       | ?:                           | R to L        | Ternary conditional
14       | = += -= *= /= %= &= ^= |=    | R to L        | Assignment operators
15       | ,                            | L to R        | Comma operator
```

#### **Precedence Examples:**

**1. Arithmetic Precedence:**
```c
int result1 = 5 + 3 * 2;        // = 5 + 6 = 11 (not 16!)
int result2 = (5 + 3) * 2;      // = 8 * 2 = 16
int result3 = 10 - 6 / 2;       // = 10 - 3 = 7
int result4 = (10 - 6) / 2;     // = 4 / 2 = 2

// Complex expression
int complex = 2 + 3 * 4 - 8 / 2 + 1;
// Step by step:
// 2 + 12 - 4 + 1 = 11
```

**2. Mixed Operator Precedence:**
```c
int a = 5, b = 3, c = 2;

// Logical and arithmetic mix
bool result1 = a + b > c * 2 && a != b;
// Step by step:
// a + b > c * 2 && a != b
// 8 > 4 && 5 != 3
// true && true = true

// Bitwise and arithmetic
int result2 = a << 1 + b;       // = a << (1 + b) = 5 << 4 = 80
int result3 = (a << 1) + b;     // = 10 + 3 = 13
```

**3. Assignment Precedence:**
```c
int x = 5, y = 3;

// Assignment has low precedence
int z = x + y * 2;              // = 5 + 6 = 11
int w = (x + y) * 2;            // = 8 * 2 = 16

// Compound assignment
x += y * 2;                     // x = x + (y * 2) = 5 + 6 = 11
// Not: x = (x + y) * 2
```

### **5.3 Operator Associativity**

Ketika operator memiliki precedence yang sama, associativity menentukan urutan evaluasi.

#### **Left-to-Right Associativity:**
```c
// Arithmetic operators
int result1 = 10 - 5 - 3;       // = (10 - 5) - 3 = 2
int result2 = 20 / 4 / 2;       // = (20 / 4) / 2 = 2.5

// Comparison operators  
bool result3 = 5 < 10 < 2;      // = (5 < 10) < 2 = 1 < 2 = true
// This is confusing! Better: (5 < 10) && (10 < 2) = false
```

#### **Right-to-Left Associativity:**
```c
// Assignment operators
int a, b, c;
a = b = c = 10;                 // = a = (b = (c = 10))

// Compound assignment
a += b += c;                    // = a += (b += c)
// If a=5, b=3, c=2: b = 3+2 = 5, then a = 5+5 = 10

// Unary operators
int x = 5;
int result = ++x + ++x;         // Undefined behavior! Don't do this
```

#### **Ternary Operator Associativity:**
```c
int a = 5, b = 3, c = 7;

// Right-to-left associativity
int result = a > b ? a : b > c ? b : c;
// = a > b ? a : (b > c ? b : c)
// = 5 > 3 ? 5 : (3 > 7 ? 3 : 7)
// = true ? 5 : 7 = 5

// Use parentheses for clarity
int clear = (a > b) ? a : ((b > c) ? b : c);
```

### **5.4 Type Conversion dalam Ekspresi**

#### **Implicit Type Conversion (Type Promotion):**

**1. Integer Promotion:**
```c
char c = 'A';           // ASCII 65
short s = 100;
int i = 1000;

int result1 = c + s;    // char and short promoted to int
int result2 = c + 1;    // char promoted to int, then added
```

**2. Usual Arithmetic Conversions:**
```c
int i = 10;
float f = 3.5f;
double d = 2.1;

float result1 = i + f;  // int promoted to float: 13.5f
double result2 = f + d; // float promoted to double: 5.6
double result3 = i + d; // int promoted to double: 12.1
```

#### **Explicit Type Conversion (Type Casting):**

**1. C-style Casting:**
```c
int i = 10;
int j = 3;

float division1 = i / j;        // Integer division: 3.0
float division2 = (float)i / j; // Cast i to float: 3.333333

// Potential data loss
int truncated = (int)3.14159;   // Result: 3 (fractional part lost)
char overflow = (char)300;      // Result: 44 (only lower 8 bits kept)
```

**2. Function-style Casting (C++):**
```cpp
float f = float(i) / j;         // Same as (float)i / j
int truncated = int(3.14159);   // Same as (int)3.14159
```

#### **Common Type Conversion Pitfalls:**
```c
// Comparing signed and unsigned
int signed_val = -1;
unsigned int unsigned_val = 1;

if (signed_val < unsigned_val) {
    printf("This might not print!\n");
}
// -1 is converted to large unsigned value!

// Floating-point precision loss
float f = 16777217.0f;          // Beyond float precision
printf("%.0f\n", f);            // May print 16777216

// Integer overflow in expressions
int large1 = 2000000000;
int large2 = 2000000000;
long long result = large1 + large2;  // Overflow before assignment!
// Correct: long long result = (long long)large1 + large2;
```

---

## **BAGIAN 6: STUDI KASUS DAN APLIKASI PRAKTIS**

### **6.1 Kalkulator Operasi Aritmatika Lengkap**

Mari implementasikan kalkulator yang mendemonstrasikan semua konsep yang telah dipelajari.

```c
#include <stdio.h>
#include <stdbool.h>
#include <math.h>

// Constants
const char PROGRAM_NAME[] = "Advanced Calculator";
const char VERSION[] = "1.0";
const float EPSILON = 1e-6f;

// Function prototypes
void displayMenu(void);
bool isValidOperation(char op);
double performOperation(double a, double b, char op);
void displayResult(double a, double b, char op, double result);
bool isNearZero(double value);

int main() {
    double num1, num2, result;
    char operation;
    bool continueProgram = true;
    
    printf("=== %s v%s ===\n\n", PROGRAM_NAME, VERSION);
    
    while (continueProgram) {
        displayMenu();
        
        // Input validation for first number
        printf("Enter first number: ");
        while (scanf("%lf", &num1) != 1) {
            printf("Invalid input! Please enter a valid number: ");
            while (getchar() != '\n'); // Clear input buffer
        }
        
        // Input validation for operation
        printf("Enter operation (+, -, *, /, %%, ^): ");
        while (scanf(" %c", &operation) != 1 || !isValidOperation(operation)) {
            printf("Invalid operation! Please enter +, -, *, /, %%, or ^: ");
            while (getchar() != '\n');
        }
        
        // Input validation for second number
        printf("Enter second number: ");
        while (scanf("%lf", &num2) != 1) {
            printf("Invalid input! Please enter a valid number: ");
            while (getchar() != '\n');
        }
        
        // Perform calculation
        result = performOperation(num1, num2, operation);
        
        // Display result
        displayResult(num1, num2, operation, result);
        
        // Continue prompt
        printf("\nContinue? (y/n): ");
        char choice;
        scanf(" %c", &choice);
        continueProgram = (choice == 'y' || choice == 'Y');
        printf("\n");
    }
    
    printf("Thank you for using %s!\n", PROGRAM_NAME);
    return 0;
}

void displayMenu(void) {
    printf("Available operations:\n");
    printf("  + : Addition\n");
    printf("  - : Subtraction\n");
    printf("  * : Multiplication\n");
    printf("  / : Division\n");
    printf("  %% : Modulus (integers only)\n");
    printf("  ^ : Exponentiation\n");
    printf("------------------------\n");
}

bool isValidOperation(char op) {
    return (op == '+' || op == '-' || op == '*' || 
            op == '/' || op == '%' || op == '^');
}

double performOperation(double a, double b, char op) {
    switch (op) {
        case '+':
            return a + b;
            
        case '-':
            return a - b;
            
        case '*':
            return a * b;
            
        case '/':
            if (isNearZero(b)) {
                printf("Error: Division by zero!\n");
                return NAN; // Not a Number
            }
            return a / b;
            
        case '%':
            if (isNearZero(b)) {
                printf("Error: Modulus by zero!\n");
                return NAN;
            }
            // Convert to integers for modulus
            return (double)((long long)a % (long long)b);
            
        case '^':
            return pow(a, b);
            
        default:
            printf("Error: Unknown operation!\n");
            return NAN;
    }
}

void displayResult(double a, double b, char op, double result) {
    printf("\nCalculation: ");
    
    if (op == '%') {
        printf("%.0f %c %.0f = ", a, op, b);
    } else {
        printf("%.6g %c %.6g = ", a, op, b);
    }
    
    if (isnan(result)) {
        printf("Error (undefined)\n");
    } else if (isinf(result)) {
        printf("Infinity\n");
    } else {
        if (op == '%') {
            printf("%.0f\n", result);
        } else {
            printf("%.6g\n", result);
        }
    }
}

bool isNearZero(double value) {
    return fabs(value) < EPSILON;
}
```

### **6.2 Sistem Konversi Suhu Multi-Unit**

```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

// Temperature conversion constants
const double CELSIUS_TO_FAHRENHEIT_MULT = 9.0/5.0;
const double CELSIUS_TO_FAHRENHEIT_ADD = 32.0;
const double KELVIN_OFFSET = 273.15;
const double RANKINE_MULT = 9.0/5.0;

// Temperature scales
typedef enum {
    CELSIUS = 1,
    FAHRENHEIT,
    KELVIN,
    RANKINE
} TemperatureScale;

// Function prototypes
void displayTemperatureMenu(void);
TemperatureScale getTemperatureScale(const char* prompt);
double convertTemperature(double temp, TemperatureScale from, TemperatureScale to);
const char* getScaleName(TemperatureScale scale);
bool isValidTemperature(double temp, TemperatureScale scale);

int main() {
    double inputTemp, convertedTemp;
    TemperatureScale fromScale, toScale;
    bool continueProgram = true;
    
    printf("=== Temperature Conversion System ===\n\n");
    
    while (continueProgram) {
        displayTemperatureMenu();
        
        // Get source scale
        fromScale = getTemperatureScale("Enter source temperature scale");
        
        // Get input temperature
        printf("Enter temperature value: ");
        while (scanf("%lf", &inputTemp) != 1) {
            printf("Invalid input! Please enter a valid number: ");
            while (getchar() != '\n');
        }
        
        // Validate temperature
        if (!isValidTemperature(inputTemp, fromScale)) {
            printf("Warning: Temperature is below absolute zero for %s scale!\n", 
                   getScaleName(fromScale));
        }
        
        // Get target scale
        toScale = getTemperatureScale("Enter target temperature scale");
        
        // Perform conversion
        convertedTemp = convertTemperature(inputTemp, fromScale, toScale);
        
        // Display result
        printf("\nConversion Result:\n");
        printf("%.2f° %s = %.2f° %s\n", 
               inputTemp, getScaleName(fromScale),
               convertedTemp, getScaleName(toScale));
        
        // Show all conversions
        printf("\nAll conversions from %.2f° %s:\n", inputTemp, getScaleName(fromScale));
        for (int scale = CELSIUS; scale <= RANKINE; scale++) {
            if (scale != fromScale) {
                double temp = convertTemperature(inputTemp, fromScale, scale);
                printf("  %s: %.2f°\n", getScaleName(scale), temp);
            }
        }
        
        // Continue prompt
        printf("\nConvert another temperature? (y/n): ");
        char choice;
        scanf(" %c", &choice);
        continueProgram = (choice == 'y' || choice == 'Y');
        printf("\n");
    }
    
    return 0;
}

void displayTemperatureMenu(void) {
    printf("Temperature Scales:\n");
    printf("  1. Celsius (°C)\n");
    printf("  2. Fahrenheit (°F)\n");
    printf("  3. Kelvin (K)\n");
    printf("  4. Rankine (°R)\n");
    printf("------------------------\n");
}

TemperatureScale getTemperatureScale(const char* prompt) {
    int choice;
    printf("%s (1-4): ", prompt);
    
    while (scanf("%d", &choice) != 1 || choice < 1 || choice > 4) {
        printf("Invalid choice! Please enter 1-4: ");
        while (getchar() != '\n');
    }
    
    return (TemperatureScale)choice;
}

double convertTemperature(double temp, TemperatureScale from, TemperatureScale to) {
    double celsius;
    
    // Convert input temperature to Celsius first
    switch (from) {
        case CELSIUS:
            celsius = temp;
            break;
        case FAHRENHEIT:
            celsius = (temp - CELSIUS_TO_FAHRENHEIT_ADD) / CELSIUS_TO_FAHRENHEIT_MULT;
            break;
        case KELVIN:
            celsius = temp - KELVIN_OFFSET;
            break;
        case RANKINE:
            celsius = (temp / RANKINE_MULT) - KELVIN_OFFSET;
            break;
    }
    
    // Convert from Celsius to target scale
    switch (to) {
        case CELSIUS:
            return celsius;
        case FAHRENHEIT:
            return (celsius * CELSIUS_TO_FAHRENHEIT_MULT) + CELSIUS_TO_FAHRENHEIT_ADD;
        case KELVIN:
            return celsius + KELVIN_OFFSET;
        case RANKINE:
            return (celsius + KELVIN_OFFSET) * RANKINE_MULT;
        default:
            return celsius;
    }
}

const char* getScaleName(TemperatureScale scale) {
    switch (scale) {
        case CELSIUS: return "Celsius";
        case FAHRENHEIT: return "Fahrenheit";
        case KELVIN: return "Kelvin";
        case RANKINE: return "Rankine";
        default: return "Unknown";
    }
}

bool isValidTemperature(double temp, TemperatureScale scale) {
    double absoluteZero;
    
    switch (scale) {
        case CELSIUS:
            absoluteZero = -273.15;
            break;
        case FAHRENHEIT:
            absoluteZero = -459.67;
            break;
        case KELVIN:
            absoluteZero = 0.0;
            break;
        case RANKINE:
            absoluteZero = 0.0;
            break;
        default:
            return true;
    }
    
    return temp >= absoluteZero;
}
```

### **6.3 Bitwise Operations Demonstration**

```c
#include <stdio.h>
#include <stdbool.h>

// Function prototypes
void printBinary(unsigned int num, int bits);
void demonstrateBitwiseOperations(void);
void demonstrateSetClearToggle(void);
void demonstrateRealWorldApplications(void);

int main() {
    printf("=== Bitwise Operations Demonstration ===\n\n");
    
    demonstrateBitwiseOperations();
    demonstrateSetClearToggle();
    demonstrateRealWorldApplications();
    
    return 0;
}

void printBinary(unsigned int num, int bits) {
    for (int i = bits - 1; i >= 0; i--) {
        printf("%d", (num >> i) & 1);
        if (i % 4 == 0 && i != 0) printf(" ");
    }
}

void demonstrateBitwiseOperations(void) {
    printf("1. Basic Bitwise Operations\n");
    printf("===========================\n");
    
    unsigned int a = 12;  // 1100
    unsigned int b = 10;  // 1010
    
    printf("a = %2d (", a); printBinary(a, 8); printf(")\n");
    printf("b = %2d (", b); printBinary(b, 8); printf(")\n\n");
    
    // AND operation
    unsigned int and_result = a & b;
    printf("a & b  = %2d (", and_result); printBinary(and_result, 8); printf(")\n");
    
    // OR operation
    unsigned int or_result = a | b;
    printf("a | b  = %2d (", or_result); printBinary(or_result, 8); printf(")\n");
    
    // XOR operation
    unsigned int xor_result = a ^ b;
    printf("a ^ b  = %2d (", xor_result); printBinary(xor_result, 8); printf(")\n");
    
    // NOT operation
    unsigned int not_a = ~a & 0xFF; // Mask to 8 bits
    printf("~a     = %2d (", not_a); printBinary(not_a, 8); printf(")\n");
    
    // Shift operations
    unsigned int left_shift = a << 2;
    unsigned int right_shift = a >> 1;
    printf("a << 2 = %2d (", left_shift); printBinary(left_shift, 8); printf(")\n");
    printf("a >> 1 = %2d (", right_shift); printBinary(right_shift, 8); printf(")\n\n");
}

void demonstrateSetClearToggle(void) {
    printf("2. Set, Clear, and Toggle Operations\n");
    printf("====================================\n");
    
    unsigned int value = 0b10100000;  // Starting value
    
    printf("Initial value: %3d (", value); printBinary(value, 8); printf(")\n");
    
    // Set bit 2
    unsigned int set_bit_2 = value | (1 << 2);
    printf("Set bit 2:     %3d (", set_bit_2); printBinary(set_bit_2, 8); printf(")\n");
    
    // Clear bit 7
    unsigned int clear_bit_7 = set_bit_2 & (~(1 << 7));
    printf("Clear bit 7:   %3d (", clear_bit_7); printBinary(clear_bit_7, 8); printf(")\n");
    
    // Toggle bit 4
    unsigned int toggle_bit_4 = clear_bit_7 ^ (1 << 4);
    printf("Toggle bit 4:  %3d (", toggle_bit_4); printBinary(toggle_bit_4, 8); printf(")\n");
    
    // Check if bit is set
    bool is_bit_5_set = (toggle_bit_4 & (1 << 5)) != 0;
    printf("Is bit 5 set? %s\n\n", is_bit_5_set ? "Yes" : "No");
}

void demonstrateRealWorldApplications(void) {
    printf("3. Real-World Applications\n");
    printf("==========================\n");
    
    // Permission system
    printf("a) Permission System:\n");
    
    #define READ_PERM    0x01  // 00000001
    #define WRITE_PERM   0x02  // 00000010
    #define EXECUTE_PERM 0x04  // 00000100
    #define ADMIN_PERM   0x08  // 00001000
    
    unsigned int user_permissions = READ_PERM | WRITE_PERM;
    printf("User permissions: "); printBinary(user_permissions, 8); printf("\n");
    printf("Can read: %s\n", (user_permissions & READ_PERM) ? "Yes" : "No");
    printf("Can write: %s\n", (user_permissions & WRITE_PERM) ? "Yes" : "No");
    printf("Can execute: %s\n", (user_permissions & EXECUTE_PERM) ? "Yes" : "No");
    
    // Grant execute permission
    user_permissions |= EXECUTE_PERM;
    printf("After granting execute: "); printBinary(user_permissions, 8); printf("\n");
    printf("Can execute: %s\n", (user_permissions & EXECUTE_PERM) ? "Yes" : "No");
    
    printf("\nb) Even/Odd Check:\n");
    for (int i = 1; i <= 10; i++) {
        printf("%d is %s\n", i, (i & 1) ? "odd" : "even");
    }
    
    printf("\nc) Fast Multiplication/Division by Powers of 2:\n");
    int number = 15;
    printf("Original: %d\n", number);
    printf("× 2 (<<1): %d\n", number << 1);
    printf("× 4 (<<2): %d\n", number << 2);
    printf("× 8 (<<3): %d\n", number << 3);
    printf("÷ 2 (>>1): %d\n", number >> 1);
    printf("÷ 4 (>>2): %d\n", number >> 2);
}
```

---

## **BAGIAN 7: LATIHAN DAN EVALUASI**

### **7.1 Latihan Bertingkat**

#### **Level 1: Basic Understanding**

**Exercise 1.1: Variable Declaration dan Initialization**
```c
// Lengkapi kode berikut dengan deklarasi yang benar
#include <stdio.h>

int main() {
    // Deklarasikan variabel untuk menyimpan:
    // - Umur mahasiswa (integer)
    // - IPK mahasiswa (floating point)
    // - Grade huruf (character)
    // - Status lulus (boolean)
    
    // Inisialisasi dengan nilai yang sesuai
    
    // Tampilkan semua variabel dengan format yang rapi
    
    return 0;
}
```

**Exercise 1.2: Operator Aritmatika**
```c
// Implementasikan program yang menghitung:
// - Luas dan keliling persegi panjang
// - Volume dan luas permukaan kubus
// - Rata-rata dari 5 bilangan

int main() {
    // Input: panjang dan lebar untuk persegi panjang
    // Input: sisi kubus
    // Input: 5 bilangan untuk rata-rata
    
    // Hitung dan tampilkan semua hasil
    
    return 0;
}
```

#### **Level 2: Intermediate Application**

**Exercise 2.1: Grade Calculator dengan Multiple Criteria**
```c
// Buat program yang menghitung grade akhir berdasarkan:
// - Assignment (30%)
// - Midterm (25%)
// - Final Exam (35%)
// - Participation (10%)
// 
// Grade scale:
// A: 90-100, B: 80-89, C: 70-79, D: 60-69, F: <60
// 
// Tambahkan validasi input dan error handling

int main() {
    // Implementasi di sini
    return 0;
}
```

**Exercise 2.2: Bitwise Flag System**
```c
// Implementasikan sistem status dengan bit flags untuk:
// - Online/Offline status
// - Admin privileges  
// - Email notifications enabled
// - SMS notifications enabled
// - Premium account
//
// Buat fungsi untuk set, clear, toggle, dan check setiap flag

#define STATUS_ONLINE     0x01
#define STATUS_ADMIN      0x02
#define NOTIFY_EMAIL      0x04
#define NOTIFY_SMS        0x08
#define PREMIUM_ACCOUNT   0x10

// Implementasikan fungsi-fungsi untuk manipulasi flags
```

#### **Level 3: Advanced Integration**

**Exercise 3.1: Complex Expression Evaluator**
```c
// Buat program yang dapat mengevaluasi ekspresi matematika sederhana
// dengan mempertimbangkan operator precedence dan associativity
// 
// Contoh input: "3 + 4 * 2 - 8 / 2"
// Expected output: 7
//
// Dukung operator: +, -, *, /, %, ^
// Dukung parentheses untuk mengubah precedence

int main() {
    // Implementasi parser dan evaluator sederhana
    return 0;
}
```

### **7.2 Assessment Rubric**

#### **Komponen Penilaian:**

**1. Correctness (40%)**
- Program menghasilkan output yang benar
- Menangani semua test cases dengan tepat
- Logic algorithm implementasi sesuai requirement

**2. Code Quality (25%)**
- Penggunaan identifier yang descriptive
- Proper variable declaration dan initialization
- Consistent coding style dan formatting
- Appropriate use of constants

**3. Input Validation (15%)**
- Validasi tipe data input
- Handling untuk invalid input
- Graceful error handling
- User-friendly error messages

**4. Efficiency (10%)**
- Appropriate data type selection
- Efficient algorithm implementation
- Minimal memory usage
- Proper use of operators

**5. Documentation (10%)**
- Clear comments explaining complex logic
- Function documentation
- Variable purpose explanation
- Algorithm description

#### **Grading Scale:**
- **A (90-100)**: Exceptional implementation dengan semua requirements terpenuhi plus additional features
- **B (80-89)**: Good implementation dengan minor issues atau missing optional features
- **C (70-79)**: Adequate implementation dengan beberapa bugs atau incomplete features
- **D (60-69)**: Basic implementation dengan significant issues
- **F (<60)**: Incomplete atau non-functional implementation

---

## **BAGIAN 8: RANGKUMAN DAN NEXT STEPS**

### **8.1 Key Learning Outcomes**

Pada minggu ini, kita telah menguasai fundamental building blocks dari programming:

**1. Identifiers dan Keywords:**
- Aturan penamaan yang konsisten dan professional
- Understanding reserved words dalam berbagai bahasa
- Best practices untuk naming conventions

**2. Data Types Mastery:**
- Integer types: size, range, signed/unsigned variations
- Floating-point precision dan special values
- Character encoding dan representations
- Boolean logic dan operations

**3. Variable Management:**
- Declaration, definition, dan initialization patterns
- Scope dan lifetime understanding
- Constant usage untuk maintainable code

**4. Operator Proficiency:**
- Arithmetic operations dan mathematical functions
- Relational comparisons dengan proper techniques
- Logical operations dan truth tables
- Bitwise manipulations untuk low-level programming

**5. Expression Evaluation:**
- Operator precedence dan associativity mastery
- Type conversion understanding
- Complex expression debugging skills

### **8.2 Real-World Applications**

**Professional Programming Skills:**
- **Code Quality**: Writing maintainable, readable code
- **Type Safety**: Preventing common programming errors
- **Performance**: Choosing appropriate data types dan operations
- **Debugging**: Understanding expression evaluation untuk troubleshooting

**Industry Applications:**
- **Systems Programming**: Bitwise operations untuk hardware interface
- **Financial Software**: Precise floating-point calculations
- **Game Development**: Performance-critical arithmetic operations
- **Embedded Systems**: Memory-efficient variable usage

### **8.3 Assignment untuk Minggu Depan**

**Main Project: Multi-Function Calculator**

Buat program kalkulator comprehensive yang mendemonstrasikan semua konsep dari minggu ini:

**Core Requirements:**
1. **Basic arithmetic operations** dengan proper error handling
2. **Type conversion** functions (int ↔ float ↔ string)
3. **Bitwise calculator** untuk binary operations
4. **Unit converter** (temperature, length, weight)
5. **Expression validator** yang checks syntax dan precedence

**Advanced Features (Optional):**
1. **Scientific functions** (trigonometry, logarithms)
2. **Number base converter** (decimal, binary, hexadecimal, octal)
3. **Statistics calculator** (mean, median, standard deviation)
4. **Memory functions** (store, recall, clear)

**Technical Specifications:**
- Proper input validation untuk all numeric inputs
- Comprehensive error handling dengan descriptive messages
- Modular design dengan separate functions untuk each feature
- Clear user interface dengan menu system
- Documentation dengan algorithm explanations

**Submission Requirements:**
- Source code dengan proper comments
- Test cases covering edge cases dan error conditions
- User manual dengan feature descriptions
- Reflection report (750 words) on implementation challenges

### **8.4 Preparation untuk Minggu Depan**

Minggu depan kita akan explore **"Operasi Seleksi (Decision/Branching)"** yang akan mencakup:

- **IF Statements**: Simple dan nested conditions
- **IF-ELSE Structures**: Binary decision making
- **Switch-Case**: Multi-way branching
- **Conditional Operators**: Ternary dan short-circuit evaluation
- **Complex Decision Trees**: Combining multiple conditions

**Recommended Preparation:**
1. Practice dengan boolean expressions dan truth tables
2. Review logical operators (&&, ||, !) usage
3. Understand comparison operator behavior dengan different data types
4. Explore decision-making scenarios dalam real-world applications

---

## **PENUTUP**

Understanding data types, variables, dan operators adalah fundamental dalam programming journey Anda. Konsep-konsep ini merupakan building blocks yang akan Anda gunakan dalam setiap program yang akan Anda tulis, dari simple calculations hingga complex algorithms.

**Key Principles to Remember:**

1. **Choose the Right Tool**: Select appropriate data types dan operators untuk your specific needs
2. **Be Explicit**: Use clear variable names dan avoid relying pada implicit behaviors
3. **Validate Everything**: Always validate input dan handle edge cases
4. **Think About Efficiency**: Consider performance implications dari your choices
5. **Write for Humans**: Code is read more often than it's written

Kemampuan untuk work effectively dengan data types dan operators akan memungkinkan Anda untuk:
- Write more efficient dan reliable code
- Debug problems more effectively
- Understand how programs work at a fundamental level
- Build more complex programs dengan confidence

Ingatlah bahwa **"Good programming is not about knowing every operator atau data type, but about knowing when dan how to use them appropriately."**

Minggu depan, kita akan membangun fondasi ini untuk mengeksplorasi cara membuat keputusan cerdas dalam program kita menggunakan struktur seleksi.

**Happy Coding!** 🔢💻

---

*Total kata: ~5000 kata*

**Referensi:**
- W3Schools Programming Data Types: https://www.w3schools.com/programming/prog_data_types.php
- W3Schools Java Operators: https://www.w3schools.com/java/java_operators.asp
- Various programming language specifications dan best practices guides
        
