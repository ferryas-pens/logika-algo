# Minggu 12: Pointer dalam Bahasa C
## Logika dan Pemrograman

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. **Memahami konsep fundamental pointer** sebagai variabel yang menyimpan alamat memori
2. **Menguasai deklarasi dan inisialisasi pointer** dengan berbagai tipe data
3. **Mengimplementasikan pointer arithmetic** dan operasi-operasi pointer
4. **Memahami relationship pointer dengan array** dan string
5. **Menguasai dynamic memory allocation** menggunakan malloc, calloc, realloc, dan free
6. **Mengimplementasikan pointer to pointer** dan complex pointer scenarios
7. **Memahami function pointers** dan callback mechanisms
8. **Menghindari common pointer errors** dan mengembangkan safe pointer practices

---

## 📊 Konsep Dasar Pointer

### Pengertian Pointer

Pointer adalah variabel yang menyimpan alamat memori dari variabel lain. Alih-alih menyimpan nilai data secara langsung, pointer menyimpan lokasi di mana data tersebut berada dalam memori. Pointer merupakan salah satu fitur paling powerful dalam bahasa C yang memungkinkan manipulasi memori secara langsung, passing by reference, dynamic memory allocation, dan implementasi struktur data kompleks.

### Mengapa Pointer Penting?

1. **Efisiensi Memori**: Passing large data structures by reference lebih efisien
2. **Dynamic Memory**: Alokasi memori saat runtime untuk flexibility
3. **Data Structures**: Implementasi linked lists, trees, graphs
4. **Function Parameters**: Memungkinkan fungsi memodifikasi variabel caller
5. **Hardware Access**: Direct memory access untuk system programming
6. **Performance**: Operasi pointer lebih cepat untuk data manipulation

### Memory dan Addressing

```c
#include <stdio.h>

int main() {
    int x = 42;
    float y = 3.14;
    char z = 'A';
    
    printf("=== MEMORY AND ADDRESSING ===\n");
    printf("Variable | Value | Address         | Size\n");
    printf("---------|-------|-----------------|------\n");
    printf("x        | %d    | %p | %zu bytes\n", x, (void*)&x, sizeof(x));
    printf("y        | %.2f  | %p | %zu bytes\n", y, (void*)&y, sizeof(y));
    printf("z        | %c     | %p | %zu byte\n", z, (void*)&z, sizeof(z));
    
    // Memory visualization
    printf("\nMemory Layout (conceptual):\n");
    printf("Address    | Content\n");
    printf("-----------|--------\n");
    printf("%p | %d (x)\n", (void*)&x, x);
    printf("%p | %.2f (y)\n", (void*)&y, y);
    printf("%p | %c (z)\n", (void*)&z, z);
    
    return 0;
}
```

---

## 🔧 Deklarasi dan Operasi Dasar Pointer

### Sintaks Deklarasi Pointer

```c
data_type *pointer_name;
```

### Operasi Dasar Pointer

```c
#include <stdio.h>

int main() {
    // Deklarasi dan inisialisasi
    int num = 100;
    int *ptr = &num;  // ptr points to num
    int *ptr2;        // Uninitialized pointer (dangerous!)
    int *ptr3 = NULL; // NULL pointer (safe initialization)
    
    printf("=== BASIC POINTER OPERATIONS ===\n");
    
    // Address-of operator (&)
    printf("\n1. Address-of Operator (&):\n");
    printf("   Value of num: %d\n", num);
    printf("   Address of num (&num): %p\n", (void*)&num);
    
    // Dereference operator (*)
    printf("\n2. Dereference Operator (*):\n");
    printf("   Value of ptr (address): %p\n", (void*)ptr);
    printf("   Value pointed by ptr (*ptr): %d\n", *ptr);
    
    // Modifying value through pointer
    printf("\n3. Modifying through Pointer:\n");
    printf("   Before: num = %d\n", num);
    *ptr = 200;
    printf("   After (*ptr = 200): num = %d\n", num);
    
    // Pointer assignment
    printf("\n4. Pointer Assignment:\n");
    int another = 300;
    printf("   Before: ptr points to %p (value: %d)\n", (void*)ptr, *ptr);
    ptr = &another;
    printf("   After (ptr = &another): ptr points to %p (value: %d)\n", 
           (void*)ptr, *ptr);
    
    // NULL pointer check
    printf("\n5. NULL Pointer Check:\n");
    if (ptr3 == NULL) {
        printf("   ptr3 is NULL (safe to check before use)\n");
    }
    
    // Size of pointer
    printf("\n6. Pointer Sizes:\n");
    printf("   sizeof(int): %zu bytes\n", sizeof(int));
    printf("   sizeof(int*): %zu bytes\n", sizeof(int*));
    printf("   sizeof(char*): %zu bytes\n", sizeof(char*));
    printf("   sizeof(double*): %zu bytes\n", sizeof(double*));
    printf("   Note: All pointers have same size on a given system\n");
    
    return 0;
}
```

### Pointer dengan Berbagai Tipe Data

