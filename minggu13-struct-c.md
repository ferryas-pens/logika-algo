# Minggu 13: Struktur (Struct) dalam Bahasa C
## Logika dan Pemrograman

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. **Memahami konsep struktur (struct)** sebagai user-defined data type dalam bahasa C
2. **Menguasai deklarasi dan inisialisasi struktur** dengan berbagai metode
3. **Mengimplementasikan nested structures** dan complex data modeling
4. **Memahami struktur dengan array dan pointer** untuk data manipulation
5. **Menguasai passing struktur ke fungsi** baik by value maupun by reference
6. **Mengimplementasikan union dan enum** sebagai alternatif data types
7. **Membuat aplikasi kompleks** menggunakan struktur untuk real-world problems
8. **Memahami memory layout dan alignment** dalam struktur

---

## 📊 Konsep Dasar Struktur

### Pengertian Struktur

Struktur (struct) adalah user-defined data type dalam C yang memungkinkan kita mengelompokkan berbagai tipe data yang berbeda di bawah satu nama. Berbeda dengan array yang hanya dapat menyimpan elemen dengan tipe yang sama, struktur dapat menggabungkan integer, float, char, array, bahkan struktur lain dalam satu unit. Struktur sangat berguna untuk merepresentasikan entitas dunia nyata yang memiliki multiple attributes.

### Mengapa Menggunakan Struktur?

```c
// Tanpa struktur - variabel terpisah sulit dikelola
char nama1[50] = "John Doe";
int umur1 = 25;
float gaji1 = 50000.0;
char nama2[50] = "Jane Smith";
int umur2 = 30;
float gaji2 = 60000.0;
// Bayangkan mengelola 100 karyawan!

// Dengan struktur - data terorganisir
struct Karyawan {
    char nama[50];
    int umur;
    float gaji;
};
struct Karyawan karyawan1 = {"John Doe", 25, 50000.0};
struct Karyawan karyawan2 = {"Jane Smith", 30, 60000.0};
```

### Karakteristik Struktur

1. **Heterogeneous Data**: Dapat menyimpan berbagai tipe data
2. **Grouped Data**: Mengelompokkan data yang berhubungan
3. **User-Defined**: Programmer mendefinisikan struktur sesuai kebutuhan
4. **Memory Efficient**: Data disimpan secara contiguous
5. **Reusable**: Dapat digunakan untuk membuat multiple instances

---

## 🔧 Deklarasi dan Definisi Struktur

### Sintaks Dasar Struktur

```c
struct structure_name {
    data_type member1;
    data_type member2;
    // ... more members
};
```

### Berbagai Cara Deklarasi Struktur

```c
#include <stdio.h>
#include <string.h>

// Method 1: Structure definition
struct Student {
    int id;
    char name[50];
    float gpa;
    int age;
};

// Method 2: Structure definition with variable declaration
struct Point {
    int x;
    int y;
} point1, point2;  // Variables declared with structure

// Method 3: Using typedef
typedef struct {
    char title[100];
    char author[50];
    int year;
    float price;
} Book;

// Method 4: typedef with struct tag
typedef struct Employee {
    int empId;
    char name[50];
    char department[30];
    float salary;
} Employee;

int main() {
    printf("=== STRUKTUR DECLARATION AND INITIALIZATION ===\n");
    
    // Different ways to declare structure variables
    struct Student student1;  // Method 1
    struct Student student2 = {1001, "Alice Johnson", 3.85, 20};  // With initialization
    
    // Using typedef
    Book book1;  // No need for 'struct' keyword
    Book book2 = {"C Programming", "Dennis Ritchie", 1978, 29.99};
    
    // Designated initializers (C99)
    struct Student student3 = {
        .name = "Bob Smith",
        .id = 1002,
        .age = 21,
        .gpa = 3.65
    };
    
    // Partial initialization
    struct Student student4 = {1003, "Charlie Brown"};  // gpa=0.0, age=0
    
    // Display initialized values
    printf("\n1. Full Initialization:\n");
    printf("   ID: %d, Name: %s, GPA: %.2f, Age: %d\n",
           student2.id, student2.name, student2.gpa, student2.age);
    
    printf("\n2. Designated Initializers:\n");
    printf("   ID: %d, Name: %s, GPA: %.2f, Age: %d\n",
           student3.id, student3.name, student3.gpa, student3.age);
    
    printf("\n3. Typedef Structure:\n");
    printf("   Book: %s by %s (%d) - $%.2f\n",
           book2.title, book2.author, book2.year, book2.price);
    
    return 0;
}
```

