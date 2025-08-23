# Minggu 11: Array dalam Bahasa C
## Logika dan Pemrograman

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. **Memahami konsep fundamental array** sebagai struktur data linear dalam bahasa C
2. **Menguasai deklarasi dan inisialisasi array** dengan berbagai metode
3. **Mengimplementasikan operasi dasar array** seperti traversal, searching, dan sorting
4. **Memahami array multidimensi** dan aplikasinya dalam pemrograman
5. **Menguasai string sebagai array karakter** dan manipulasinya
6. **Mengintegrasikan array dengan fungsi** untuk passing dan returning arrays
7. **Memahami memory management** dan pointer relationship dengan array
8. **Mengembangkan aplikasi kompleks** menggunakan array sebagai struktur data utama

---

## 📊 Konsep Dasar Array

### Pengertian Array

Array adalah struktur data yang menyimpan koleksi elemen dengan tipe data yang sama dalam lokasi memori yang berurutan (contiguous). Setiap elemen dalam array dapat diakses menggunakan index, yang dimulai dari 0. Array merupakan salah satu struktur data paling fundamental dalam pemrograman C dan digunakan untuk menyimpan dan memanipulasi data dalam jumlah banyak secara efisien.

### Karakteristik Array

1. **Fixed Size**: Ukuran array harus ditentukan saat deklarasi dan tidak dapat diubah
2. **Homogeneous**: Semua elemen harus memiliki tipe data yang sama
3. **Contiguous Memory**: Elemen-elemen disimpan berurutan dalam memori
4. **Zero-Based Indexing**: Index dimulai dari 0 hingga n-1 (n = ukuran array)
5. **Direct Access**: Setiap elemen dapat diakses langsung menggunakan index

### Mengapa Menggunakan Array?

```c
// Tanpa array - tidak praktis untuk data banyak
int nilai1 = 80;
int nilai2 = 75;
int nilai3 = 90;
int nilai4 = 85;
int nilai5 = 88;
// ... dan seterusnya untuk 100 mahasiswa?

// Dengan array - efisien dan scalable
int nilai[100];  // Dapat menyimpan 100 nilai
nilai[0] = 80;
nilai[1] = 75;
nilai[2] = 90;
nilai[3] = 85;
nilai[4] = 88;
```

---

## 🔧 Deklarasi dan Inisialisasi Array

### Sintaks Deklarasi Array

```c
data_type array_name[array_size];
```

### Berbagai Cara Deklarasi dan Inisialisasi

```c
#include <stdio.h>

int main() {
    // 1. Deklarasi tanpa inisialisasi
    int arr1[5];  // Berisi garbage values
    
    // 2. Deklarasi dengan inisialisasi lengkap
    int arr2[5] = {10, 20, 30, 40, 50};
    
    // 3. Inisialisasi parsial (sisa elemen = 0)
    int arr3[5] = {10, 20};  // {10, 20, 0, 0, 0}
    
    // 4. Inisialisasi semua elemen dengan 0
    int arr4[5] = {0};  // {0, 0, 0, 0, 0}
    
    // 5. Ukuran array otomatis dari initializer
    int arr5[] = {1, 2, 3, 4, 5};  // Size = 5
    
    // 6. Designated initializers (C99)
    int arr6[5] = {[0] = 10, [2] = 30, [4] = 50};  // {10, 0, 30, 0, 50}
    
    // 7. Character array (string)
    char str1[] = "Hello";  // {'H', 'e', 'l', 'l', 'o', '\0'}
    char str2[10] = "Hi";   // {'H', 'i', '\0', 0, 0, ...}
    
    // Display arrays
    printf("=== BERBAGAI CARA INISIALISASI ARRAY ===\n");
    
    printf("arr2 (full init): ");
    for(int i = 0; i < 5; i++) printf("%d ", arr2[i]);
    printf("\n");
    
    printf("arr3 (partial): ");
    for(int i = 0; i < 5; i++) printf("%d ", arr3[i]);
    printf("\n");
    
    printf("arr6 (designated): ");
    for(int i = 0; i < 5; i++) printf("%d ", arr6[i]);
    printf("\n");
    
    return 0;
}
```

### Memory Layout Array

```c
#include <stdio.h>

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    
    printf("=== MEMORY LAYOUT ARRAY ===\n");
    printf("Array base address: %p\n", arr);
    printf("\nElement | Value | Address        | Offset\n");
    printf("--------|-------|----------------|--------\n");
    
    for(int i = 0; i < 5; i++) {
        printf("arr[%d]  | %3d   | %p | +%ld bytes\n", 
               i, arr[i], &arr[i], 
               (char*)&arr[i] - (char*)arr);
    }
    
    printf("\nUkuran int: %zu bytes\n", sizeof(int));
    printf("Total ukuran array: %zu bytes\n", sizeof(arr));
    
    return 0;
}
```

---

## 📝 Operasi Dasar Array

### 1. Traversal (Iterasi)

```c
#include <stdio.h>

void displayArray(int arr[], int size) {
    printf("Array elements: ");
    for(int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

void displayArrayReverse(int arr[], int size) {
    printf("Reverse order: ");
    for(int i = size - 1; i >= 0; i--) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

void displayEvenIndices(int arr[], int size) {
    printf("Even indices: ");
    for(int i = 0; i < size; i += 2) {
        printf("arr[%d]=%d ", i, arr[i]);
    }
    printf("\n");
}

int main() {
    int numbers[] = {10, 20, 30, 40, 50, 60, 70, 80, 90, 100};
    int size = sizeof(numbers) / sizeof(numbers[0]);
    
    printf("=== ARRAY TRAVERSAL ===\n");
    displayArray(numbers, size);
    displayArrayReverse(numbers, size);
    displayEvenIndices(numbers, size);
    
    return 0;
}
```