```c
#include <stdio.h>

int main() {
    // Integer pointer
    int intVar = 42;
    int *intPtr = &intVar;
    
    // Float pointer
    float floatVar = 3.14159;
    float *floatPtr = &floatVar;
    
    // Character pointer
    char charVar = 'Z';
    char *charPtr = &charVar;
    
    // Double pointer
    double doubleVar = 2.71828;
    double *doublePtr = &doubleVar;
    
    printf("=== POINTERS WITH DIFFERENT DATA TYPES ===\n");
    printf("Type     | Variable | Value    | Pointer Addr    | Pointed Value\n");
    printf("---------|----------|----------|-----------------|---------------\n");
    printf("int      | intVar   | %d      | %p | %d\n", 
           intVar, (void*)intPtr, *intPtr);
    printf("float    | floatVar | %.5f | %p | %.5f\n", 
           floatVar, (void*)floatPtr, *floatPtr);
    printf("char     | charVar  | %c       | %p | %c\n", 
           charVar, (void*)charPtr, *charPtr);
    printf("double   | dblVar   | %.5f | %p | %.5f\n", 
           doubleVar, (void*)doublePtr, *doublePtr);
    
    // Type safety demonstration
    printf("\n=== TYPE SAFETY ===\n");
    // intPtr = &floatVar;  // Compiler warning: incompatible pointer types
    // Correct way with casting (but be careful!)
    intPtr = (int*)&floatVar;
    printf("Float %f interpreted as int: %d (undefined behavior!)\n", 
           floatVar, *intPtr);
    
    return 0;
}
```

---

## 🔢 Pointer Arithmetic

### Arithmetic Operations on Pointers

```c
#include <stdio.h>

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int *ptr = arr;  // Points to first element
    
    printf("=== POINTER ARITHMETIC ===\n");
    printf("Array: {10, 20, 30, 40, 50}\n");
    printf("Initial ptr points to: %p (value: %d)\n\n", (void*)ptr, *ptr);
    
    // Increment operator
    printf("1. Increment (ptr++):\n");
    printf("   Before: ptr = %p, *ptr = %d\n", (void*)ptr, *ptr);
    ptr++;
    printf("   After:  ptr = %p, *ptr = %d\n", (void*)ptr, *ptr);
    printf("   Note: Moved by sizeof(int) = %zu bytes\n\n", sizeof(int));
    
    // Addition
    printf("2. Addition (ptr + 2):\n");
    printf("   Current: ptr = %p, *ptr = %d\n", (void*)ptr, *ptr);
    printf("   ptr + 2 = %p, *(ptr + 2) = %d\n\n", 
           (void*)(ptr + 2), *(ptr + 2));
    
    // Decrement
    printf("3. Decrement (ptr--):\n");
    ptr = &arr[3];  // Reset to 4th element
    printf("   Before: ptr = %p, *ptr = %d\n", (void*)ptr, *ptr);
    ptr--;
    printf("   After:  ptr = %p, *ptr = %d\n\n", (void*)ptr, *ptr);
    
    // Pointer difference
    printf("4. Pointer Difference:\n");
    int *ptr1 = &arr[1];
    int *ptr2 = &arr[4];
    printf("   ptr2 - ptr1 = %ld elements\n", ptr2 - ptr1);
    printf("   Distance in bytes: %ld\n\n", 
           (char*)ptr2 - (char*)ptr1);
    
    // Array traversal using pointer arithmetic
    printf("5. Array Traversal with Pointer:\n");
    ptr = arr;
    for(int i = 0; i < 5; i++) {
        printf("   *(ptr + %d) = %d\n", i, *(ptr + i));
    }
    
    // Alternative notation
    printf("\n6. Equivalent Notations:\n");
    printf("   arr[2] = %d\n", arr[2]);
    printf("   *(arr + 2) = %d\n", *(arr + 2));
    printf("   2[arr] = %d (valid but unusual!)\n", 2[arr]);
    printf("   *(2 + arr) = %d\n", *(2 + arr));
    
    return 0;
}
```

### Pointer Arithmetic with Different Types

```c
#include <stdio.h>

int main() {
    char charArr[] = "ABCDE";
    int intArr[] = {100, 200, 300, 400, 500};
    double doubleArr[] = {1.1, 2.2, 3.3, 4.4, 5.5};
    
    char *charPtr = charArr;
    int *intPtr = intArr;
    double *doublePtr = doubleArr;
    
    printf("=== POINTER ARITHMETIC WITH DIFFERENT TYPES ===\n");
    printf("Type   | Initial Address | +1 Address      | Increment\n");
    printf("-------|-----------------|-----------------|----------\n");
    
    printf("char   | %p | %p | %ld byte\n", 
           (void*)charPtr, (void*)(charPtr + 1), 
           (char*)(charPtr + 1) - charPtr);
    
    printf("int    | %p | %p | %ld bytes\n", 
           (void*)intPtr, (void*)(intPtr + 1), 
           (char*)(intPtr + 1) - (char*)intPtr);
    
    printf("double | %p | %p | %ld bytes\n", 
           (void*)doublePtr, (void*)(doublePtr + 1), 
           (char*)(doublePtr + 1) - (char*)doublePtr);
    
    printf("\nConclusion: Pointer arithmetic scales by sizeof(type)\n");
    
    return 0;
}
```