### Accessing Structure Members

```c
#include <stdio.h>
#include <string.h>

struct Rectangle {
    float length;
    float width;
    float area;
    float perimeter;
};

void calculateRectangleProperties(struct Rectangle *rect) {
    rect->area = rect->length * rect->width;
    rect->perimeter = 2 * (rect->length + rect->width);
}

int main() {
    printf("=== ACCESSING STRUCTURE MEMBERS ===\n");
    
    // Using dot operator (.)
    struct Rectangle rect1;
    rect1.length = 10.5;
    rect1.width = 5.5;
    calculateRectangleProperties(&rect1);
    
    printf("\n1. Using Dot Operator (.):\n");
    printf("   Length: %.2f\n", rect1.length);
    printf("   Width: %.2f\n", rect1.width);
    printf("   Area: %.2f\n", rect1.area);
    printf("   Perimeter: %.2f\n", rect1.perimeter);
    
    // Using pointer and arrow operator (->)
    struct Rectangle *rectPtr = &rect1;
    rectPtr->length = 15.0;  // Modify through pointer
    rectPtr->width = 8.0;
    calculateRectangleProperties(rectPtr);
    
    printf("\n2. Using Arrow Operator (->):\n");
    printf("   Length: %.2f\n", rectPtr->length);
    printf("   Width: %.2f\n", rectPtr->width);
    printf("   Area: %.2f\n", rectPtr->area);
    printf("   Perimeter: %.2f\n", rectPtr->perimeter);
    
    // Alternative: (*pointer).member
    printf("\n3. Using (*pointer).member:\n");
    printf("   Length: %.2f\n", (*rectPtr).length);
    printf("   Width: %.2f\n", (*rectPtr).width);
    
    return 0;
}
```

---

## 🏗️ Nested Structures

### Structure Within Structure

```c
#include <stdio.h>
#include <string.h>

// Structure for Date
struct Date {
    int day;
    int month;
    int year;
};

// Structure for Address
struct Address {
    char street[100];
    char city[50];
    char state[50];
    char zipCode[10];
};

// Structure for Person with nested structures
struct Person {
    char name[50];
    struct Date birthDate;      // Nested structure
    struct Address homeAddress;  // Nested structure
    float height;
    float weight;
};

// Structure with anonymous nested structure
struct Company {
    char name[100];
    struct {  // Anonymous structure
        char street[100];
        char city[50];
        char country[50];
    } headquarters;
    int employeeCount;
    float revenue;
};

void displayPerson(struct Person p) {
    printf("\n=== PERSON DETAILS ===\n");
    printf("Name: %s\n", p.name);
    printf("Birth Date: %02d/%02d/%04d\n", 
           p.birthDate.day, p.birthDate.month, p.birthDate.year);
    printf("Address: %s, %s, %s %s\n",
           p.homeAddress.street, p.homeAddress.city,
           p.homeAddress.state, p.homeAddress.zipCode);
    printf("Height: %.2f cm, Weight: %.2f kg\n", p.height, p.weight);
}

int main() {
    printf("=== NESTED STRUCTURES ===\n");
    
    // Initialize nested structure
    struct Person person1 = {
        "John Doe",
        {15, 6, 1990},  // Birth date
        {"123 Main St", "New York", "NY", "10001"},  // Address
        175.5,
        70.2
    };
    
    // Access nested members
    printf("\n1. Accessing Nested Members:\n");
    printf("   Name: %s\n", person1.name);
    printf("   Birth Year: %d\n", person1.birthDate.year);
    printf("   City: %s\n", person1.homeAddress.city);
    
    // Modify nested members
    person1.birthDate.year = 1991;
    strcpy(person1.homeAddress.city, "Boston");
    
    printf("\n2. After Modification:\n");
    printf("   Birth Year: %d\n", person1.birthDate.year);
    printf("   City: %s\n", person1.homeAddress.city);
    
    // Display complete person details
    displayPerson(person1);
    
    // Anonymous nested structure
    struct Company company = {
        "Tech Corp",
        {"456 Tech Ave", "San Francisco", "USA"},
        5000,
        1000000.0
    };
    
    printf("\n=== COMPANY DETAILS ===\n");
    printf("Company: %s\n", company.name);
    printf("HQ: %s, %s\n", 
           company.headquarters.city, company.headquarters.country);
    printf("Employees: %d\n", company.employeeCount);
    printf("Revenue: $%.2f\n", company.revenue);
    
    return 0;
}
```