### 2. Searching (Pencarian)

```c
#include <stdio.h>

// Linear Search - O(n)
int linearSearch(int arr[], int size, int key) {
    for(int i = 0; i < size; i++) {
        if(arr[i] == key) {
            return i;  // Return index if found
        }
    }
    return -1;  // Not found
}

// Binary Search - O(log n) - Array must be sorted
int binarySearch(int arr[], int size, int key) {
    int left = 0, right = size - 1;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] == key) {
            return mid;
        }
        
        if(arr[mid] < key) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1;  // Not found
}

// Find all occurrences
void findAllOccurrences(int arr[], int size, int key) {
    printf("Searching for %d: ", key);
    int found = 0;
    
    for(int i = 0; i < size; i++) {
        if(arr[i] == key) {
            printf("index %d ", i);
            found = 1;
        }
    }
    
    if(!found) {
        printf("Not found");
    }
    printf("\n");
}

int main() {
    int unsorted[] = {64, 34, 25, 12, 22, 11, 90, 22, 34};
    int sorted[] = {11, 12, 22, 25, 34, 64, 88, 90, 100};
    int size1 = sizeof(unsorted) / sizeof(unsorted[0]);
    int size2 = sizeof(sorted) / sizeof(sorted[0]);
    
    printf("=== ARRAY SEARCHING ===\n");
    
    // Linear search on unsorted array
    int key = 22;
    int result = linearSearch(unsorted, size1, key);
    if(result != -1) {
        printf("Linear Search: %d found at index %d\n", key, result);
    } else {
        printf("Linear Search: %d not found\n", key);
    }
    
    // Binary search on sorted array
    key = 34;
    result = binarySearch(sorted, size2, key);
    if(result != -1) {
        printf("Binary Search: %d found at index %d\n", key, result);
    } else {
        printf("Binary Search: %d not found\n", key);
    }
    
    // Find all occurrences
    findAllOccurrences(unsorted, size1, 22);
    findAllOccurrences(unsorted, size1, 34);
    
    return 0;
}
```

### 3. Sorting (Pengurutan)

```c
#include <stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

// Bubble Sort - O(n²)
void bubbleSort(int arr[], int n) {
    for(int i = 0; i < n - 1; i++) {
        int swapped = 0;
        for(int j = 0; j < n - i - 1; j++) {
            if(arr[j] > arr[j + 1]) {
                swap(&arr[j], &arr[j + 1]);
                swapped = 1;
            }
        }
        if(!swapped) break;  // Optimized: stop if already sorted
    }
}

// Selection Sort - O(n²)
void selectionSort(int arr[], int n) {
    for(int i = 0; i < n - 1; i++) {
        int min_idx = i;
        for(int j = i + 1; j < n; j++) {
            if(arr[j] < arr[min_idx]) {
                min_idx = j;
            }
        }
        if(min_idx != i) {
            swap(&arr[i], &arr[min_idx]);
        }
    }
}

// Insertion Sort - O(n²)
void insertionSort(int arr[], int n) {
    for(int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        
        while(j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}

void printArray(int arr[], int size) {
    for(int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr1[] = {64, 34, 25, 12, 22, 11, 90};
    int arr2[] = {64, 34, 25, 12, 22, 11, 90};
    int arr3[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr1) / sizeof(arr1[0]);
    
    printf("=== SORTING ALGORITHMS ===\n");
    printf("Original array: ");
    printArray(arr1, n);
    
    // Bubble Sort
    bubbleSort(arr1, n);
    printf("Bubble Sort:    ");
    printArray(arr1, n);
    
    // Selection Sort
    selectionSort(arr2, n);
    printf("Selection Sort: ");
    printArray(arr2, n);
    
    // Insertion Sort
    insertionSort(arr3, n);
    printf("Insertion Sort: ");
    printArray(arr3, n);
    
    return 0;
}
```

### 4. Statistical Operations

```c
#include <stdio.h>
#include <limits.h>

int findMin(int arr[], int size) {
    int min = INT_MAX;
    for(int i = 0; i < size; i++) {
        if(arr[i] < min) {
            min = arr[i];
        }
    }
    return min;
}

int findMax(int arr[], int size) {
    int max = INT_MIN;
    for(int i = 0; i < size; i++) {
        if(arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}

double calculateAverage(int arr[], int size) {
    long sum = 0;
    for(int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return (double)sum / size;
}

int calculateSum(int arr[], int size) {
    int sum = 0;
    for(int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return sum;
}

void findFrequency(int arr[], int size) {
    printf("\n=== FREQUENCY COUNT ===\n");
    
    // Simple approach for small range
    int visited[100] = {0};  // Assuming values < 100
    
    for(int i = 0; i < size; i++) {
        if(visited[i]) continue;
        
        int count = 1;
        for(int j = i + 1; j < size; j++) {
            if(arr[i] == arr[j]) {
                count++;
                visited[j] = 1;
            }
        }
        printf("%d occurs %d time(s)\n", arr[i], count);
    }
}

int main() {
    int data[] = {45, 67, 23, 89, 45, 12, 67, 90, 45, 34};
    int size = sizeof(data) / sizeof(data[0]);
    
    printf("=== STATISTICAL OPERATIONS ===\n");
    printf("Array: ");
    for(int i = 0; i < size; i++) printf("%d ", data[i]);
    printf("\n\n");
    
    printf("Minimum: %d\n", findMin(data, size));
    printf("Maximum: %d\n", findMax(data, size));
    printf("Sum: %d\n", calculateSum(data, size));
    printf("Average: %.2f\n", calculateAverage(data, size));
    
    findFrequency(data, size);
    
    return 0;
}
```