---

## 🔗 Pointers and Arrays

### Array-Pointer Relationship

```c
#include <stdio.h>

void printArrayUsingPointer(int *arr, int size) {
    printf("Array elements: ");
    for(int i = 0; i < size; i++) {
        printf("%d ", *(arr + i));
    }
    printf("\n");
}

void demonstrateArrayPointerEquivalence() {
    int numbers[] = {15, 25, 35, 45, 55};
    int *ptr = numbers;
    
    printf("\n=== ARRAY-POINTER EQUIVALENCE ===\n");
    
    // Array name as pointer
    printf("Array name 'numbers': %p\n", (void*)numbers);
    printf("Address of first element: %p\n", (void*)&numbers[0]);
    printf("These are identical!\n\n");
    
    // Different ways to access elements
    printf("Element Access Methods:\n");
    for(int i = 0; i < 5; i++) {
        printf("Index %d:\n", i);
        printf("  numbers[%d] = %d\n", i, numbers[i]);
        printf("  *(numbers + %d) = %d\n", i, *(numbers + i));
        printf("  ptr[%d] = %d\n", i, ptr[i]);
        printf("  *(ptr + %d) = %d\n", i, *(ptr + i));
    }
    
    // Key difference
    printf("\n=== KEY DIFFERENCE ===\n");
    printf("sizeof(numbers) = %zu (entire array)\n", sizeof(numbers));
    printf("sizeof(ptr) = %zu (pointer size)\n", sizeof(ptr));
}

int main() {
    int data[] = {100, 200, 300, 400, 500};
    
    printf("=== POINTERS AND ARRAYS ===\n");
    
    // Pass array to function
    printArrayUsingPointer(data, 5);
    
    // Demonstrate equivalence
    demonstrateArrayPointerEquivalence();
    
    // 2D arrays and pointers
    int matrix[3][4] = {
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12}
    };
    
    printf("\n=== 2D ARRAYS AND POINTERS ===\n");
    int (*rowPtr)[4] = matrix;  // Pointer to array of 4 ints
    
    for(int i = 0; i < 3; i++) {
        printf("Row %d: ", i);
        for(int j = 0; j < 4; j++) {
            printf("%d ", *(*(rowPtr + i) + j));
        }
        printf("\n");
    }
    
    return 0;
}
```

---

## 🎭 Pointers and Strings

```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

// Custom string length using pointer
int myStrlen(const char *str) {
    const char *ptr = str;
    while(*ptr != '\0') {
        ptr++;
    }
    return ptr - str;
}

// Custom string copy using pointers
void myStrcpy(char *dest, const char *src) {
    while((*dest++ = *src++) != '\0');
}

// Custom string concatenation
void myStrcat(char *dest, const char *src) {
    // Move to end of dest
    while(*dest != '\0') {
        dest++;
    }
    // Copy src
    while((*dest++ = *src++) != '\0');
}

// Reverse string using pointers
void reverseString(char *str) {
    char *start = str;
    char *end = str + strlen(str) - 1;
    
    while(start < end) {
        char temp = *start;
        *start = *end;
        *end = temp;
        start++;
        end--;
    }
}

int main() {
    // String literals vs character arrays
    char arr[] = "Hello";        // Modifiable
    char *ptr = "World";         // Points to string literal (read-only)
    char buffer[100];
    
    printf("=== POINTERS AND STRINGS ===\n");
    
    printf("\n1. String Storage:\n");
    printf("   Character array: %s (modifiable)\n", arr);
    printf("   Pointer to literal: %s (read-only)\n", ptr);
    
    // Modifying character array is OK
    arr[0] = 'h';
    printf("   Modified array: %s\n", arr);
    
    // ptr[0] = 'w';  // This would cause segmentation fault!
    
    printf("\n2. String Functions with Pointers:\n");
    printf("   Length of '%s': %d\n", arr, myStrlen(arr));
    
    myStrcpy(buffer, "Hello ");
    printf("   After strcpy: %s\n", buffer);
    
    myStrcat(buffer, "Pointer!");
    printf("   After strcat: %s\n", buffer);
    
    reverseString(buffer);
    printf("   After reverse: %s\n", buffer);
    
    // Array of strings using pointers
    printf("\n3. Array of Strings:\n");
    const char *colors[] = {"Red", "Green", "Blue", "Yellow", "Purple"};
    int numColors = sizeof(colors) / sizeof(colors[0]);
    
    for(int i = 0; i < numColors; i++) {
        printf("   colors[%d] = %s (at %p)\n", 
               i, colors[i], (void*)colors[i]);
    }
    
    // Dynamic string
    printf("\n4. Dynamic String Allocation:\n");
    char *dynamicStr = (char*)malloc(50 * sizeof(char));
    if(dynamicStr != NULL) {
        strcpy(dynamicStr, "Dynamically allocated string");
        printf("   %s\n", dynamicStr);
        
        // Resize
        dynamicStr = (char*)realloc(dynamicStr, 100 * sizeof(char));
        strcat(dynamicStr, " - now extended!");
        printf("   %s\n", dynamicStr);
        
        free(dynamicStr);
    }
    
    return 0;
}
```