---

## 📚 Arrays of Structures

```c
#include <stdio.h>
#include <string.h>

#define MAX_STUDENTS 100

typedef struct {
    int rollNo;
    char name[50];
    float marks[5];  // Array within structure
    float average;
    char grade;
} Student;

// Calculate average and assign grade
void processStudent(Student *s) {
    float sum = 0;
    for(int i = 0; i < 5; i++) {
        sum += s->marks[i];
    }
    s->average = sum / 5.0;
    
    if(s->average >= 90) s->grade = 'A';
    else if(s->average >= 80) s->grade = 'B';
    else if(s->average >= 70) s->grade = 'C';
    else if(s->average >= 60) s->grade = 'D';
    else s->grade = 'F';
}

// Sort students by average (descending)
void sortStudents(Student students[], int count) {
    for(int i = 0; i < count - 1; i++) {
        for(int j = 0; j < count - i - 1; j++) {
            if(students[j].average < students[j + 1].average) {
                Student temp = students[j];
                students[j] = students[j + 1];
                students[j + 1] = temp;
            }
        }
    }
}

// Display student record
void displayStudent(Student s, int rank) {
    printf("%-4d %-6d %-20s ", rank, s.rollNo, s.name);
    for(int i = 0; i < 5; i++) {
        printf("%-6.1f ", s.marks[i]);
    }
    printf("%-7.2f %c\n", s.average, s.grade);
}

int main() {
    printf("=== ARRAY OF STRUCTURES - STUDENT MANAGEMENT ===\n");
    
    Student students[MAX_STUDENTS];
    int studentCount = 0;
    
    // Sample data initialization
    Student sampleStudents[] = {
        {101, "Alice Johnson", {85, 90, 88, 92, 87}, 0, ' '},
        {102, "Bob Smith", {78, 82, 85, 80, 79}, 0, ' '},
        {103, "Charlie Brown", {92, 95, 90, 94, 93}, 0, ' '},
        {104, "Diana Prince", {88, 85, 87, 90, 86}, 0, ' '},
        {105, "Eve Wilson", {75, 78, 72, 77, 74}, 0, ' '}
    };
    
    studentCount = 5;
    
    // Copy sample data and process
    for(int i = 0; i < studentCount; i++) {
        students[i] = sampleStudents[i];
        processStudent(&students[i]);
    }
    
    // Display unsorted records
    printf("\n1. Original Student Records:\n");
    printf("%-4s %-6s %-20s %-36s %-7s %s\n", 
           "Rank", "Roll", "Name", "Marks (5 subjects)", "Average", "Grade");
    printf("--------------------------------------------------------------------------------\n");
    
    for(int i = 0; i < studentCount; i++) {
        displayStudent(students[i], i + 1);
    }
    
    // Sort by average
    sortStudents(students, studentCount);
    
    // Display sorted records
    printf("\n2. Sorted by Average (Descending):\n");
    printf("%-4s %-6s %-20s %-36s %-7s %s\n", 
           "Rank", "Roll", "Name", "Marks (5 subjects)", "Average", "Grade");
    printf("--------------------------------------------------------------------------------\n");
    
    for(int i = 0; i < studentCount; i++) {
        displayStudent(students[i], i + 1);
    }
    
    // Statistics
    printf("\n3. Class Statistics:\n");
    float classAverage = 0;
    int gradeCount[5] = {0};  // A, B, C, D, F
    
    for(int i = 0; i < studentCount; i++) {
        classAverage += students[i].average;
        switch(students[i].grade) {
            case 'A': gradeCount[0]++; break;
            case 'B': gradeCount[1]++; break;
            case 'C': gradeCount[2]++; break;
            case 'D': gradeCount[3]++; break;
            case 'F': gradeCount[4]++; break;
        }
    }
    classAverage /= studentCount;
    
    printf("   Class Average: %.2f\n", classAverage);
    printf("   Top Performer: %s (%.2f)\n", 
           students[0].name, students[0].average);
    printf("   Grade Distribution:\n");
    char grades[] = {'A', 'B', 'C', 'D', 'F'};
    for(int i = 0; i < 5; i++) {
        printf("     Grade %c: %d students\n", grades[i], gradeCount[i]);
    }
    
    return 0;
}
```