---

## 🔲 Array Multidimensi

### Array 2 Dimensi (Matrix)

```c
#include <stdio.h>

#define ROWS 3
#define COLS 4

void printMatrix(int matrix[][COLS], int rows) {
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < COLS; j++) {
            printf("%3d ", matrix[i][j]);
        }
        printf("\n");
    }
}

void transposeMatrix(int matrix[][COLS], int transposed[][ROWS], int rows, int cols) {
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < cols; j++) {
            transposed[j][i] = matrix[i][j];
        }
    }
}

int main() {
    // Different ways to initialize 2D array
    int matrix1[ROWS][COLS] = {
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12}
    };
    
    int matrix2[ROWS][COLS] = {{1, 2}, {3, 4}};  // Partial initialization
    
    int matrix3[ROWS][COLS] = {0};  // All zeros
    
    printf("=== 2D ARRAY (MATRIX) ===\n");
    printf("Matrix 1:\n");
    printMatrix(matrix1, ROWS);
    
    printf("\nMatrix 2 (partial init):\n");
    printMatrix(matrix2, ROWS);
    
    // Accessing elements
    printf("\nElement at [1][2]: %d\n", matrix1[1][2]);
    
    // Row and column sums
    printf("\nRow sums: ");
    for(int i = 0; i < ROWS; i++) {
        int sum = 0;
        for(int j = 0; j < COLS; j++) {
            sum += matrix1[i][j];
        }
        printf("%d ", sum);
    }
    
    printf("\nColumn sums: ");
    for(int j = 0; j < COLS; j++) {
        int sum = 0;
        for(int i = 0; i < ROWS; i++) {
            sum += matrix1[i][j];
        }
        printf("%d ", sum);
    }
    
    // Transpose
    int transposed[COLS][ROWS];
    transposeMatrix(matrix1, transposed, ROWS, COLS);
    printf("\n\nTransposed Matrix:\n");
    for(int i = 0; i < COLS; i++) {
        for(int j = 0; j < ROWS; j++) {
            printf("%3d ", transposed[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

### Operasi Matrix

```c
#include <stdio.h>

#define SIZE 3

void inputMatrix(int mat[][SIZE], char name) {
    printf("Enter elements for Matrix %c:\n", name);
    for(int i = 0; i < SIZE; i++) {
        for(int j = 0; j < SIZE; j++) {
            printf("%c[%d][%d]: ", name, i, j);
            scanf("%d", &mat[i][j]);
        }
    }
}

void printMatrix(int mat[][SIZE]) {
    for(int i = 0; i < SIZE; i++) {
        for(int j = 0; j < SIZE; j++) {
            printf("%4d ", mat[i][j]);
        }
        printf("\n");
    }
}

void addMatrices(int a[][SIZE], int b[][SIZE], int result[][SIZE]) {
    for(int i = 0; i < SIZE; i++) {
        for(int j = 0; j < SIZE; j++) {
            result[i][j] = a[i][j] + b[i][j];
        }
    }
}

void multiplyMatrices(int a[][SIZE], int b[][SIZE], int result[][SIZE]) {
    for(int i = 0; i < SIZE; i++) {
        for(int j = 0; j < SIZE; j++) {
            result[i][j] = 0;
            for(int k = 0; k < SIZE; k++) {
                result[i][j] += a[i][k] * b[k][j];
            }
        }
    }
}

int calculateDeterminant(int mat[][SIZE]) {
    // For 3x3 matrix
    int det = 0;
    
    for(int i = 0; i < SIZE; i++) {
        int prod1 = 1, prod2 = 1;
        for(int j = 0; j < SIZE; j++) {
            prod1 *= mat[j][(i + j) % SIZE];
            prod2 *= mat[j][(i - j + SIZE) % SIZE];
        }
        det += prod1 - prod2;
    }
    
    return det;
}

int main() {
    int matrixA[SIZE][SIZE] = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    int matrixB[SIZE][SIZE] = {{9, 8, 7}, {6, 5, 4}, {3, 2, 1}};
    int result[SIZE][SIZE];
    
    printf("=== MATRIX OPERATIONS ===\n");
    
    printf("\nMatrix A:\n");
    printMatrix(matrixA);
    
    printf("\nMatrix B:\n");
    printMatrix(matrixB);
    
    // Addition
    addMatrices(matrixA, matrixB, result);
    printf("\nA + B:\n");
    printMatrix(result);
    
    // Multiplication
    multiplyMatrices(matrixA, matrixB, result);
    printf("\nA × B:\n");
    printMatrix(result);
    
    // Determinant
    printf("\nDeterminant of A: %d\n", calculateDeterminant(matrixA));
    
    return 0;
}
```

---

## 📜 String sebagai Array Karakter

### Konsep String dalam C

```c
#include <stdio.h>
#include <string.h>