---

## 💾 Dynamic Memory Allocation

### Memory Management Functions

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    printf("=== DYNAMIC MEMORY ALLOCATION ===\n");
    
    // 1. malloc() - Memory Allocation
    printf("\n1. malloc() - Allocate memory:\n");
    int *arr1 = (int*)malloc(5 * sizeof(int));
    
    if(arr1 == NULL) {
        printf("   Memory allocation failed!\n");
        return 1;
    }
    
    printf("   Allocated %zu bytes for 5 integers\n", 5 * sizeof(int));
    printf("   Note: Memory is uninitialized (contains garbage)\n");
    
    for(int i = 0; i < 5; i++) {
        arr1[i] = (i + 1) * 10;
    }
    
    printf("   Array after initialization: ");
    for(int i = 0; i < 5; i++) {
        printf("%d ", arr1[i]);
    }
    printf("\n");
    
    // 2. calloc() - Contiguous Allocation
    printf("\n2. calloc() - Allocate and initialize to zero:\n");
    int *arr2 = (int*)calloc(5, sizeof(int));
    
    if(arr2 == NULL) {
        printf("   Memory allocation failed!\n");
        free(arr1);
        return 1;
    }
    
    printf("   Array after calloc: ");
    for(int i = 0; i < 5; i++) {
        printf("%d ", arr2[i]);  // All zeros
    }
    printf("\n");
    
    // 3. realloc() - Resize memory
    printf("\n3. realloc() - Resize allocated memory:\n");
    printf("   Original size: 5 integers\n");
    
    arr1 = (int*)realloc(arr1, 10 * sizeof(int));
    if(arr1 == NULL) {
        printf("   Reallocation failed!\n");
        free(arr2);
        return 1;
    }
    
    printf("   Resized to 10 integers\n");
    
    // Initialize new elements
    for(int i = 5; i < 10; i++) {
        arr1[i] = (i + 1) * 10;
    }
    
    printf("   Extended array: ");
    for(int i = 0; i < 10; i++) {
        printf("%d ", arr1[i]);
    }
    printf("\n");
    
    // 4. free() - Deallocate memory
    printf("\n4. free() - Release allocated memory:\n");
    free(arr1);
    free(arr2);
    printf("   Memory freed successfully\n");
    printf("   Important: Always free allocated memory to prevent leaks!\n");
    
    // Common mistakes demonstration
    printf("\n=== COMMON MISTAKES ===\n");
    printf("1. Using freed memory (dangling pointer) - DON'T DO THIS!\n");
    printf("2. Memory leaks (forgetting to free) - AVOID!\n");
    printf("3. Double free (freeing same memory twice) - DANGEROUS!\n");
    
    return 0;
}
```

### Dynamic Array Example

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int *data;
    int size;
    int capacity;
} DynamicArray;

DynamicArray* createArray(int initialCapacity) {
    DynamicArray *arr = (DynamicArray*)malloc(sizeof(DynamicArray));
    if(arr == NULL) return NULL;
    
    arr->data = (int*)malloc(initialCapacity * sizeof(int));
    if(arr->data == NULL) {
        free(arr);
        return NULL;
    }
    
    arr->size = 0;
    arr->capacity = initialCapacity;
    return arr;
}

void push(DynamicArray *arr, int value) {
    if(arr->size >= arr->capacity) {
        // Double the capacity
        arr->capacity *= 2;
        arr->data = (int*)realloc(arr->data, arr->capacity * sizeof(int));
        if(arr->data == NULL) {
            printf("Failed to expand array!\n");
            return;
        }
        printf("Array expanded to capacity %d\n", arr->capacity);
    }
    
    arr->data[arr->size++] = value;
}

void printArray(DynamicArray *arr) {
    printf("Array (size=%d, capacity=%d): ", arr->size, arr->capacity);
    for(int i = 0; i < arr->size; i++) {
        printf("%d ", arr->data[i]);
    }
    printf("\n");
}

void freeArray(DynamicArray *arr) {
    if(arr != NULL) {
        free(arr->data);
        free(arr);
    }
}

int main() {
    printf("=== DYNAMIC ARRAY IMPLEMENTATION ===\n");
    
    DynamicArray *myArray = createArray(2);
    if(myArray == NULL) {
        printf("Failed to create array!\n");
        return 1;
    }
    
    printf("Adding elements to dynamic array:\n");
    for(int i = 1; i <= 10; i++) {
        printf("Adding %d: ", i * 10);
        push(myArray, i * 10);
        printArray(myArray);
    }
    
    freeArray(myArray);
    printf("\nDynamic array freed successfully!\n");
    
    return 0;
}
```

---

## 🔄 Pointer to Pointer