---

## 🔄 Structures and Functions

### Passing Structures to Functions

```c
#include <stdio.h>
#include <math.h>

typedef struct {
    float x;
    float y;
} Point;

typedef struct {
    Point center;
    float radius;
} Circle;

// Pass by value
float calculateDistance(Point p1, Point p2) {
    float dx = p2.x - p1.x;
    float dy = p2.y - p1.y;
    return sqrt(dx * dx + dy * dy);
}

// Pass by reference (pointer)
void translatePoint(Point *p, float dx, float dy) {
    p->x += dx;
    p->y += dy;
}

// Return structure
Point midpoint(Point p1, Point p2) {
    Point mid;
    mid.x = (p1.x + p2.x) / 2;
    mid.y = (p1.y + p2.y) / 2;
    return mid;
}

// Structure with nested structure parameter
float circleArea(Circle c) {
    return M_PI * c.radius * c.radius;
}

// Array of structures as parameter
void displayPoints(Point points[], int count) {
    printf("Points:\n");
    for(int i = 0; i < count; i++) {
        printf("  P%d: (%.2f, %.2f)\n", i + 1, points[i].x, points[i].y);
    }
}

// Function returning pointer to structure
Point* createPoint(float x, float y) {
    Point *p = (Point*)malloc(sizeof(Point));
    if(p != NULL) {
        p->x = x;
        p->y = y;
    }
    return p;
}

int main() {
    printf("=== STRUCTURES AND FUNCTIONS ===\n");
    
    // Create points
    Point p1 = {0, 0};
    Point p2 = {3, 4};
    Point p3 = {6, 8};
    
    // 1. Pass by value
    printf("\n1. Pass by Value:\n");
    float dist = calculateDistance(p1, p2);
    printf("   Distance between (%.1f,%.1f) and (%.1f,%.1f): %.2f\n",
           p1.x, p1.y, p2.x, p2.y, dist);
    
    // 2. Pass by reference
    printf("\n2. Pass by Reference:\n");
    printf("   Before translation: P2 = (%.1f, %.1f)\n", p2.x, p2.y);
    translatePoint(&p2, 2, 3);
    printf("   After translation: P2 = (%.1f, %.1f)\n", p2.x, p2.y);
    
    // 3. Return structure
    printf("\n3. Return Structure:\n");
    Point mid = midpoint(p1, p3);
    printf("   Midpoint of (%.1f,%.1f) and (%.1f,%.1f): (%.1f,%.1f)\n",
           p1.x, p1.y, p3.x, p3.y, mid.x, mid.y);
    
    // 4. Nested structure
    printf("\n4. Nested Structure:\n");
    Circle circle = {{5, 5}, 3};
    printf("   Circle: Center(%.1f,%.1f), Radius=%.1f\n",
           circle.center.x, circle.center.y, circle.radius);
    printf("   Area: %.2f\n", circleArea(circle));
    
    // 5. Array of structures
    printf("\n5. Array of Structures:\n");
    Point polygon[] = {p1, p2, p3, mid};
    displayPoints(polygon, 4);
    
    // 6. Dynamic structure
    printf("\n6. Dynamic Structure:\n");
    Point *dynamicPoint = createPoint(10, 20);
    if(dynamicPoint != NULL) {
        printf("   Dynamic point: (%.1f, %.1f)\n", 
               dynamicPoint->x, dynamicPoint->y);
        free(dynamicPoint);
    }
    
    return 0;
}
```

---

## 🔀 Unions and Enumerations

### Union - Memory Efficient Alternative