int main() {
    // Different ways to declare strings
    char str1[] = "Hello";  // Size = 6 (5 chars + '\0')
    char str2[10] = "World";  // Size = 10, but only uses 6
    char str3[] = {'C', 'o', 'd', 'e', '\0'};  // Manual null terminator
    char str4[20];  // Uninitialized
    
    printf("=== STRING AS CHARACTER ARRAY ===\n");
    
    // Display strings and their properties
    printf("str1: %s (length: %zu, size: %zu)\n", 
           str1, strlen(str1), sizeof(str1));
    printf("str2: %s (length: %zu, size: %zu)\n", 
           str2, strlen(str2), sizeof(str2));
    printf("str3: %s (length: %zu, size: %zu)\n", 
           str3, strlen(str3), sizeof(str3));
    
    // Character by character access
    printf("\nCharacter by character (str1):\n");
    for(int i = 0; str1[i] != '\0'; i++) {
        printf("str1[%d] = '%c' (ASCII: %d)\n", i, str1[i], str1[i]);
    }
    
    // String input
    printf("\nEnter a string (max 19 chars): ");
    scanf("%19s", str4);  // Limit input to prevent buffer overflow
    printf("You entered: %s\n", str4);
    
    // String with spaces using fgets
    char sentence[100];
    printf("Enter a sentence: ");
    getchar();  // Clear buffer
    fgets(sentence, sizeof(sentence), stdin);
    sentence[strcspn(sentence, "\n")] = '\0';  // Remove newline
    printf("You entered: %s\n", sentence);
    
    return 0;
}
```

### String Manipulation Functions

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

// Custom string length
int myStrlen(char str[]) {
    int len = 0;
    while(str[len] != '\0') {
        len++;
    }
    return len;
}

// Custom string copy
void myStrcpy(char dest[], char src[]) {
    int i = 0;
    while(src[i] != '\0') {
        dest[i] = src[i];
        i++;
    }
    dest[i] = '\0';
}

// Custom string concatenation
void myStrcat(char dest[], char src[]) {
    int i = 0, j = 0;
    
    // Find end of dest
    while(dest[i] != '\0') {
        i++;
    }
    
    // Copy src to end of dest
    while(src[j] != '\0') {
        dest[i] = src[j];
        i++;
        j++;
    }
    dest[i] = '\0';
}

// Custom string comparison
int myStrcmp(char str1[], char str2[]) {
    int i = 0;
    
    while(str1[i] != '\0' && str2[i] != '\0') {
        if(str1[i] != str2[i]) {
            return str1[i] - str2[i];
        }
        i++;
    }
    
    return str1[i] - str2[i];
}

// Reverse string
void reverseString(char str[]) {
    int len = strlen(str);
    for(int i = 0; i < len / 2; i++) {
        char temp = str[i];
        str[i] = str[len - 1 - i];
        str[len - 1 - i] = temp;
    }
}

// Check palindrome
int isPalindrome(char str[]) {
    int len = strlen(str);
    for(int i = 0; i < len / 2; i++) {
        if(tolower(str[i]) != tolower(str[len - 1 - i])) {
            return 0;
        }
    }
    return 1;
}

// Count words
int countWords(char str[]) {
    int count = 0;
    int inWord = 0;
    
    for(int i = 0; str[i] != '\0'; i++) {
        if(str[i] != ' ' && str[i] != '\t' && str[i] != '\n') {
            if(!inWord) {
                count++;
                inWord = 1;
            }
        } else {
            inWord = 0;
        }
    }
    
    return count;
}

int main() {
    char str1[100] = "Hello";
    char str2[100] = "World";
    char str3[100];
    char palindrome1[] = "racecar";
    char palindrome2[] = "hello";
    char sentence[] = "The quick brown fox jumps";
    
    printf("=== STRING MANIPULATION ===\n");
    
    // Length
    printf("Length of '%s': %d (custom), %zu (strlen)\n", 
           str1, myStrlen(str1), strlen(str1));
    
    // Copy
    myStrcpy(str3, str1);
    printf("After copy: str3 = '%s'\n", str3);
    
    // Concatenation
    myStrcat(str1, " ");
    myStrcat(str1, str2);
    printf("After concatenation: '%s'\n", str1);
    
    // Comparison
    printf("Comparing 'Apple' and 'Banana': %d\n", 
           myStrcmp("Apple", "Banana"));
    printf("Comparing 'Apple' and 'Apple': %d\n", 
           myStrcmp("Apple", "Apple"));
    
    // Reverse
    char toReverse[] = "Programming";
    printf("\nOriginal: %s\n", toReverse);
    reverseString(toReverse);
    printf("Reversed: %s\n", toReverse);
    
    // Palindrome check
    printf("\n'%s' is %sa palindrome\n", 
           palindrome1, isPalindrome(palindrome1) ? "" : "not ");
    printf("'%s' is %sa palindrome\n", 
           palindrome2, isPalindrome(palindrome2) ? "" : "not ");
    
    // Word count
    printf("\nWords in '%s': %d\n", sentence, countWords(sentence));
    
    return 0;
}
```

---

## 🔗 Array dan Pointer

### Relationship Between Arrays and Pointers

```c
#include <stdio.h>

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int *ptr = arr;  // Array name is a pointer to first element
    
    printf("=== ARRAY AND POINTER RELATIONSHIP ===\n");
    
    // Different ways to access array elements
    printf("\nAccessing array elements:\n");
    for(int i = 0; i < 5; i++) {
        printf("Method 1 - arr[%d]: %d\n", i, arr[i]);
        printf("Method 2 - *(arr + %d): %d\n", i, *(arr + i));
        printf("Method 3 - ptr[%d]: %d\n", i, ptr[i]);
        printf("Method 4 - *(ptr + %d): %d\n", i, *(ptr + i));
        printf("---\n");
    }
    
    // Address arithmetic
    printf("\nAddress arithmetic:\n");
    printf("arr base address: %p\n", (void*)arr);
    printf("ptr points to: %p\n", (void*)ptr);
    
    for(int i = 0; i < 5; i++) {
        printf("&arr[%d] = %p, arr + %d = %p\n", 
               i, (void*)&arr[i], i, (void*)(arr + i));
    }
    
    // Pointer arithmetic
    printf("\nPointer arithmetic:\n");
    ptr = arr;  // Reset to beginning
    printf("*ptr = %d\n", *ptr);
    ptr++;
    printf("After ptr++, *ptr = %d\n", *ptr);
    ptr += 2;
    printf("After ptr += 2, *ptr = %d\n", *ptr);
    
    // Difference between array and pointer
    printf("\nSize comparison:\n");
    printf("sizeof(arr) = %zu bytes (entire array)\n", sizeof(arr));
    printf("sizeof(ptr) = %zu bytes (pointer size)\n", sizeof(ptr));
    
    return 0;
}
```