```c
#include <stdio.h>
#include <stdlib.h>

void allocateMemory(int **ptr, int size) {
    *ptr = (int*)malloc(size * sizeof(int));
    if(*ptr != NULL) {
        for(int i = 0; i < size; i++) {
            (*ptr)[i] = i + 1;
        }
    }
}

void swapPointers(int **ptr1, int **ptr2) {
    int *temp = *ptr1;
    *ptr1 = *ptr2;
    *ptr2 = temp;
}

int main() {
    printf("=== POINTER TO POINTER ===\n");
    
    // Basic pointer to pointer
    int value = 42;
    int *ptr = &value;
    int **pptr = &ptr;
    
    printf("\n1. Basic Pointer to Pointer:\n");
    printf("   value = %d\n", value);
    printf("   *ptr = %d\n", *ptr);
    printf("   **pptr = %d\n", **pptr);
    printf("   Address chain: pptr(%p) -> ptr(%p) -> value(%p)\n",
           (void*)pptr, (void*)ptr, (void*)&value);
    
    // Modifying through pointer to pointer
    **pptr = 100;
    printf("   After **pptr = 100, value = %d\n", value);
    
    // Dynamic allocation using pointer to pointer
    printf("\n2. Dynamic Allocation with Pointer to Pointer:\n");
    int *dynamicArr = NULL;
    allocateMemory(&dynamicArr, 5);
    
    if(dynamicArr != NULL) {
        printf("   Allocated array: ");
        for(int i = 0; i < 5; i++) {
            printf("%d ", dynamicArr[i]);
        }
        printf("\n");
    }
    
    // 2D dynamic array
    printf("\n3. Dynamic 2D Array:\n");
    int rows = 3, cols = 4;
    int **matrix = (int**)malloc(rows * sizeof(int*));
    
    for(int i = 0; i < rows; i++) {
        matrix[i] = (int*)malloc(cols * sizeof(int));
        for(int j = 0; j < cols; j++) {
            matrix[i][j] = i * cols + j + 1;
        }
    }
    
    printf("   2D Array:\n");
    for(int i = 0; i < rows; i++) {
        printf("   ");
        for(int j = 0; j < cols; j++) {
            printf("%3d ", matrix[i][j]);
        }
        printf("\n");
    }
    
    // Swap pointers
    printf("\n4. Swapping Pointers:\n");
    int arr1[] = {1, 2, 3};
    int arr2[] = {7, 8, 9};
    int *p1 = arr1;
    int *p2 = arr2;
    
    printf("   Before swap: p1[0]=%d, p2[0]=%d\n", p1[0], p2[0]);
    swapPointers(&p1, &p2);
    printf("   After swap:  p1[0]=%d, p2[0]=%d\n", p1[0], p2[0]);
    
    // Cleanup
    free(dynamicArr);
    for(int i = 0; i < rows; i++) {
        free(matrix[i]);
    }
    free(matrix);
    
    return 0;
}
```

---

## 🎯 Function Pointers

```c
#include <stdio.h>
#include <stdlib.h>

// Function prototypes
int add(int a, int b) { return a + b; }
int subtract(int a, int b) { return a - b; }
int multiply(int a, int b) { return a * b; }
int divide(int a, int b) { return b != 0 ? a / b : 0; }

// Function that takes function pointer as parameter
int calculate(int a, int b, int (*operation)(int, int)) {
    return operation(a, b);
}

// Comparison functions for sorting
int ascending(const void *a, const void *b) {
    return (*(int*)a - *(int*)b);
}

int descending(const void *a, const void *b) {
    return (*(int*)b - *(int*)a);
}

// Callback example
void processArray(int arr[], int size, void (*callback)(int)) {
    for(int i = 0; i < size; i++) {
        callback(arr[i]);
    }
}

void printSquare(int n) {
    printf("%d^2 = %d\n", n, n * n);
}

int main() {
    printf("=== FUNCTION POINTERS ===\n");
    
    // 1. Basic function pointer
    printf("\n1. Basic Function Pointer:\n");
    int (*funcPtr)(int, int);
    funcPtr = add;
    
    int result = funcPtr(10, 5);
    printf("   add(10, 5) via pointer = %d\n", result);
    
    funcPtr = multiply;
    result = funcPtr(10, 5);
    printf("   multiply(10, 5) via pointer = %d\n", result);
    
    // 2. Array of function pointers
    printf("\n2. Array of Function Pointers (Calculator):\n");
    int (*operations[4])(int, int) = {add, subtract, multiply, divide};
    char *opNames[] = {"+", "-", "*", "/"};
    
    int a = 20, b = 5;
    for(int i = 0; i < 4; i++) {
        printf("   %d %s %d = %d\n", a, opNames[i], b, operations[i](a, b));
    }
    
    // 3. Function pointer as parameter
    printf("\n3. Function Pointer as Parameter:\n");
    printf("   calculate(15, 3, add) = %d\n", calculate(15, 3, add));
    printf("   calculate(15, 3, subtract) = %d\n", calculate(15, 3, subtract));
    
    // 4. Using with qsort
    printf("\n4. Function Pointers with qsort:\n");
    int numbers[] = {5, 2, 8, 1, 9, 3, 7};
    int size = sizeof(numbers) / sizeof(numbers[0]);
    
    printf("   Original: ");
    for(int i = 0; i < size; i++) printf("%d ", numbers[i]);
    printf("\n");
    
    qsort(numbers, size, sizeof(int), descending);
    printf("   Descending: ");
    for(int i = 0; i < size; i++) printf("%d ", numbers[i]);
    printf("\n");
    
    // 5. Callback function
    printf("\n5. Callback Functions:\n");
    int data[] = {2, 3, 4, 5};
    processArray(data, 4, printSquare);
    
    return 0;
}
```