```c
#include <stdio.h>
#include <string.h>

// Union definition
union Data {
    int intValue;
    float floatValue;
    char stringValue[20];
};

// Structure vs Union comparison
struct StructExample {
    int a;
    float b;
    char c[20];
};

union UnionExample {
    int a;
    float b;
    char c[20];
};

// Tagged union for type safety
typedef enum {
    TYPE_INT,
    TYPE_FLOAT,
    TYPE_STRING
} DataType;

typedef struct {
    DataType type;
    union {
        int intVal;
        float floatVal;
        char strVal[50];
    } data;
} TaggedUnion;

void printTaggedUnion(TaggedUnion *tu) {
    switch(tu->type) {
        case TYPE_INT:
            printf("Integer: %d\n", tu->data.intVal);
            break;
        case TYPE_FLOAT:
            printf("Float: %.2f\n", tu->data.floatVal);
            break;
        case TYPE_STRING:
            printf("String: %s\n", tu->data.strVal);
            break;
    }
}

int main() {
    printf("=== UNIONS ===\n");
    
    // Basic union usage
    union Data data;
    
    printf("\n1. Union Memory Sharing:\n");
    data.intValue = 42;
    printf("   After setting intValue = 42:\n");
    printf("     intValue: %d\n", data.intValue);
    
    data.floatValue = 3.14;
    printf("   After setting floatValue = 3.14:\n");
    printf("     floatValue: %.2f\n", data.floatValue);
    printf("     intValue (corrupted): %d\n", data.intValue);
    
    strcpy(data.stringValue, "Hello");
    printf("   After setting stringValue = \"Hello\":\n");
    printf("     stringValue: %s\n", data.stringValue);
    
    // Size comparison
    printf("\n2. Size Comparison:\n");
    printf("   sizeof(StructExample): %zu bytes\n", sizeof(struct StructExample));
    printf("   sizeof(UnionExample): %zu bytes\n", sizeof(union UnionExample));
    printf("   Union uses memory of largest member\n");
    
    // Tagged union for type safety
    printf("\n3. Tagged Union (Type-Safe):\n");
    TaggedUnion values[3];
    
    values[0].type = TYPE_INT;
    values[0].data.intVal = 100;
    
    values[1].type = TYPE_FLOAT;
    values[1].data.floatVal = 3.14159;
    
    values[2].type = TYPE_STRING;
    strcpy(values[2].data.strVal, "Tagged Union");
    
    for(int i = 0; i < 3; i++) {
        printf("   ");
        printTaggedUnion(&values[i]);
    }
    
    return 0;
}
```

### Enumeration - Named Constants

```c
#include <stdio.h>

// Basic enumeration
enum Day {
    SUNDAY,    // 0
    MONDAY,    // 1
    TUESDAY,   // 2
    WEDNESDAY, // 3
    THURSDAY,  // 4
    FRIDAY,    // 5
    SATURDAY   // 6
};

// Enumeration with custom values
enum Month {
    JAN = 1,
    FEB,      // 2
    MAR,      // 3
    APR = 10, // 10
    MAY,      // 11
    JUN       // 12
};

// Enumeration for state machine
typedef enum {
    STATE_IDLE,
    STATE_RUNNING,
    STATE_PAUSED,
    STATE_STOPPED,
    STATE_ERROR
} SystemState;

// Enumeration with bit flags
enum FilePermission {
    PERM_READ = 1,    // 001
    PERM_WRITE = 2,   // 010
    PERM_EXECUTE = 4  // 100
};

const char* getDayName(enum Day day) {
    switch(day) {
        case SUNDAY: return "Sunday";
        case MONDAY: return "Monday";
        case TUESDAY: return "Tuesday";
        case WEDNESDAY: return "Wednesday";
        case THURSDAY: return "Thursday";
        case FRIDAY: return "Friday";
        case SATURDAY: return "Saturday";
        default: return "Invalid";
    }
}

void printSystemState(SystemState state) {
    printf("System is ");
    switch(state) {
        case STATE_IDLE: printf("IDLE\n"); break;
        case STATE_RUNNING: printf("RUNNING\n"); break;
        case STATE_PAUSED: printf("PAUSED\n"); break;
        case STATE_STOPPED: printf("STOPPED\n"); break;
        case STATE_ERROR: printf("in ERROR state!\n"); break;
    }
}

int main() {
    printf("=== ENUMERATIONS ===\n");
    
    // Basic enumeration
    printf("\n1. Days of the Week:\n");
    enum Day today = WEDNESDAY;
    printf("   Today is %s (value: %d)\n", getDayName(today), today);
    
    for(enum Day d = SUNDAY; d <= SATURDAY; d++) {
        printf("   Day %d: %s\n", d, getDayName(d));
    }
    
    // Custom values
    printf("\n2. Months with Custom Values:\n");
    printf("   JAN = %d\n", JAN);
    printf("   FEB = %d\n", FEB);
    printf("   APR = %d (custom)\n", APR);
    printf("   MAY = %d (continues from APR)\n", MAY);
    
    // State machine
    printf("\n3. State Machine:\n");
    SystemState currentState = STATE_IDLE;
    printSystemState(currentState);
    
    currentState = STATE_RUNNING;
    printSystemState(currentState);
    
    currentState = STATE_ERROR;
    printSystemState(currentState);
    
    // Bit flags
    printf("\n4. File Permissions (Bit Flags):\n");
    int permissions = PERM_READ | PERM_WRITE;  // Read and write
    
    printf("   Permissions: ");
    if(permissions & PERM_READ) printf("READ ");
    if(permissions & PERM_WRITE) printf("WRITE ");
    if(permissions & PERM_EXECUTE) printf("EXECUTE");
    printf("\n");
    
    // Add execute permission
    permissions |= PERM_EXECUTE;
    printf("   After adding EXECUTE: ");
    if(permissions & PERM_READ) printf("READ ");
    if(permissions & PERM_WRITE) printf("WRITE ");
    if(permissions & PERM_EXECUTE) printf("EXECUTE");
    printf("\n");
    
    return 0;
}
```