### Passing Arrays to Functions

```c
#include <stdio.h>

// Method 1: Array notation
void printArray1(int arr[], int size) {
    printf("Method 1 (array notation): ");
    for(int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

// Method 2: Pointer notation
void printArray2(int *arr, int size) {
    printf("Method 2 (pointer notation): ");
    for(int i = 0; i < size; i++) {
        printf("%d ", *(arr + i));
    }
    printf("\n");
}

// Method 3: Fixed size array (C99)
void printArray3(int size, int arr[size]) {
    printf("Method 3 (VLA parameter): ");
    for(int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

// Modifying array elements
void doubleElements(int arr[], int size) {
    for(int i = 0; i < size; i++) {
        arr[i] *= 2;
    }
}

// Return array from function (using static)
int* getStaticArray() {
    static int arr[5] = {1, 2, 3, 4, 5};
    return arr;
}

// Dynamic array allocation
int* createDynamicArray(int size) {
    int *arr = (int*)malloc(size * sizeof(int));
    if(arr != NULL) {
        for(int i = 0; i < size; i++) {
            arr[i] = i + 1;
        }
    }
    return arr;
}

int main() {
    int numbers[] = {10, 20, 30, 40, 50};
    int size = sizeof(numbers) / sizeof(numbers[0]);
    
    printf("=== PASSING ARRAYS TO FUNCTIONS ===\n");
    
    printf("Original array: ");
    for(int i = 0; i < size; i++) printf("%d ", numbers[i]);
    printf("\n\n");
    
    // Different methods to pass array
    printArray1(numbers, size);
    printArray2(numbers, size);
    printArray3(size, numbers);
    
    // Modify array
    printf("\nDoubling elements...\n");
    doubleElements(numbers, size);
    printf("After doubling: ");
    printArray1(numbers, size);
    
    // Get array from function
    printf("\nStatic array from function: ");
    int *staticArr = getStaticArray();
    for(int i = 0; i < 5; i++) {
        printf("%d ", staticArr[i]);
    }
    printf("\n");
    
    // Dynamic array
    printf("\nDynamic array: ");
    int *dynamicArr = createDynamicArray(7);
    if(dynamicArr != NULL) {
        for(int i = 0; i < 7; i++) {
            printf("%d ", dynamicArr[i]);
        }
        free(dynamicArr);  // Don't forget to free!
    }
    printf("\n");
    
    return 0;
}
```

---

## 💼 Studi Kasus Komprehensif

### Sistem Manajemen Data Mahasiswa