---

## 💼 Studi Kasus: Linked List Implementation

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;
    struct Node *next;
} Node;

typedef struct {
    Node *head;
    int size;
} LinkedList;

// Create new node
Node* createNode(int data) {
    Node *newNode = (Node*)malloc(sizeof(Node));
    if(newNode == NULL) {
        printf("Memory allocation failed!\n");
        return NULL;
    }
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

// Initialize linked list
LinkedList* createList() {
    LinkedList *list = (LinkedList*)malloc(sizeof(LinkedList));
    if(list == NULL) return NULL;
    list->head = NULL;
    list->size = 0;
    return list;
}

// Insert at beginning
void insertAtBeginning(LinkedList *list, int data) {
    Node *newNode = createNode(data);
    if(newNode == NULL) return;
    
    newNode->next = list->head;
    list->head = newNode;
    list->size++;
    printf("Inserted %d at beginning\n", data);
}

// Insert at end
void insertAtEnd(LinkedList *list, int data) {
    Node *newNode = createNode(data);
    if(newNode == NULL) return;
    
    if(list->head == NULL) {
        list->head = newNode;
    } else {
        Node *current = list->head;
        while(current->next != NULL) {
            current = current->next;
        }
        current->next = newNode;
    }
    list->size++;
    printf("Inserted %d at end\n", data);
}

// Insert at position
void insertAtPosition(LinkedList *list, int data, int position) {
    if(position < 0 || position > list->size) {
        printf("Invalid position!\n");
        return;
    }
    
    if(position == 0) {
        insertAtBeginning(list, data);
        return;
    }
    
    Node *newNode = createNode(data);
    if(newNode == NULL) return;
    
    Node *current = list->head;
    for(int i = 0; i < position - 1; i++) {
        current = current->next;
    }
    
    newNode->next = current->next;
    current->next = newNode;
    list->size++;
    printf("Inserted %d at position %d\n", data, position);
}

// Delete from beginning
void deleteFromBeginning(LinkedList *list) {
    if(list->head == NULL) {
        printf("List is empty!\n");
        return;
    }
    
    Node *temp = list->head;
    int data = temp->data;
    list->head = list->head->next;
    free(temp);
    list->size--;
    printf("Deleted %d from beginning\n", data);
}

// Delete by value
void deleteByValue(LinkedList *list, int value) {
    if(list->head == NULL) {
        printf("List is empty!\n");
        return;
    }
    
    if(list->head->data == value) {
        deleteFromBeginning(list);
        return;
    }
    
    Node *current = list->head;
    Node *prev = NULL;
    
    while(current != NULL && current->data != value) {
        prev = current;
        current = current->next;
    }
    
    if(current == NULL) {
        printf("Value %d not found!\n", value);
        return;
    }
    
    prev->next = current->next;
    free(current);
    list->size--;
    printf("Deleted %d from list\n", value);
}

// Search element
int search(LinkedList *list, int value) {
    Node *current = list->head;
    int position = 0;
    
    while(current != NULL) {
        if(current->data == value) {
            return position;
        }
        current = current->next;
        position++;
    }
    
    return -1;
}

// Display list
void displayList(LinkedList *list) {
    if(list->head == NULL) {
        printf("List is empty\n");
        return;
    }
    
    printf("List (size=%d): ", list->size);
    Node *current = list->head;
    while(current != NULL) {
        printf("%d", current->data);
        if(current->next != NULL) printf(" -> ");
        current = current->next;
    }
    printf(" -> NULL\n");
}

// Reverse list
void reverseList(LinkedList *list) {
    Node *prev = NULL;
    Node *current = list->head;
    Node *next = NULL;
    
    while(current != NULL) {
        next = current->next;
        current->next = prev;
        prev = current;
        current = next;
    }
    
    list->head = prev;
    printf("List reversed\n");
}

// Free entire list
void freeList(LinkedList *list) {
    Node *current = list->head;
    Node *next;
    
    while(current != NULL) {
        next = current->next;
        free(current);
        current = next;
    }
    
    free(list);
    printf("List freed\n");
}

int main() {
    printf("=== LINKED LIST IMPLEMENTATION ===\n\n");
    
    LinkedList *myList = createList();
    
    // Insert operations
    printf("1. Insertion Operations:\n");
    insertAtBeginning(myList, 10);
    insertAtEnd(myList, 20);
    insertAtBeginning(myList, 5);
    insertAtEnd(myList, 30);
    insertAtPosition(myList, 15, 2);
    displayList(myList);
    
    // Search operation
    printf("\n2. Search Operation:\n");
    int searchValue = 15;
    int position = search(myList, searchValue);
    if(position != -1) {
        printf("   %d found at position %d\n", searchValue, position);
    } else {
        printf("   %d not found\n", searchValue);
    }
    
    // Delete operations
    printf("\n3. Deletion Operations:\n");
    deleteFromBeginning(myList);
    displayList(myList);
    deleteByValue(myList, 20);
    displayList(myList);
    
    // Reverse list
    printf("\n4. Reverse Operation:\n");
    reverseList(myList);
    displayList(myList);
    
    // Cleanup
    printf("\n5. Cleanup:\n");
    freeList(myList);
    
    return 0;
}
```

---

## 🛡️ Common Pointer Errors and Best Practices

### Common Errors

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void demonstrateCommonErrors() {
    printf("=== COMMON POINTER ERRORS ===\n");
    
    // 1. Uninitialized pointer
    printf("\n1. Uninitialized Pointer (DON'T DO THIS):\n");
    // int *ptr;  // Uninitialized - contains garbage
    // *ptr = 10; // CRASH! Segmentation fault
    printf("   Always initialize: int *ptr = NULL;\n");
    
    // 2. NULL pointer dereference
    printf("\n2. NULL Pointer Dereference:\n");
    int *ptr = NULL;
    // *ptr = 10;  // CRASH!
    printf("   Always check: if(ptr != NULL) { use ptr }\n");
    
    // 3. Dangling pointer
    printf("\n3. Dangling Pointer:\n");
    int *dangling = (int*)malloc(sizeof(int));
    *dangling = 42;
    free(dangling);
    // *dangling = 100;  // UNDEFINED BEHAVIOR!
    printf("   After free, set to NULL: ptr = NULL;\n");
    
    // 4. Memory leak
    printf("\n4. Memory Leak:\n");
    // for(int i = 0; i < 1000; i++) {
    //     int *leak = (int*)malloc(sizeof(int));
    //     // Forgot to free!
    // }
    printf("   Always free allocated memory!\n");
    
    // 5. Buffer overflow
    printf("\n5. Buffer Overflow:\n");
    char buffer[10];
    // strcpy(buffer, "This string is way too long!");  // OVERFLOW!
    printf("   Use safe functions: strncpy, snprintf\n");
    
    // 6. Double free
    printf("\n6. Double Free:\n");
    int *dbl = (int*)malloc(sizeof(int));
    free(dbl);
    // free(dbl);  // CRASH! Double free
    printf("   Free only once, then set to NULL\n");
    
    // 7. Incorrect pointer arithmetic
    printf("\n7. Incorrect Pointer Arithmetic:\n");
    int arr[5] = {1, 2, 3, 4, 5};
    int *p = arr;
    // p = p + 10;  // Goes beyond array bounds
    // *p = 100;    // UNDEFINED BEHAVIOR!
    printf("   Stay within bounds when using arithmetic\n");
}

void demonstrateBestPractices() {
    printf("\n=== BEST PRACTICES ===\n");
    
    // 1. Initialize pointers
    printf("\n1. Always Initialize Pointers:\n");
    int *ptr = NULL;  // Good practice
    printf("   Initialized to NULL\n");
    
    // 2. Check allocation success
    printf("\n2. Check Allocation Success:\n");
    int *arr = (int*)malloc(10 * sizeof(int));
    if(arr == NULL) {
        printf("   Allocation failed - handle error\n");
        return;
    }
    printf("   Allocation successful\n");
    
    // 3. Use const for read-only
    printf("\n3. Use const for Read-Only:\n");
    const char *message = "Read-only string";
    printf("   Protected: %s\n", message);
    
    // 4. Free and nullify
    printf("\n4. Free and Nullify:\n");
    free(arr);
    arr = NULL;  // Prevent use after free
    printf("   Freed and set to NULL\n");
    
    // 5. Validate pointer before use
    printf("\n5. Validate Before Use:\n");
    if(arr != NULL) {
        // Safe to use
    } else {
        printf("   Pointer is NULL - skipping operation\n");
    }
    
    // 6. Use appropriate sizes
    printf("\n6. Use sizeof() Correctly:\n");
    int *numbers = (int*)malloc(5 * sizeof(int));  // Good
    // NOT: malloc(5 * 4);  // Assumes int is 4 bytes
    if(numbers != NULL) {
        printf("   Allocated using sizeof(int)\n");
        free(numbers);
    }
}

int main() {
    demonstrateCommonErrors();
    demonstrateBestPractices();
    
    printf("\n=== GOLDEN RULES ===\n");
    printf("1. Initialize all pointers (preferably to NULL)\n");
    printf("2. Check for NULL before dereferencing\n");
    printf("3. Free allocated memory exactly once\n");
    printf("4. Set pointer to NULL after freeing\n");
    printf("5. Don't return addresses of local variables\n");
    printf("6. Use const for pointers to read-only data\n");
    printf("7. Validate array bounds in pointer arithmetic\n");
    printf("8. Use tools like valgrind to detect memory issues\n");
    
    return 0;
}
```

---

## 💡 Advanced Pointer Concepts

### Void Pointers and Generic Programming

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Generic swap function using void pointers
void genericSwap(void *a, void *b, size_t size) {
    unsigned char *temp = (unsigned char*)malloc(size);
    if(temp == NULL) return;
    
    memcpy(temp, a, size);
    memcpy(a, b, size);
    memcpy(b, temp, size);
    
    free(temp);
}

// Generic print function
void printArray(void *arr, int count, size_t size, void (*printFunc)(void*)) {
    for(int i = 0; i < count; i++) {
        printFunc((char*)arr + i * size);
        printf(" ");
    }
    printf("\n");
}

void printInt(void *n) {
    printf("%d", *(int*)n);
}

void printFloat(void *f) {
    printf("%.2f", *(float*)f);
}

void printChar(void *c) {
    printf("%c", *(char*)c);
}

int main() {
    printf("=== VOID POINTERS AND GENERIC PROGRAMMING ===\n");
    
    // 1. Void pointer basics
    printf("\n1. Void Pointer Basics:\n");
    int x = 42;
    float y = 3.14;
    char z = 'A';
    
    void *vptr;
    
    vptr = &x;
    printf("   Integer via void*: %d\n", *(int*)vptr);
    
    vptr = &y;
    printf("   Float via void*: %.2f\n", *(float*)vptr);
    
    vptr = &z;
    printf("   Char via void*: %c\n", *(char*)vptr);
    
    // 2. Generic swap
    printf("\n2. Generic Swap Function:\n");
    int a = 10, b = 20;
    printf("   Before: a=%d, b=%d\n", a, b);
    genericSwap(&a, &b, sizeof(int));
    printf("   After:  a=%d, b=%d\n", a, b);
    
    float f1 = 1.5, f2 = 2.5;
    printf("   Before: f1=%.1f, f2=%.1f\n", f1, f2);
    genericSwap(&f1, &f2, sizeof(float));
    printf("   After:  f1=%.1f, f2=%.1f\n", f1, f2);
    
    // 3. Generic array printing
    printf("\n3. Generic Array Printing:\n");
    int intArr[] = {1, 2, 3, 4, 5};
    float floatArr[] = {1.1, 2.2, 3.3, 4.4};
    char charArr[] = {'H', 'E', 'L', 'L', 'O'};
    
    printf("   Int array: ");
    printArray(intArr, 5, sizeof(int), printInt);
    
    printf("   Float array: ");
    printArray(floatArr, 4, sizeof(float), printFloat);
    
    printf("   Char array: ");
    printArray(charArr, 5, sizeof(char), printChar);
    
    return 0;
}
```

---

## 🎯 Kesimpulan

### Ringkasan Materi

Dalam minggu ke-12 ini, kita telah mempelajari konsep pointer dalam bahasa C secara komprehensif:

#### 1. **Fundamental Concepts**
- Pengertian pointer sebagai variabel yang menyimpan alamat
- Operator & (address-of) dan * (dereference)
- Deklarasi dan inisialisasi pointer

#### 2. **Pointer Arithmetic**
- Increment dan decrement operations
- Scaling berdasarkan tipe data
- Pointer difference dan comparison

#### 3. **Pointers with Arrays and Strings**
- Array-pointer relationship
- String manipulation dengan pointer
- Dynamic strings

#### 4. **Dynamic Memory Management**
- malloc(), calloc(), realloc(), free()
- Memory leaks dan dangling pointers
- Best practices untuk memory management

#### 5. **Advanced Concepts**
- Pointer to pointer
- Function pointers dan callbacks
- Void pointers untuk generic programming

#### 6. **Practical Implementation**
- Linked list implementation
- Dynamic array
- Generic functions

### Key Takeaways

1. **Pointers provide direct memory access** untuk efficient programming
2. **Pointer arithmetic** scales berdasarkan sizeof(type)
3. **Dynamic memory** harus selalu di-free untuk mencegah leaks
4. **NULL checking** essential untuk pointer safety
5. **Function pointers** enable callbacks dan dynamic behavior
6. **Pointer-array duality** fundamental dalam C
7. **Generic programming** possible dengan void pointers

### Integrasi dengan Materi Sebelumnya

- **Minggu 11**: Arrays dan pointer relationship
- **Minggu 10**: Functions dan parameter passing by reference
- **Minggu 7**: Operators termasuk address-of dan dereference
- **Minggu 4**: Data types dan memory representation

### Common Pitfalls to Avoid

1. Uninitialized pointers
2. NULL pointer dereference
3. Memory leaks
4. Buffer overflows
5. Dangling pointers
6. Double free
7. Returning local variable addresses

---

## 📖 Referensi dan Sumber Pembelajaran

### Referensi Utama
- The C Programming Language (Kernighan & Ritchie)
- Understanding and Using C Pointers (Richard Reese)
- Expert C Programming (Peter van der Linden)

### Online Resources
- GeeksforGeeks - Pointers in C
- Programiz - C Pointers
- TutorialsPoint - C Pointers

### Tools untuk Debugging
- Valgrind - Memory leak detection
- GDB - Debugger untuk pointer issues
- AddressSanitizer - Memory error detector

### Latihan Tambahan
1. Implementasi dynamic stack dan queue
2. Buat memory pool allocator
3. Implementasi binary search tree dengan pointers
4. Buat string library dengan pointer operations
5. Implementasi smart pointer sederhana, size, sizeof(int), ascending);
    printf("   Ascending: ");
    for(int i = 0; i < size; i++) printf("%d ", numbers[i]);
    printf("\n");
    
    qsort(numbers