---

## 💾 Dynamic Memory with Structures

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct Node {
    int data;
    struct Node *next;
} Node;

typedef struct {
    char *name;        // Dynamic string
    int *scores;       // Dynamic array
    int scoreCount;
} DynamicStudent;

// Create dynamic student
DynamicStudent* createStudent(const char *name, int numScores) {
    DynamicStudent *student = (DynamicStudent*)malloc(sizeof(DynamicStudent));
    if(student == NULL) return NULL;
    
    // Allocate memory for name
    student->name = (char*)malloc(strlen(name) + 1);
    if(student->name == NULL) {
        free(student);
        return NULL;
    }
    strcpy(student->name, name);
    
    // Allocate memory for scores
    student->scores = (int*)malloc(numScores * sizeof(int));
    if(student->scores == NULL) {
        free(student->name);
        free(student);
        return NULL;
    }
    student->scoreCount = numScores;
    
    // Initialize scores to 0
    for(int i = 0; i < numScores; i++) {
        student->scores[i] = 0;
    }
    
    return student;
}

// Free dynamic student
void freeStudent(DynamicStudent *student) {
    if(student != NULL) {
        free(student->name);
        free(student->scores);
        free(student);
    }
}

// Dynamic array of structures
typedef struct {
    int id;
    char name[50];
    float salary;
} Employee;

typedef struct {
    Employee *employees;
    int count;
    int capacity;
} EmployeeDatabase;

EmployeeDatabase* createDatabase(int initialCapacity) {
    EmployeeDatabase *db = (EmployeeDatabase*)malloc(sizeof(EmployeeDatabase));
    if(db == NULL) return NULL;
    
    db->employees = (Employee*)malloc(initialCapacity * sizeof(Employee));
    if(db->employees == NULL) {
        free(db);
        return NULL;
    }
    
    db->count = 0;
    db->capacity = initialCapacity;
    return db;
}

void addEmployee(EmployeeDatabase *db, int id, const char *name, float salary) {
    if(db->count >= db->capacity) {
        // Resize array
        db->capacity *= 2;
        Employee *temp = (Employee*)realloc(db->employees, 
                                           db->capacity * sizeof(Employee));
        if(temp == NULL) {
            printf("Failed to expand database!\n");
            return;
        }
        db->employees = temp;
        printf("Database expanded to capacity %d\n", db->capacity);
    }
    
    db->employees[db->count].id = id;
    strcpy(db->employees[db->count].name, name);
    db->employees[db->count].salary = salary;
    db->count++;
}

void displayDatabase(EmployeeDatabase *db) {
    printf("\nEmployee Database (Count: %d, Capacity: %d):\n", 
           db->count, db->capacity);
    printf("%-5s %-20s %-10s\n", "ID", "Name", "Salary");
    printf("------------------------------------\n");
    for(int i = 0; i < db->count; i++) {
        printf("%-5d %-20s $%-9.2f\n",
               db->employees[i].id,
               db->employees[i].name,
               db->employees[i].salary);
    }
}

void freeDatabase(EmployeeDatabase *db) {
    if(db != NULL) {
        free(db->employees);