```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAX_STUDENTS 100
#define MAX_NAME 50
#define NUM_SUBJECTS 5

typedef struct {
    int id;
    char name[MAX_NAME];
    int scores[NUM_SUBJECTS];
    float average;
    char grade;
} Student;

// Global array
Student students[MAX_STUDENTS];
int studentCount = 0;
char subjects[NUM_SUBJECTS][20] = {"Mathematics", "Physics", "Chemistry", "English", "Computer"};

// Function prototypes
void displayMenu();
void addStudent();
void displayAllStudents();
void searchStudent();
void updateStudent();
void deleteStudent();
void displayStatistics();
void sortStudentsByAverage();
void saveToFile();
void loadFromFile();
float calculateAverage(int scores[], int count);
char calculateGrade(float average);
int findStudentById(int id);
void displayStudent(Student s);

int main() {
    int choice;
    
    printf("=== STUDENT MANAGEMENT SYSTEM ===\n");
    loadFromFile();  // Load existing data
    
    do {
        displayMenu();
        printf("Enter choice: ");
        scanf("%d", &choice);
        
        switch(choice) {
            case 1: addStudent(); break;
            case 2: displayAllStudents(); break;
            case 3: searchStudent(); break;
            case 4: updateStudent(); break;
            case 5: deleteStudent(); break;
            case 6: displayStatistics(); break;
            case 7: sortStudentsByAverage(); break;
            case 8: saveToFile(); break;
            case 0: 
                saveToFile();
                printf("Data saved. Goodbye!\n");
                break;
            default: printf("Invalid choice!\n");
        }
        
        if(choice != 0) {
            printf("\nPress Enter to continue...");
            getchar(); getchar();
        }
        
    } while(choice != 0);
    
    return 0;
}

void displayMenu() {
    printf("\n========== MENU ==========\n");
    printf("1. Add Student\n");
    printf("2. Display All Students\n");
    printf("3. Search Student\n");
    printf("4. Update Student\n");
    printf("5. Delete Student\n");
    printf("6. Display Statistics\n");
    printf("7. Sort by Average\n");
    printf("8. Save to File\n");
    printf("0. Exit\n");
    printf("========================\n");
}

void addStudent() {
    if(studentCount >= MAX_STUDENTS) {
        printf("Database full!\n");
        return;
    }
    
    Student newStudent;
    newStudent.id = 1000 + studentCount + 1;
    
    printf("\n=== ADD NEW STUDENT ===\n");
    printf("Name: ");
    getchar();  // Clear buffer
    fgets(newStudent.name, MAX_NAME, stdin);
    newStudent.name[strcspn(newStudent.name, "\n")] = '\0';
    
    printf("Enter scores for:\n");
    for(int i = 0; i < NUM_SUBJECTS; i++) {
        do {
            printf("%s (0-100): ", subjects[i]);
            scanf("%d", &newStudent.scores[i]);
            if(newStudent.scores[i] < 0 || newStudent.scores[i] > 100) {
                printf("Invalid score! Must be 0-100.\n");
            }
        } while(newStudent.scores[i] < 0 || newStudent.scores[i] > 100);
    }
    
    newStudent.average = calculateAverage(newStudent.scores, NUM_SUBJECTS);
    newStudent.grade = calculateGrade(newStudent.average);
    
    students[studentCount++] = newStudent;
    printf("\nStudent added successfully! ID: %d\n", newStudent.id);
}

void displayAllStudents() {
    if(studentCount == 0) {
        printf("\nNo students in database!\n");
        return;
    }
    
    printf("\n=== ALL STUDENTS ===\n");
    printf("%-5s %-20s ", "ID", "Name");
    for(int i = 0; i < NUM_SUBJECTS; i++) {
        printf("%-10s ", subjects[i]);
    }
    printf("%-8s %-5s\n", "Average", "Grade");
    
    printf("------------------------------------------------------------");
    printf("------------------------------------------------------------\n");
    
    for(int i = 0; i < studentCount; i++) {
        displayStudent(students[i]);
    }
    
    printf("\nTotal Students: %d\n", studentCount);
}

void searchStudent() {
    int id;
    printf("\nEnter Student ID to search: ");
    scanf("%d", &id);
    
    int index = findStudentById(id);
    if(index == -1) {
        printf("Student not found!\n");
        return;
    }
    
    printf("\n=== STUDENT DETAILS ===\n");
    printf("ID: %d\n", students[index].id);
    printf("Name: %s\n", students[index].name);
    printf("\nScores:\n");
    for(int i = 0; i < NUM_SUBJECTS; i++) {
        printf("  %s: %d\n", subjects[i], students[index].scores[i]);
    }
    printf("Average: %.2f\n", students[index].average);
    printf("Grade: %c\n", students[index].grade);
}

void updateStudent() {
    int id;
    printf("\nEnter Student ID to update: ");
    scanf("%d", &id);
    
    int index = findStudentById(id);
    if(index == -1) {
        printf("Student not found!\n");
        return;
    }
    
    printf("Current Name: %s\n", students[index].name);
    printf("Enter new name (or press Enter to keep current): ");
    getchar();
    char newName[MAX_NAME];
    fgets(newName, MAX_NAME, stdin);
    if(newName[0] != '\n') {
        newName[strcspn(newName, "\n")] = '\0';
        strcpy(students[index].name, newName);
    }
    
    printf("Update scores? (y/n): ");
    char choice;
    scanf(" %c", &choice);
    
    if(choice == 'y' || choice == 'Y') {
        for(int i = 0; i < NUM_SUBJECTS; i++) {
            printf("%s (current: %d): ", subjects[i], students[index].scores[i]);
            scanf("%d", &students[index].scores[i]);
        }
        
        students[index].average = calculateAverage(students[index].scores, NUM_SUBJECTS);
        students[index].grade = calculateGrade(students[index].average);
    }
    
    printf("Student updated successfully!\n");
}

void deleteStudent() {
    int id;
    printf("\nEnter Student ID to delete: ");
    scanf("%d", &id);
    
    int index = findStudentById(id);
    if(index == -1) {
        printf("Student not found!\n");
        return;
    }
    
    // Shift elements
    for(int i = index; i < studentCount - 1; i++) {
        students[i] = students[i + 1];
    }
    studentCount--;
    
    printf("Student deleted successfully!\n");
}

void displayStatistics() {
    if(studentCount == 0) {
        printf("\nNo students in database!\n");
        return;
    }
    
    printf("\n=== STATISTICS ===\n");
    
    // Overall statistics
    float totalAvg = 0;
    float maxAvg = 0, minAvg = 100;
    int maxIndex = 0, minIndex = 0;
    
    for(int i = 0; i < studentCount; i++) {
        totalAvg += students[i].average;
        if(students[i].average > maxAvg) {
            maxAvg = students[i].average;
            maxIndex = i;
        }
        if(students[i].average < minAvg) {
            minAvg = students[i].average;
            minIndex = i;
        }
    }
    
    printf("Total Students: %d\n", studentCount);
    printf("Class Average: %.2f\n", totalAvg / studentCount);
    printf("Highest Average: %.2f (%s)\n", maxAvg, students[maxIndex].name);
    printf("Lowest Average: %.2f (%s)\n", minAvg, students[minIndex].name);
    
    // Grade distribution
    int gradeCount[5] = {0};  // A, B, C, D, F
    for(int i = 0; i < studentCount; i++) {
        switch(students[i].grade) {
            case 'A': gradeCount[0]++; break;
            case 'B': gradeCount[1]++; break;
            case 'C': gradeCount[2]++; break;
            case 'D': gradeCount[3]++; break;
            case 'F': gradeCount[4]++; break;
        }
    }
    
    printf("\nGrade Distribution:\n");
    char grades[] = {'A', 'B', 'C', 'D', 'F'};
    for(int i = 0; i < 5; i++) {
        printf("Grade %c: %d students (%.1f%%)\n", 
               grades[i], gradeCount[i], 
               (gradeCount[i] * 100.0) / studentCount);
    }
    
    // Subject statistics
    printf("\nSubject Averages:\n");
    for(int j = 0; j < NUM_SUBJECTS; j++) {
        float subjectTotal = 0;
        for(int i = 0; i < studentCount; i++) {
            subjectTotal += students[i].scores[j];
        }
        printf("%s: %.2f\n", subjects[j], subjectTotal / studentCount);
    }
}

void sortStudentsByAverage() {
    // Bubble sort by average (descending)
    for(int i = 0; i < studentCount - 1; i++) {
        for(int j = 0; j < studentCount - i - 1; j++) {
            if(students[j].average < students[j + 1].average) {
                Student temp = students[j];
                students[j] = students[j + 1];
                students[j + 1] = temp;
            }
        }
    }
    
    printf("\nStudents sorted by average (descending)!\n");
    displayAllStudents();
}

void saveToFile() {
    FILE *file = fopen("students.dat", "wb");
    if(file == NULL) {
        printf("Error opening file!\n");
        return;
    }
    
    fwrite(&studentCount, sizeof(int), 1, file);
    fwrite(students, sizeof(Student), studentCount, file);
    fclose(file);
    
    printf("Data saved to file!\n");
}

void loadFromFile() {
    FILE *file = fopen("students.dat", "rb");
    if(file == NULL) {
        printf("No existing data file found.\n");
        return;
    }
    
    fread(&studentCount, sizeof(int), 1, file);
    fread(students, sizeof(Student), studentCount, file);
    fclose(file);
    
    printf("Loaded %d students from file.\n", studentCount);
}

float calculateAverage(int scores[], int count) {
    int sum = 0;
    for(int i = 0; i < count; i++) {
        sum += scores[i];
    }
    return (float)sum / count;
}

char calculateGrade(float average) {
    if(average >= 85) return 'A';
    if(average >= 70) return 'B';
    if(average >= 55) return 'C';
    if(average >= 40) return 'D';
    return 'F';
}

int findStudentById(int id) {
    for(int i = 0; i < studentCount; i++) {
        if(students[i].id == id) {
            return i;
        }
    }
    return -1;
}

void displayStudent(Student s) {
    printf("%-5d %-20s ", s.id, s.name);
    for(int i = 0; i < NUM_SUBJECTS; i++) {
        printf("%-10d ", s.scores[i]);
    }
    printf("%-8.2f %-5c\n", s.average, s.grade);
}
```

---

## 🎮 Aplikasi Game: Tic-Tac-Toe

```c
#include <stdio.h>
#include <stdlib.h>

#define SIZE 3

char board[SIZE][SIZE];
char currentPlayer;

void initializeBoard() {
    int count = 1;
    for(int i = 0; i < SIZE; i++) {
        for(int j = 0; j < SIZE; j++) {
            board[i][j] = '0' + count++;
        }
    }
}

void displayBoard() {
    printf("\n");
    for(int i = 0; i < SIZE; i++) {
        printf(" ");
        for(int j = 0; j < SIZE; j++) {
            printf(" %c ", board[i][j]);
            if(j < SIZE - 1) printf("|");
        }
        printf("\n");
        if(i < SIZE - 1) {
            printf(" ---|---|---\n");
        }
    }
    printf("\n");
}

int isValidMove(int position) {
    if(position < 1 || position > 9) return 0;
    
    int row = (position - 1) / SIZE;
    int col = (position - 1) % SIZE;
    
    return (board[row][col] != 'X' && board[row][col] != 'O');
}

void makeMove(int position) {
    int row = (position - 1) / SIZE;
    int col = (position - 1) % SIZE;
    board[row][col] = currentPlayer;
}

int checkWin() {
    // Check rows
    for(int i = 0; i < SIZE; i++) {
        if(board[i][0] == board[i][1] && 
           board[i][1] == board[i][2]) {
            return 1;
        }
    }
    
    // Check columns
    for(int j = 0; j < SIZE; j++) {
        if(board[0][j] == board[1][j] && 
           board[1][j] == board[2][j]) {
            return 1;
        }
    }
    
    // Check diagonals
    if(board[0][0] == board[1][1] && 
       board[1][1] == board[2][2]) {
        return 1;
    }
    
    if(board[0][2] == board[1][1] && 
       board[1][1] == board[2][0]) {
        return 1;
    }
    
    return 0;
}

int isBoardFull() {
    for(int i = 0; i < SIZE; i++) {
        for(int j = 0; j < SIZE; j++) {
            if(board[i][j] != 'X' && board[i][j] != 'O') {
                return 0;
            }
        }
    }
    return 1;
}

void switchPlayer() {
    currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
}

int main() {
    int position;
    int gameOver = 0;
    
    printf("=== TIC-TAC-TOE GAME ===\n");
    printf("Player 1: X\n");
    printf("Player 2: O\n");
    
    initializeBoard();
    currentPlayer = 'X';
    
    while(!gameOver) {
        displayBoard();
        
        printf("Player %c's turn\n", currentPlayer);
        printf("Enter position (1-9): ");
        scanf("%d", &position);
        
        if(!isValidMove(position)) {
            printf("Invalid move! Try again.\n");
            continue;
        }
        
        makeMove(position);
        
        if(checkWin()) {
            displayBoard();
            printf("🎉 Player %c wins! 🎉\n", currentPlayer);
            gameOver = 1;
        } else if(isBoardFull()) {
            displayBoard();
            printf("It's a draw!\n");
            gameOver = 1;
        } else {
            switchPlayer();
        }
    }
    
    return 0;
}
```

---

## 💡 Best Practices dan Tips

### 1. Array Bounds Checking

```c
// BAIK - Always check array bounds
#define MAX_SIZE 100

int safeArrayAccess(int arr[], int size, int index) {
    if(index < 0 || index >= size) {
        printf("Error: Index out of bounds!\n");
        return -1;  // Error value
    }
    return arr[index];
}
```

### 2. Dynamic Array Allocation

```c
// BAIK - Dynamic allocation with error checking
int* createArray(int size) {
    int *arr = (int*)malloc(size * sizeof(int));
    if(arr == NULL) {
        printf("Memory allocation failed!\n");
        return NULL;
    }
    
    // Initialize array
    for(int i = 0; i < size; i++) {
        arr[i] = 0;
    }
    
    return arr;
}

// Always free allocated memory
void cleanup(int *arr) {
    if(arr != NULL) {
        free(arr);
    }
}
```

### 3. Array as Function Parameter

```c
// BAIK - Pass size explicitly
void processArray(int arr[], int size) {
    // Always use size parameter, not sizeof
    for(int i = 0; i < size; i++) {
        // Process arr[i]
    }
}

// BURUK - Assuming fixed size
void badProcess(int arr[]) {
    // sizeof(arr) gives pointer size, not array size!
    for(int i = 0; i < sizeof(arr); i++) {  // WRONG!
        // ...
    }
}
```

### 4. String Handling Safety

```c
// BAIK - Safe string operations
void safeStringCopy(char dest[], const char src[], int destSize) {
    int i;
    for(i = 0; i < destSize - 1 && src[i] != '\0'; i++) {
        dest[i] = src[i];
    }
    dest[i] = '\0';  // Ensure null termination
}

// Using standard library safely
char buffer[100];
snprintf(buffer, sizeof(buffer), "%s", userInput);  // Safe
// NOT: sprintf(buffer, "%s", userInput);  // Unsafe!
```

### 5. Common Pitfalls to Avoid

```c
// PITFALL 1: Array decay to pointer
int arr[10];
int *ptr = arr;  // OK
// sizeof(arr) = 40 (10 * 4 bytes)
// sizeof(ptr) = 8 (pointer size)

// PITFALL 2: Returning local array
int* badFunction() {
    int localArray[10];  // Stack allocated
    return localArray;   // WRONG! Undefined behavior
}

// PITFALL 3: Buffer overflow
char str[10];
strcpy(str, "This string is too long!");  // Buffer overflow!

// PITFALL 4: Uninitialized array
int arr[10];  // Contains garbage values
// Always initialize before use
```

---

## 🎯 Kesimpulan

### Ringkasan Materi

Dalam minggu ke-11 ini, kita telah mempelajari konsep array dalam bahasa C secara komprehensif:

#### 1. **Fundamental Concepts**
- Definisi dan karakteristik array
- Deklarasi dan inisialisasi berbagai jenis array
- Memory layout dan indexing

#### 2. **Array Operations**
- Traversal dan iterasi
- Searching (linear dan binary)
- Sorting (bubble, selection, insertion)
- Statistical operations

#### 3. **Multidimensional Arrays**
- Array 2D (matrix)
- Operasi matrix
- Aplikasi praktis

#### 4. **Strings**
- String sebagai array karakter
- String manipulation functions
- Custom string operations

#### 5. **Arrays and Pointers**
- Relationship between arrays and pointers
- Pointer arithmetic
- Passing arrays to functions

#### 6. **Practical Applications**
- Student Management System
- Tic-Tac-Toe Game
- Data processing applications

### Key Takeaways

1. **Array adalah struktur data fundamental** untuk menyimpan koleksi data
2. **Zero-based indexing** adalah konvensi dalam C
3. **Bounds checking** penting untuk menghindari buffer overflow
4. **Arrays dan pointers** memiliki hubungan erat dalam C
5. **String handling** memerlukan perhatian khusus untuk safety
6. **Multidimensional arrays** powerful untuk data kompleks
7. **Memory management** crucial untuk array dinamis

### Integrasi dengan Materi Sebelumnya

- **Minggu 10**: Fungsi untuk manipulasi array
- **Minggu 7**: Operator perbandingan dalam searching/sorting
- **Minggu 5-6**: Loops untuk array traversal
- **Minggu 4**: Tipe data untuk elemen array

### Persiapan untuk Materi Selanjutnya

Array mempersiapkan untuk:
- **Pointer dan Dynamic Memory**: Advanced array manipulation
- **Structures**: Complex data types dengan arrays
- **File I/O**: Reading/writing arrays to files
- **Data Structures**: Linked lists, stacks, queues

### Evaluasi Pembelajaran

✅ Dapat mendeklarasikan dan menginisialisasi array  
✅ Memahami operasi dasar array (traversal, search, sort)  
✅ Menguasai array multidimensi dan aplikasinya  
✅ Memahami string sebagai array karakter  
✅ Dapat mengintegrasikan array dengan fungsi  
✅ Memahami relationship array dan pointer  
✅ Mampu membuat aplikasi kompleks dengan array

---

## 📖 Referensi dan Sumber Pembelajaran

### Referensi Utama
- The C Programming Language (Kernighan & Ritchie)
- C Programming: A Modern Approach (K.N. King)
- Data Structures Using C (Reema Thareja)

### Online Resources
- GeeksforGeeks - Arrays in C
- Programiz - C Arrays
- TutorialsPoint - C Arrays

### Latihan Tambahan
1. Implementasi algoritma searching dan sorting lanjutan
2. Buat program manajemen inventory dengan array
3. Implementasi game Snake menggunakan 2D array
4. Buat program enkripsi/dekripsi teks
5. Implementasi calculator matrix lengkap