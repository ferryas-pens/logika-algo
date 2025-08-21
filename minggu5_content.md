    bool has_badge = (badge == 'y' || badge == 'Y');
    bool biometric_verified = (biometric == 'y' || biometric == 'Y');
    bool emergency_mode = (emergency == 'y' || emergency == 'Y');
    
    check_access_permission((AccessLevel)level, (SecurityZone)zone, 
                          has_badge, biometric_verified, hour, emergency_mode);
    
    return 0;
}
```

---

## **BAGIAN 3: SWITCH-CASE STATEMENT**

### **3.1 Konsep Switch-Case**

Switch statement memungkinkan kita untuk mengeksekusi satu blok kode di antara banyak alternatif. Switch statement dapat melakukan hal yang sama dengan IF...ELSE IF ladder. Namun, syntax switch statement jauh lebih mudah dibaca dan ditulis.

#### **Kapan Menggunakan Switch vs IF-ELSE:**

**Switch Statement - Ideal untuk:**
- Multiple exact value comparisons
- Menu-driven applications
- Categorical data processing
- State machine implementations
- Character/integer-based decisions

**IF-ELSE - Ideal untuk:**
- Range comparisons
- Complex boolean expressions
- Multiple condition combinations
- Floating-point comparisons

#### **Switch Statement Syntax:**
```c
switch (expression) {
    case constant1:
        // statements
        break;
    case constant2:
        // statements
        break;
    case constant3:
        // statements
        break;
    ...
    default:
        // default statements
        break;
}
```

### **3.2 Basic Switch Implementation**

#### **Menu-Driven Calculator:**
```c
#include <stdio.h>
#include <math.h>

void display_calculator_menu() {
    printf("\n=== ADVANCED CALCULATOR ===\n");
    printf("1. Addition (+)\n");
    printf("2. Subtraction (-)\n");
    printf("3. Multiplication (*)\n");
    printf("4. Division (/)\n");
    printf("5. Power (^)\n");
    printf("6. Square Root\n");
    printf("7. Percentage\n");
    printf("8. Exit\n");
    printf("Enter your choice (1-8): ");
}

void perform_calculation(int choice) {
    double num1, num2, result;
    
    switch (choice) {
        case 1:  // Addition
            printf("Enter two numbers: ");
            scanf("%lf %lf", &num1, &num2);
            result = num1 + num2;
            printf("%.2f + %.2f = %.2f\n", num1, num2, result);
            break;
            
        case 2:  // Subtraction
            printf("Enter two numbers: ");
            scanf("%lf %lf", &num1, &num2);
            result = num1 - num2;
            printf("%.2f - %.2f = %.2f\n", num1, num2, result);
            break;
            
        case 3:  // Multiplication
            printf("Enter two numbers: ");
            scanf("%lf %lf", &num1, &num2);
            result = num1 * num2;
            printf("%.2f * %.2f = %.2f\n", num1, num2, result);
            break;
            
        case 4:  // Division
            printf("Enter two numbers: ");
            scanf("%lf %lf", &num1, &num2);
            if (num2 != 0) {
                result = num1 / num2;
                printf("%.2f / %.2f = %.2f\n", num1, num2, result);
            } else {
                printf("Error: Division by zero is not allowed!\n");
            }
            break;
            
        case 5:  // Power
            printf("Enter base and exponent: ");
            scanf("%lf %lf", &num1, &num2);
            result = pow(num1, num2);
            printf("%.2f ^ %.2f = %.2f\n", num1, num2, result);
            break;
            
        case 6:  // Square Root
            printf("Enter a number: ");
            scanf("%lf", &num1);
            if (num1 >= 0) {
                result = sqrt(num1);
                printf("√%.2f = %.2f\n", num1, result);
            } else {
                printf("Error: Cannot calculate square root of negative number!\n");
            }
            break;
            
        case 7:  // Percentage
            printf("Enter number and percentage: ");
            scanf("%lf %lf", &num1, &num2);
            result = (num1 * num2) / 100;
            printf("%.2f%% of %.2f = %.2f\n", num2, num1, result);
            break;
            
        case 8:  // Exit
            printf("Thank you for using the calculator!\n");
            break;
            
        default:
            printf("Invalid choice! Please select 1-8.\n");
            break;
    }
}

int main() {
    int choice;
    
    do {
        display_calculator_menu();
        scanf("%d", &choice);
        perform_calculation(choice);
        
        if (choice != 8) {
            printf("\nPress Enter to continue...");
            getchar(); // Clear buffer
            getchar(); // Wait for Enter
        }
        
    } while (choice != 8);
    
    return 0;
}
```

### **3.3 Advanced Switch Applications**

#### **Student Management System:**
```c
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

typedef struct {
    int id;
    char name[50];
    float gpa;
    char major[30];
    int year;
    bool is_active;
} Student;

Student students[100];
int student_count = 0;

void add_student() {
    if (student_count >= 100) {
        printf("Error: Maximum student capacity reached!\n");
        return;
    }
    
    Student new_student;
    printf("\n=== ADD NEW STUDENT ===\n");
    
    printf("Enter Student ID: ");
    scanf("%d", &new_student.id);
    
    printf("Enter Student Name: ");
    scanf(" %[^\n]", new_student.name);  // Read line with spaces
    
    printf("Enter GPA (0.0-4.0): ");
    scanf("%f", &new_student.gpa);
    
    printf("Enter Major: ");
    scanf(" %[^\n]", new_student.major);
    
    printf("Enter Year (1-4): ");
    scanf("%d", &new_student.year);
    
    new_student.is_active = true;
    
    students[student_count] = new_student;
    student_count++;
    
    printf("✓ Student added successfully!\n");
}

void display_all_students() {
    if (student_count == 0) {
        printf("No students found in the system.\n");
        return;
    }
    
    printf("\n=== ALL STUDENTS ===\n");
    printf("%-5s %-20s %-8s %-15s %-6s %-8s\n", 
           "ID", "Name", "GPA", "Major", "Year", "Status");
    printf("─────────────────────────────────────────────────────────────\n");
    
    for (int i = 0; i < student_count; i++) {
        printf("%-5d %-20s %-8.2f %-15s %-6d %-8s\n",
               students[i].id,
               students[i].name,
               students[i].gpa,
               students[i].major,
               students[i].year,
               students[i].is_active ? "Active" : "Inactive");
    }
}

void search_student() {
    int search_id;
    printf("Enter Student ID to search: ");
    scanf("%d", &search_id);
    
    for (int i = 0; i < student_count; i++) {
        if (students[i].id == search_id) {
            printf("\n=== STUDENT FOUND ===\n");
            printf("ID: %d\n", students[i].id);
            printf("Name: %s\n", students[i].name);
            printf("GPA: %.2f\n", students[i].gpa);
            printf("Major: %s\n", students[i].major);
            printf("Year: %d\n", students[i].year);
            printf("Status: %s\n", students[i].is_active ? "Active" : "Inactive");
            return;
        }
    }
    
    printf("Student with ID %d not found.\n", search_id);
}

void calculate_statistics() {
    if (student_count == 0) {
        printf("No students available for statistics.\n");
        return;
    }
    
    float total_gpa = 0;
    float highest_gpa = 0;
    float lowest_gpa = 4.0;
    int active_count = 0;
    
    for (int i = 0; i < student_count; i++) {
        total_gpa += students[i].gpa;
        
        if (students[i].gpa > highest_gpa) {
            highest_gpa = students[i].gpa;
        }
        
        if (students[i].gpa < lowest_gpa) {
            lowest_gpa = students[i].gpa;
        }
        
        if (students[i].is_active) {
            active_count++;
        }
    }
    
    printf("\n=== STUDENT STATISTICS ===\n");
    printf("Total Students: %d\n", student_count);
    printf("Active Students: %d\n", active_count);
    printf("Inactive Students: %d\n", student_count - active_count);
    printf("Average GPA: %.2f\n", total_gpa / student_count);
    printf("Highest GPA: %.2f\n", highest_gpa);
    printf("Lowest GPA: %.2f\n", lowest_gpa);
}

void grade_distribution() {
    int grade_counts[5] = {0}; // A, B, C, D, F
    
    for (int i = 0; i < student_count; i++) {
        if (students[i].gpa >= 3.5) {
            grade_counts[0]++; // A
        } else if (students[i].gpa >= 3.0) {
            grade_counts[1]++; // B
        } else if (students[i].gpa >= 2.0) {
            grade_counts[2]++; // C
        } else if (students[i].gpa >= 1.0) {
            grade_counts[3]++; // D
        } else {
            grade_counts[4]++; // F
        }
    }
    
    printf("\n=== GRADE DISTRIBUTION ===\n");
    printf("A (3.5-4.0): %d students (%.1f%%)\n", 
           grade_counts[0], (float)grade_counts[0]/student_count*100);
    printf("B (3.0-3.4): %d students (%.1f%%)\n", 
           grade_counts[1], (float)grade_counts[1]/student_count*100);
    printf("C (2.0-2.9): %d students (%.1f%%)\n", 
           grade_counts[2], (float)grade_counts[2]/student_count*100);
    printf("D (1.0-1.9): %d students (%.1f%%)\n", 
           grade_counts[3], (float)grade_counts[3]/student_count*100);
    printf("F (0.0-0.9): %d students (%.1f%%)\n", 
           grade_counts[4], (float)grade_counts[4]/student_count*100);
}

void main_menu() {
    int choice;
    
    do {
        printf("\n╔══════════════════════════════════════╗\n");
        printf("║        STUDENT MANAGEMENT SYSTEM     ║\n");
        printf("╠══════════════════════════════════════╣\n");
        printf("║ 1. Add New Student                   ║\n");
        printf("║ 2. Display All Students              ║\n");
        printf("║ 3. Search Student by ID              ║\n");
        printf("║ 4. Calculate Statistics              ║\n");
        printf("║ 5. Grade Distribution                ║\n");
        printf("║ 6. Exit                              ║\n");
        printf("╚══════════════════════════════════════╝\n");
        printf("Enter your choice (1-6): ");
        
        scanf("%d", &choice);
        
        switch (choice) {
            case 1:
                add_student();
                break;
                
            case 2:
                display_all_students();
                break;
                
            case 3:
                search_student();
                break;
                
            case 4:
                calculate_statistics();
                break;
                
            case 5:
                grade_distribution();
                break;
                
            case 6:
                printf("\n📚 Thank you for using Student Management System!\n");
                printf("Goodbye! 👋\n");
                break;
                
            default:
                printf("❌ Invalid choice! Please select 1-6.\n");
                break;
        }
        
        if (choice != 6) {
            printf("\n⏎ Press Enter to continue...");
            getchar(); // Clear buffer
            getchar(); // Wait for Enter
        }
        
    } while (choice != 6);
}

int main() {
    // Initialize with sample data
    strcpy(students[0].name, "Alice Johnson");
    students[0].id = 1001;
    students[0].gpa = 3.8;
    strcpy(students[0].major, "Computer Science");
    students[0].year = 3;
    students[0].is_active = true;
    
    strcpy(students[1].name, "Bob Smith");
    students[1].id = 1002;
    students[1].gpa = 3.2;
    strcpy(students[1].major, "Mathematics");
    students[1].year = 2;
    students[1].is_active = true;
    
    student_count = 2;
    
    main_menu();
    return 0;
}
```

### **3.4 Switch with Character Cases**

#### **Text Processing and Analysis:**
```c
#include <stdio.h>
#include <ctype.h>
#include <string.h>

void analyze_character(char c) {
    printf("Character: '%c' (ASCII: %d)\n", c, c);
    
    switch (c) {
        case 'a': case 'e': case 'i': case 'o': case 'u':
        case 'A': case 'E': case 'I': case 'O': case 'U':
            printf("Type: Vowel\n");
            break;
            
        case '0': case '1': case '2': case '3': case '4':
        case '5': case '6': case '7': case '8': case '9':
            printf("Type: Digit\n");
            printf("Numeric value: %d\n", c - '0');
            break;
            
        case '+': case '-': case '*': case '/': case '%':
        case '=': case '<': case '>': case '!':
            printf("Type: Operator/Symbol\n");
            break;
            
        case ' ': case '\t': case '\n': case '\r':
            printf("Type: Whitespace\n");
            break;
            
        case '.': case ',': case ';': case ':':
        case '?': case '!': case '"': case '\'':
            printf("Type: Punctuation\n");
            break;
            
        default:
            if (isalpha(c)) {
                printf("Type: Consonant\n");
                if (islower(c)) {
                    printf("Case: Lowercase\n");
                } else {
                    printf("Case: Uppercase\n");
                }
            } else {
                printf("Type: Special character\n");
            }
            break;
    }
}

void text_statistics(char* text) {
    int vowels = 0, consonants = 0, digits = 0, spaces = 0, others = 0;
    int length = strlen(text);
    
    printf("\n=== TEXT ANALYSIS ===\n");
    printf("Text: \"%s\"\n", text);
    printf("Length: %d characters\n\n", length);
    
    for (int i = 0; i < length; i++) {
        char c = text[i];
        
        switch (c) {
            case 'a': case 'e': case 'i': case 'o': case 'u':
            case 'A': case 'E': case 'I': case 'O': case 'U':
                vowels++;
                break;
                
            case '0': case '1': case '2': case '3': case '4':
            case '5': case '6': case '7': case '8': case '9':
                digits++;
                break;
                
            case ' ': case '\t': case '\n':
                spaces++;
                break;
                
            default:
                if (isalpha(c)) {
                    consonants++;
                } else {
                    others++;
                }
                break;
        }
    }
    
    printf("Character breakdown:\n");
    printf("├── Vowels: %d (%.1f%%)\n", vowels, (float)vowels/length*100);
    printf("├── Consonants: %d (%.1f%%)\n", consonants, (float)consonants/length*100);
    printf("├── Digits: %d (%.1f%%)\n", digits, (float)digits/length*100);
    printf("├── Spaces: %d (%.1f%%)\n", spaces, (float)spaces/length*100);
    printf("└── Others: %d (%.1f%%)\n", others, (float)others/length*100);
}

int main() {
    char input_text[1000];
    char single_char;
    int choice;
    
    printf("=== CHARACTER & TEXT ANALYZER ===\n");
    printf("1. Analyze single character\n");
    printf("2. Analyze text string\n");
    printf("Enter choice (1-2): ");
    scanf("%d", &choice);
    
    switch (choice) {
        case 1:
            printf("Enter a character: ");
            scanf(" %c", &single_char);
            analyze_character(single_char);
            break;
            
        case 2:
            printf("Enter text to analyze: ");
            scanf(" %[^\n]", input_text);
            text_statistics(input_text);
            break;
            
        default:
            printf("Invalid choice!\n");
            break;
    }
    
    return 0;
}
```

---

## **BAGIAN 4: STUDI KASUS: SISTEM PENENTUAN KELULUSAN**

### **4.1 Requirement Analysis**

Mari implementasikan sistem penentuan kelulusan mahasiswa yang komprehensif dengan multiple criteria dan decision logic yang kompleks.

#### **Business Requirements:**
1. **Multiple Assessment Components**: Assignment, Quiz, Midterm, Final Exam
2. **Weighted Grading**: Different weights for each component
3. **Minimum Threshold**: Each component must meet minimum requirements
4. **Attendance Requirement**: Minimum attendance percentage
5. **Grade Calculation**: Letter grade assignment
6. **Academic Standing**: Dean's list, probation, etc.

### **4.2 Complete Implementation**

```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

typedef struct {
    char student_id[20];
    char name[50];
    double assignment_score;    // Max 100, Weight 25%
    double quiz_score;         // Max 100, Weight 15%
    double midterm_score;      // Max 100, Weight 25%
    double final_score;        // Max 100, Weight 35%
    double attendance_percent; // Must be >= 75%
    int late_submissions;      // Penalty factor
    bool academic_misconduct;  // Automatic failure
} StudentRecord;

typedef struct {
    double final_score;
    char letter_grade;
    char* grade_description;
    double gpa_points;
    bool passed;
    char* academic_standing;
    char* comments;
} GradingResult;

// Function prototypes
bool validate_student_data(StudentRecord student);
GradingResult calculate_final_grade(StudentRecord student);
void print_detailed_report(StudentRecord student, GradingResult result);
void print_grade_summary(GradingResult result);

bool validate_student_data(StudentRecord student) {
    printf("\n=== VALIDATING STUDENT DATA ===\n");
    
    // Check score ranges
    if (student.assignment_score < 0 || student.assignment_score > 100) {
        printf("❌ Invalid assignment score: %.1f (must be 0-100)\n", student.assignment_score);
        return false;
    }
    
    if (student.quiz_score < 0 || student.quiz_score > 100) {
        printf("❌ Invalid quiz score: %.1f (must be 0-100)\n", student.quiz_score);
        return false;
    }
    
    if (student.midterm_score < 0 || student.midterm_score > 100) {
        printf("❌ Invalid midterm score: %.1f (must be 0-100)\n", student.midterm_score);
        return false;
    }
    
    if (student.final_score < 0 || student.final_score > 100) {
        printf("❌ Invalid final score: %.1f (must be 0-100)\n", student.final_score);
        return false;
    }
    
    if (student.attendance_percent < 0 || student.attendance_percent > 100) {
        printf("❌ Invalid attendance: %.1f%% (must be 0-100%%)\n", student.attendance_percent);
        return false;
    }
    
    if (student.late_submissions < 0) {
        printf("❌ Invalid late submissions: %d (cannot be negative)\n", student.late_submissions);
        return false;
    }
    
    printf("✅ All data validated successfully\n");
    return true;
}

GradingResult calculate_final_grade(StudentRecord student) {
    GradingResult result = {0};
    
    // Check for automatic failure conditions
    if (student.academic_misconduct) {
        result.final_score = 0.0;
        result.letter_grade = 'F';
        result.grade_description = "F (Academic Misconduct)";
        result.gpa_points = 0.0;
        result.passed = false;
        result.academic_standing = "Academic Probation";
        result.comments = "Failed due to academic misconduct";
        return result;
    }
    
    // Check attendance requirement
    if (student.attendance_percent < 75.0) {
        result.final_score = 0.0;
        result.letter_grade = 'F';
        result.grade_description = "F (Insufficient Attendance)";
        result.gpa_points = 0.0;
        result.passed = false;
        result.academic_standing = "Academic Probation";
        result.comments = "Failed due to insufficient attendance (<75%)";
        return result;
    }
    
    // Check minimum component requirements
    bool meets_minimums = true;
    
    if (student.assignment_score < 40.0) {
        meets_minimums = false;
        printf("⚠️ Assignment score below minimum (40%%): %.1f%%\n", student.assignment_score);
    }
    
    if (student.midterm_score < 40.0) {
        meets_minimums = false;
        printf("⚠️ Midterm score below minimum (40%%): %.1f%%\n", student.midterm_score);
    }
    
    if (student.final_score < 40.0) {
        meets_minimums = false;
        printf("⚠️ Final exam score below minimum (40%%): %.1f%%\n", student.final_score);
    }
    
    if (!meets_minimums) {
        result.final_score = 0.0;
        result.letter_grade = 'F';
        result.grade_description = "F (Component Minimum Not Met)";
        result.gpa_points = 0.0;
        result.passed = false;
        result.academic_standing = "Academic Probation";
        result.comments = "Failed - one or more components below minimum threshold";
        return result;
    }
    
    // Calculate weighted average
    double weighted_score = (student.assignment_score * 0.25) +
                           (student.quiz_score * 0.15) +
                           (student.midterm_score * 0.25) +
                           (student.final_score * 0.35);
    
    // Apply late submission penalty
    double penalty = student.late_submissions * 2.0; // 2 points per late submission
    weighted_score -= penalty;
    
    if (weighted_score < 0) {
        weighted_score = 0;
    }
    
    result.final_score = weighted_score;
    
    // Determine letter grade and other attributes
    if (weighted_score >= 97.0) {
        result.letter_grade = 'A';
        result.grade_description = "A+ (Outstanding)";
        result.gpa_points = 4.0;
        result.passed = true;
        result.academic_standing = "Dean's List";
        result.comments = "Exceptional performance - Dean's List recognition";
    } else if (weighted_score >= 93.0) {
        result.letter_grade = 'A';
        result.grade_description = "A (Excellent)";
        result.gpa_points = 4.0;
        result.passed = true;
        result.academic_standing = "Dean's List";
        result.comments = "Excellent performance - Dean's List recognition";
    } else if (weighted_score >= 90.0) {
        result.letter_grade = 'A';
        result.grade_description = "A- (Very Good)";
        result.gpa_points = 3.7;
        result.passed = true;
        result.academic_standing = "Honor Roll";
        result.comments = "Very good performance - Honor Roll recognition";
    } else if (weighted_score >= 87.0) {
        result.letter_grade = 'B';
        result.grade_description = "B+ (Good)";
        result.gpa_points = 3.3;
        result.passed = true;
        result.academic_standing = "Good Standing";
        result.comments = "Good performance - continue building on strengths";
    } else if (weighted_score >= 83.0) {
        result.letter_grade = 'B';
        result.grade_description = "B (Satisfactory)";
        result.gpa_points = 3.0;
        result.passed = true;
        result.academic_standing = "Good Standing";
        result.comments = "Satisfactory performance - consider additional study";
    } else if (weighted_score >= 80.0) {
        result.letter_grade = 'B';
        result.grade_description = "B- (Below Average)";
        result.gpa_points = 2.7;
        result.passed = true;
        result.academic_standing = "Good Standing";
        result.comments = "Below average - focus on key concepts";
    } else if (weighted_score >= 77.0) {
        result.letter_grade = 'C';
        result.grade_description = "C+ (Marginal)";
        result.gpa_points = 2.3;
        result.passed = true;
        result.academic_standing = "Academic Warning";
        result.comments = "Marginal performance - seek additional help";
    } else if (weighted_score >= 73.0) {
        result.letter_grade = 'C';
        result.grade_description = "C (Poor)";
        result.gpa_points = 2.0;
        result.passed = true;
        result.academic_standing = "Academic Warning";
        result.comments = "Poor performance - tutoring recommended";
    } else if (weighted_score >= 70.0) {
        result.letter_grade = 'C';
        result.grade_description = "C- (Very Poor)";
        result.gpa_points = 1.7;
        result.passed = true;
        result.academic_standing = "Academic Warning";
        result.comments = "Very poor - consider course retake";
    } else if (weighted_score >= 67.0) {
        result.letter_grade = 'D';
        result.grade_description = "D+ (Inadequate)";
        result.gpa_points = 1.3;
        result.passed = false;
        result.academic_standing = "Academic Probation";
        result.comments = "Inadequate - immediate intervention needed";
    } else if (weighted_score >= 65.0) {
        result.letter_grade = 'D';
        result.grade_description = "D (Minimal)";
        result.gpa_points = 1.0;
        result.passed = false;
        result.academic_standing = "Academic Probation";
        result.comments = "Minimal performance - retake strongly recommended";
    } else {
        result.letter_grade = 'F';
        result.grade_description = "F (Failure)";
        result.gpa_points = 0.0;
        result.passed = false;
        result.academic_standing = "Academic Probation";
        result.comments = "Failed - must retake course";
    }
    
    return result;
}

void print_detailed_report(StudentRecord student, GradingResult result) {
    printf("\n");
    printf("╔══════════════════════════════════════════════════════════════╗\n");
    printf("║                     STUDENT GRADE REPORT                     ║\n");
    printf("╠══════════════════════════════════════════════════════════════╣\n");
    printf("║ Student ID: %-20s Name: %-20s ║\n", student.student_id, student.name);
    printf("╠══════════════════════════════════════════════════════════════╣\n");
    printf("║                    COMPONENT SCORES                          ║\n");
    printf("╠══════════════════════════════════════════════════════════════╣\n");
    printf("║ Assignment (25%%):     %6.1f/100                           ║\n", student.assignment_score);
    printf("║ Quiz (15%%):           %6.1f/100                           ║\n", student.quiz_score);
    printf("║ Midterm (25%%):        %6.1f/100                           ║\n", student.midterm_score);
    printf("║ Final Exam (35%%):     %6.1f/100                           ║\n", student.final_score);
    printf("║ Attendance:           %6.1f%%                             ║\n", student.attendance_percent);
    printf("║ Late Submissions:     %6d                                 ║\n", student.late_submissions);
    printf("╠══════════════════════════════════════════════════════════════╣\n");
    printf("║                    FINAL RESULTS                             ║\n");
    printf("╠══════════════════════════════════════════════════════════════╣\n");
    printf("║ Final Score:          %6.2f/100                           ║\n", result.final_score);
    printf("║ Letter Grade:         %6s                                 ║\n", result.grade_description);
    printf("║ GPA Points:           %6.1f                               ║\n", result.gpa_points);
    printf("║ Status:               %s                                    ║\n", result.passed ? "✅ PASSED" : "❌ FAILED");
    printf("║ Academic Standing:    %-30s           ║\n", result.academic_standing);
    printf("╠══════════════════════════════════════════════════════════════╣\n");
    printf("║ Comments: %-50s ║\n", result.comments);
    printf("╚══════════════════════════════════════════════════════════════╝\n");
}

void print_grade_summary(GradingResult result) {
    printf("\n=== QUICK SUMMARY ===\n");
    
    if (result.passed) {
        printf("🎉 CONGRATULATIONS! You have passed the course.\n");
    } else {
        printf("😔 Unfortunately, you did not pass the course.\n");
    }
    
    printf("Final Grade: %s (%.2f points)\n", result.grade_description, result.final_score);
    printf("GPA Impact: %.1f points\n", result.gpa_points);
    printf("Academic Standing: %s\n", result.academic_standing);
}

int main() {
    StudentRecord student;
    int choice;
    
    printf("╔══════════════════════════════════════════════════════════════╗\n");
    printf("║              STUDENT GRADING SYSTEM v2.0                    ║\n");
    printf("║                                                              ║\n");
    printf("║  This system calculates final grades based on:              ║\n");
    printf("║  • Assignments (25%%), Quiz (15%%), Midterm (25%%), Final (35%%) ║\n");
    printf("║  • Minimum 75%% attendance required                          ║\n");
    printf("║  • Each major component must score ≥40%%                     ║\n");
    printf("║  • Late submission penalty: -2 points each                  ║\n");
    printf("╚══════════════════════════════════════════════════════════════╝\n");
    
    printf("\nChoose input method:\n");
    printf("1. Manual data entry\n");
    printf("2. Use sample student data\n");
    printf("Enter choice (1-2): ");
    scanf("%d", &choice);
    
    switch (choice) {
        case 1:
            // Manual input
            printf("\n=== ENTER STUDENT INFORMATION ===\n");
            
            printf("Student ID: ");
            scanf("%s", student.student_id);
            
            printf("Student Name: ");
            scanf(" %[^\n]", student.name);
            
            printf("Assignment Score (0-100): ");
            scanf("%lf", &student.assignment_score);
            
            printf("Quiz Score (0-100): ");
            scanf("%lf", &student.quiz_score);
            
            printf("Midterm Score (0-100): ");
            scanf("%lf", &student.midterm_score);
            
            printf("Final Exam Score (0-100): ");
            scanf("%lf", &student.final_score);
            
            printf("Attendance Percentage (0-100): ");
            scanf("%lf", &student.attendance_percent);
            
            printf("Number of Late Submissions: ");
            scanf("%d", &student.late_submissions);
            
            char misconduct;
            printf("Academic Misconduct (y/n): ");
            scanf(" %c", &misconduct);
            student.academic_misconduct = (misconduct == 'y' || misconduct == 'Y');
            break;
            
        case 2:
            // Sample data
            strcpy(student.student_id, "CS2024001");
            strcpy(student.name, "Alice Johnson");
            student.assignment_score = 85.5;
            student.quiz_score = 78.0;
            student.midterm_score = 82.5;
            student.final_score = 88.0;
            student.attendance_percent = 92.0;
            student.late_submissions = 1;
            student.academic_misconduct = false;
            
            printf("\n✓ Using sample data for demonstration\n");
            break;
            
        default:
            printf("Invalid choice! Using sample data.\n");
            // Use sample data as fallback
            strcpy(student.student_id, "CS2024001");
            strcpy(student.name, "Alice Johnson");
            student.assignment_score = 85.5;
            student.quiz_score = 78.0;
            student.midterm_score = 82.5;
            student.final_score = 88.0;
            student.attendance_percent = 92.0;
            student.late_submissions = 1;
            student.academic_misconduct = false;
            break;
    }
    
    // Validate input data
    if (!validate_student_data(student)) {
        printf("\n❌ Error: Invalid student data. Please check your inputs.\n");
        return 1;
    }
    
    // Calculate grade
    printf("\n⏳ Calculating final grade...\n");
    GradingResult result = calculate_final_grade(student);
    
    // Display results
    print_detailed_report(student, result);
    print_grade_summary(result);
    
    // Additional recommendations based on grade
    printf("\n=== RECOMMENDATIONS ===\n");
    
    if (result.gpa_points >= 3.5) {
        printf("🌟 Excellent work! Consider:\n");
        printf("   • Applying for academic scholarships\n");
        printf("   • Taking advanced or honors courses\n");
        printf("   • Considering research opportunities\n");
    } else if (result.gpa_points >= 3.0) {
        printf("👍 Good performance! Consider:\n");
        printf("   • Maintaining current study habits\n");
        printf("   • Seeking opportunities for improvement\n");
        printf("   • Participating in study groups\n");
    } else if (result.gpa_points >= 2.0) {
        printf("⚠️ Warning: Academic support needed. Consider:\n");
        printf("   • Meeting with academic advisor\n");
        printf("   • Utilizing tutoring services\n");
        printf("   • Attending professor office hours\n");
        printf("   • Reviewing study strategies\n");
    } else {
        printf("🚨 Immediate action required:\n");
        printf("   • Schedule meeting with academic advisor\n");
        printf("   • Consider course withdrawal/retake options\n");
        printf("   • Seek comprehensive academic support\n");
        printf("   • Evaluate course load and study time\n");
    }
    
    return 0;
}
```

---

## **BAGIAN 5: BEST PRACTICES DAN OPTIMIZATION**

### **5.1 Decision Structure Best Practices**

#### **Code Readability dan Maintainability:**

**1. Use Meaningful Condition Names:**
```c
// Bad
if (x > 0 && y < 100 && z == 1) {
    // do something
}

// Good
bool is_positive = (x > 0);
bool within_limit = (y < 100);
bool is_active = (z == 1);

if (is_positive && within_limit && is_active) {
    // do something
}
```

**2. Avoid Deep Nesting:**
```c
// Bad - Deep nesting
if (user_logged_in) {
    if (has_permission) {
        if (resource_available) {
            if (within_time_limit) {
                // perform action
            }
        }
    }
}

// Good - Early returns
if (!user_logged_in) {
    printf("Please log in first\n");
    return;
}

if (!has_permission) {
    printf("Access denied\n");
    return;
}

if (!resource_available) {
    printf("Resource not available\n");
    return;
}

if (!within_time_limit) {
    printf("Request timeout\n");
    return;
}

// perform action
```

**3. Use Switch for Multiple Exact Comparisons:**
```c
// Better suited for switch
switch (day_of_week) {
    case 1: printf("Monday"); break;
    case 2: printf("Tuesday"); break;
    case 3: printf("Wednesday"); break;
    // ... etc
}

// Better suited for if-else
if (temperature > 30) {
    printf("Hot");
} else if (temperature > 20) {
    printf("Warm");
} else {
    printf("Cool");
}
```

### **5.2 Performance Considerations**

#### **Short-Circuit Evaluation Optimization:**
```c
// Efficient: Check simpler conditions first
if (cheap_check() && expensive_function()) {
    // expensive_function() only called if cheap_check() is true
}

// Put most likely false conditions first in AND
if (rarely_true_condition && often_true_condition) {
    // rarely_true_condition checked first
}

// Put most likely true conditions first in OR
if (often_true_condition || rarely_true_condition) {
    // rarely_true_condition only checked if often_true_condition is false
}
```

#### **Switch vs IF-ELSE Performance:**
```c
// Switch is generally faster for many discrete values
switch (menu_choice) {
    case 1: case 2: case 3: case 4: case 5:
    case 6: case 7: case 8: case 9: case 10:
        // Handle menu options
        break;
}

// IF-ELSE better for ranges and complex conditions
if (score >= 90) {
    grade = 'A';
} else if (score >= 80) {
    grade = 'B';
} // etc.
```

---

## **BAGIAN 6: LATIHAN DAN EVALUASI**

### **6.1 Progressive Exercises**

#### **Exercise 1: Basic Decision Making**
```c
// Implement a traffic light system
// Input: light color (R, Y, G)
// Output: appropriate action

void traffic_light_action(char light) {
    // Implement using switch-case
    // Handle invalid inputs
    // Provide clear instructions
}
```

#### **Exercise 2: Multi-Criteria Decision**
```c
// Implement loan approval system
// Criteria: credit score, income, debt ratio, employment length
// Use nested if statements
// Provide detailed feedback for rejections

bool approve_loan(int credit_score, double income, 
                  double debt_ratio, int employment_months) {
    // Your implementation here
}
```

#### **Exercise 3: Complex State Machine**
```c
// Implement ATM transaction system
// States: Insert Card, Enter PIN, Select Transaction, etc.
// Use switch-case for state transitions
// Handle all edge cases and errors

typedef enum {
    STATE_IDLE,
    STATE_CARD_INSERTED,
    STATE_PIN_ENTERED,
    STATE_MENU_DISPLAYED,
    STATE_TRANSACTION_PROCESSING
} ATMState;

void handle_atm_state(ATMState current_state, int user_input) {
    // Your implementation here
}
```

### **6.2 Assessment Rubric**

#### **Evaluation Criteria:**

**1. Correctness (40%)**
- Logical flow accuracy
- Proper condition evaluation
- Complete coverage of all cases
- Correct use of operators

**2. Code Structure (25%)**
- Appropriate use of if/switch statements
- Proper nesting and organization
- Clean, readable code structure
- Effective use of functions

**3. Input Validation (15%)**
- Comprehensive input checking
- Graceful error handling
- User-friendly error messages
- Edge case coverage

**4. Logic Efficiency (10%)**
- Optimal condition ordering
- Appropriate structure selection
- Minimal redundancy
- Performance considerations

**5. Documentation (10%)**
- Clear comments explaining logic
- Function documentation
- Variable purpose explanation
- Decision rationale

---

## **BAGIAN 7: RANGKUMAN DAN NEXT STEPS**

### **7.1 Key Learning Outcomes**

Pada minggu ini, kita telah menguasai:

**1. Decision Making Fundamentals:**
- Boolean logic dan truth tables
- Condition evaluation dan short-circuit logic
- Multi-criteria decision systems

**2. IF Statement Mastery:**
- Simple, nested, dan if-else if structures
- Complex conditional logic
- Real-world application scenarios

**3. Switch-Case Proficiency:**
- Multi-way branching
- Character dan integer case handling
- Menu-driven programming

**4. Advanced Applications:**
- Student grading systems
- Security access control
- Medical diagnosis logic
- Financial decision systems

### **7.2 Real-World Impact**

**Professional Applications:**
- **Business Rules Engine**: Complex decision logic in enterprise software
- **Access Control Systems**: Security dan authorization mechanisms
- **Financial Systems**: Credit approval, risk assessment
- **Medical Software**: Diagnosis assistance, treatment protocols

### **7.3 Assignment untuk Minggu Depan**

**Main Project: Academic Management System**

Implementasikan sistem manajemen akademik dengan fitur:

**Core Features:**
1. **Student enrollment** dengan validation
2. **Grade calculation** dengan multiple criteria
3. **Academic standing** determination
4. **Transcript generation** dengan formatting
5. **Statistical analysis** dan reporting

**Technical Requirements:**
- Comprehensive input validation
- Multi-level decision trees
- Error handling dan recovery
- User-friendly interface
- Complete documentation

### **7.4 Preparation untuk Minggu Depan**

Minggu depan: **"Operasi Perulangan (Looping)"**

**Topics to Cover:**
- **FOR loops**: Counted iterations
- **WHILE loops**: Condition-based repetition  
- **DO-WHILE loops**: Post-test iterations
- **Nested loops**: Complex iteration patterns
- **Loop control**: break, continue statements

**Recommended Preparation:**
1. Review decision-making concepts
2. Practice dengan iterative thinking
3. Understand counter dan accumulator patterns
4. Explore pattern generation problems

---

## **PENUTUP**

Decision making adalah heart of intelligent programming. Kemampuan untuk membuat keputusan berdasarkan kondisi adalah apa yang membedakan program sederhana dari aplikasi yang sophisticated dan useful.

**Key Principles to Remember:**

1. **Think Like a User**: Consider all possible scenarios dan edge cases
2. **Plan Before Coding**: Design your decision logic before implementation
3. **Keep It Simple**: Choose the most appropriate structure for each situation
4. **Validate Everything**: Never trust user input without verification
5. **Provide Feedback**: Always inform users about decisions dan their consequences

**Real-World Impact:**

The decision structures you've learned power:
- Banking systems yang approve atau reject transactions
- Medical devices yang make life-critical decisions  
- Security systems yang protect sensitive data
- E-commerce platforms yang personalize user experiences
- Transportation systems yang optimize routes

Mastery dari decision-making programming akan enable you untuk build intelligent applications yang can adapt, respond, dan make smart choices just like humans do.

Next week, kita akan explore how to make programs repeat actions efficiently dengan looping structures - another fundamental building block dalam creating powerful applications.

**Happy Decision Making!** 🎯💻

---

*Total kata: ~5000 kata*

**Referensi:**
- Programiz C if...else Statement: https://www.programiz.com/c-programming/c-if-else-statement
- Programiz C switch...case Statement: https://www.programiz.com/c-programming/c-switch-case-statement
- Various programming best practices dan real-world implementation guides# MINGGU 5: OPERASI SELEKSI (DECISION/BRANCHING)
## Mata Kuliah: Logika dan Algoritma Pemrograman

---

## **TUJUAN PEMBELAJARAN**

Setelah mengikuti pembelajaran pada minggu ini, mahasiswa diharapkan dapat:

1. **Memahami konsep decision making** dalam programming dan aplikasinya
2. **Menggunakan IF statements** (simple, nested, if-else if) dengan benar
3. **Mengimplementasikan switch-case** untuk multi-way branching
4. **Menerapkan conditional operators** dan short-circuit evaluation
5. **Menyelesaikan studi kasus** penentuan lulus/tidak lulus dengan logika yang tepat

---

## **BAGIAN 1: KONSEP DECISION MAKING DALAM PROGRAMMING**

### **1.1 Fundamental Decision Making**

Decision making dalam programming mirip dengan decision making dalam kehidupan nyata. Dalam programming, kita juga menghadapi situasi dimana kita ingin blok kode tertentu dieksekusi ketika kondisi tertentu terpenuhi.

#### **Mengapa Decision Making Penting:**

**1. Control Flow Management:**
- Mengatur alur eksekusi program berdasarkan kondisi
- Memungkinkan program merespons input yang berbeda
- Membuat program lebih intelligent dan adaptive

**2. Problem Solving Capability:**
- Meniru logical thinking manusia dalam code
- Menangani multiple scenarios dan edge cases
- Implementasi business rules dan policies

**3. Interactive Programming:**
- User input validation dan handling
- Menu-driven applications
- Conditional processing berdasarkan user choices

#### **Jenis-Jenis Decision Structures:**

**1. Simple Decision (IF):**
```c
// Contoh: Validasi umur untuk voting
int age = 18;
if (age >= 18) {
    printf("Eligible to vote\n");
}
// Program continues regardless
```

**2. Binary Decision (IF-ELSE):**
```c
// Contoh: Penentuan genap/ganjil
int number = 7;
if (number % 2 == 0) {
    printf("Even number\n");
} else {
    printf("Odd number\n");
}
```

**3. Multiple Decision (IF-ELSE IF):**
```c
// Contoh: Grade assignment
int score = 85;
if (score >= 90) {
    printf("Grade A\n");
} else if (score >= 80) {
    printf("Grade B\n");
} else if (score >= 70) {
    printf("Grade C\n");
} else if (score >= 60) {
    printf("Grade D\n");
} else {
    printf("Grade F\n");
}
```

**4. Multi-way Decision (SWITCH-CASE):**
```c
// Contoh: Menu selection
char choice = 'B';
switch (choice) {
    case 'A':
        printf("Option A selected\n");
        break;
    case 'B':
        printf("Option B selected\n");
        break;
    case 'C':
        printf("Option C selected\n");
        break;
    default:
        printf("Invalid option\n");
}
```

### **1.2 Boolean Logic Foundation**

Sebelum mempelajari decision structures secara detail, penting untuk memahami boolean logic yang mendasarinya.

#### **Boolean Expressions:**

**1. Relational Expressions:**
```c
int a = 10, b = 5;

// Basic comparisons
bool greater = (a > b);          // true
bool equal = (a == b);           // false
bool not_equal = (a != b);       // true
bool less_equal = (a <= b);      // false

// Real-world example: Age validation
int user_age = 25;
bool is_adult = (user_age >= 18);
bool is_senior = (user_age >= 65);
bool working_age = (user_age >= 18 && user_age < 65);
```

**2. Logical Combinations:**
```c
// Complex conditions using logical operators
int temperature = 25;
bool is_sunny = true;
bool weekend = false;

// Perfect day for outdoor activity
bool perfect_outdoor_day = (temperature > 20) && (temperature < 30) && is_sunny;

// Good day for any activity
bool good_day = perfect_outdoor_day || weekend;

// Not a work day
bool not_work_day = weekend || !is_sunny;
```

**3. Short-Circuit Evaluation:**
```c
int divisor = 0;
int dividend = 10;

// Safe division using short-circuit AND
if (divisor != 0 && dividend / divisor > 5) {
    printf("Result is greater than 5\n");
}
// If divisor is 0, the second condition is NOT evaluated

// Safe access using short-circuit OR
bool has_backup = false;
bool primary_available = false;

if (primary_available || (has_backup && backup_system_ready())) {
    printf("System can operate\n");
}
// backup_system_ready() only called if primary_available is false
```

### **1.3 Truth Tables dan Decision Logic**

Understanding truth tables membantu dalam designing complex decision logic.

#### **Logical AND (&&) Applications:**
```
Condition A | Condition B | A && B | Use Case
------------|-------------|--------|----------------------------------
true        | true        | true   | Both requirements met
true        | false       | false  | Incomplete requirements
false       | true        | false  | Missing primary condition
false       | false       | false  | No conditions met
```

**Practical Example: Bank Loan Approval**
```c
bool loan_approved(int credit_score, double income, double debt_ratio) {
    bool good_credit = (credit_score >= 700);
    bool sufficient_income = (income >= 50000);
    bool manageable_debt = (debt_ratio <= 0.4);
    
    return good_credit && sufficient_income && manageable_debt;
}
```

#### **Logical OR (||) Applications:**
```
Condition A | Condition B | A || B | Use Case
------------|-------------|--------|----------------------------------
true        | true        | true   | Multiple valid options
true        | false       | true   | Primary condition sufficient
false       | true        | true   | Alternative condition met
false       | false       | false  | No valid options
```

**Practical Example: Emergency System Activation**
```c
bool activate_emergency_system(bool fire_detected, bool gas_leak, bool intrusion) {
    return fire_detected || gas_leak || intrusion;
}
```

---

## **BAGIAN 2: IF STATEMENTS**

### **2.1 Simple IF Statement**

IF statement adalah decision structure yang paling sederhana. Digunakan untuk memutuskan apakah statement atau blok statement tertentu akan dieksekusi berdasarkan kondisi tertentu.

#### **Syntax dan Structure:**
```c
if (test_expression) {
    // Block of code executed if test_expression is true
}
// Program continues here regardless of condition
```

#### **Cara Kerja IF Statement:**
IF statement mengevaluasi test expression di dalam tanda kurung (). Jika test expression evaluated to true, statements di dalam body IF dieksekusi. Jika test expression evaluated to false, statements di dalam body IF tidak dieksekusi.

#### **Contoh Implementasi Lengkap:**

**1. Input Validation:**
```c
#include <stdio.h>

int main() {
    int score;
    
    printf("Enter your exam score (0-100): ");
    scanf("%d", &score);
    
    // Validate score range
    if (score < 0) {
        printf("Error: Score cannot be negative!\n");
        score = 0;  // Set to minimum valid value
    }
    
    if (score > 100) {
        printf("Error: Score cannot exceed 100!\n");
        score = 100;  // Set to maximum valid value
    }
    
    // Additional validation: warn about unusual scores
    if (score < 10) {
        printf("Warning: Very low score detected.\n");
    }
    
    if (score == 100) {
        printf("Congratulations on perfect score!\n");
    }
    
    printf("Final validated score: %d\n", score);
    return 0;
}
```

**2. Business Logic Implementation:**
```c
#include <stdio.h>
#include <stdbool.h>

// Function to check if customer qualifies for discount
void check_customer_discount(double purchase_amount, bool is_member, int age) {
    printf("Purchase Analysis:\n");
    printf("Amount: $%.2f\n", purchase_amount);
    
    // Senior citizen discount (age 65+)
    if (age >= 65) {
        printf("✓ Senior citizen discount (10%%) applies\n");
    }
    
    // Large purchase discount
    if (purchase_amount >= 500.0) {
        printf("✓ Large purchase discount (5%%) applies\n");
    }
    
    // Membership bonus
    if (is_member) {
        printf("✓ Member loyalty bonus (2%%) applies\n");
    }
    
    // First-time buyer bonus
    if (purchase_amount > 0 && !is_member) {
        printf("✓ First-time buyer bonus (3%%) applies\n");
    }
    
    // VIP treatment
    if (purchase_amount >= 1000.0 && is_member) {
        printf("✓ VIP customer - free shipping included\n");
    }
}

int main() {
    double amount = 750.0;
    bool member = true;
    int customer_age = 68;
    
    check_customer_discount(amount, member, customer_age);
    return 0;
}
```

### **2.2 IF-ELSE Statement**

IF statement mungkin memiliki blok else opsional. IF...ELSE statement mengeksekusi dua kode berbeda tergantung apakah test expression adalah true atau false.

#### **Enhanced Decision Making:**

**Syntax:**
```c
if (test_expression) {
    // Code executed if condition is true
} else {
    // Code executed if condition is false
}
```

#### **Comprehensive Examples:**

**1. User Authentication System:**
```c
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

bool authenticate_user(char username[], char password[]) {
    // Simple authentication logic
    char valid_username[] = "admin";
    char valid_password[] = "password123";
    
    if (strcmp(username, valid_username) == 0 && strcmp(password, valid_password) == 0) {
        printf("✓ Authentication successful!\n");
        printf("Welcome, %s!\n", username);
        return true;
    } else {
        printf("✗ Authentication failed!\n");
        
        // Provide specific feedback
        if (strcmp(username, valid_username) != 0) {
            printf("Invalid username.\n");
        }
        if (strcmp(password, valid_password) != 0) {
            printf("Invalid password.\n");
        }
        return false;
    }
}

int main() {
    char user[50], pass[50];
    
    printf("=== User Login System ===\n");
    printf("Username: ");
    scanf("%s", user);
    printf("Password: ");
    scanf("%s", pass);
    
    bool login_success = authenticate_user(user, pass);
    
    if (login_success) {
        printf("\nAccess granted to main system.\n");
    } else {
        printf("\nAccess denied. Please try again.\n");
    }
    
    return 0;
}
```

**2. Financial Calculator:**
```c
#include <stdio.h>

void calculate_loan_eligibility(double income, double existing_debt, double requested_amount) {
    double debt_to_income_ratio = (existing_debt / income) * 100;
    double max_affordable = income * 0.28; // 28% rule
    
    printf("\n=== Loan Eligibility Analysis ===\n");
    printf("Annual Income: $%.2f\n", income);
    printf("Existing Debt: $%.2f\n", existing_debt);
    printf("Requested Loan: $%.2f\n", requested_amount);
    printf("Debt-to-Income Ratio: %.1f%%\n", debt_to_income_ratio);
    printf("Maximum Affordable Payment: $%.2f\n", max_affordable);
    
    if (debt_to_income_ratio <= 36.0 && requested_amount <= max_affordable) {
        printf("\n✓ LOAN APPROVED\n");
        printf("You qualify for the requested loan amount.\n");
        
        // Calculate loan terms
        double monthly_payment = requested_amount / 60; // 5-year term
        printf("Estimated monthly payment: $%.2f\n", monthly_payment);
        
        if (debt_to_income_ratio <= 20.0) {
            printf("Bonus: You qualify for reduced interest rate!\n");
        }
    } else {
        printf("\n✗ LOAN DENIED\n");
        
        if (debt_to_income_ratio > 36.0) {
            printf("Reason: Debt-to-income ratio too high (%.1f%% > 36%%)\n", debt_to_income_ratio);
            printf("Suggestion: Pay down existing debt to improve ratio.\n");
        }
        
        if (requested_amount > max_affordable) {
            printf("Reason: Requested amount exceeds affordability limit.\n");
            printf("Maximum you can afford: $%.2f\n", max_affordable);
        }
    }
}

int main() {
    double income, debt, loan_request;
    
    printf("Enter annual income: $");
    scanf("%lf", &income);
    printf("Enter existing monthly debt: $");
    scanf("%lf", &debt);
    printf("Enter requested loan amount: $");
    scanf("%lf", &loan_request);
    
    calculate_loan_eligibility(income, debt * 12, loan_request); // Convert monthly to annual
    
    return 0;
}
```

### **2.3 IF-ELSE IF Ladder**

IF...ELSE statement mengeksekusi dua kode berbeda tergantung apakah test expression adalah true atau false. Terkadang, pilihan harus dibuat dari lebih dari 2 kemungkinan. IF...ELSE ladder memungkinkan Anda untuk memeriksa beberapa test expression dan mengeksekusi statement yang berbeda.

#### **Multi-Condition Decision Making:**

**Syntax:**
```c
if (condition1) {
    // statements
} else if (condition2) {
    // statements
} else if (condition3) {
    // statements
} else {
    // default statements
}
```

#### **Advanced Implementation Examples:**

**1. Comprehensive Grading System:**
```c
#include <stdio.h>
#include <stdbool.h>

typedef struct {
    char letter_grade;
    char* description;
    double gpa_points;
    char* comment;
} GradeInfo;

GradeInfo determine_grade(double score) {
    GradeInfo grade;
    
    if (score >= 97.0) {
        grade.letter_grade = 'A';
        grade.description = "A+ (Exceptional)";
        grade.gpa_points = 4.0;
        grade.comment = "Outstanding performance! Keep up the excellent work.";
    } else if (score >= 93.0) {
        grade.letter_grade = 'A';
        grade.description = "A (Excellent)";
        grade.gpa_points = 4.0;
        grade.comment = "Excellent work! You've mastered the material.";
    } else if (score >= 90.0) {
        grade.letter_grade = 'A';
        grade.description = "A- (Very Good)";
        grade.gpa_points = 3.7;
        grade.comment = "Very good performance with room for minor improvement.";
    } else if (score >= 87.0) {
        grade.letter_grade = 'B';
        grade.description = "B+ (Good)";
        grade.gpa_points = 3.3;
        grade.comment = "Good work! Continue building on your strengths.";
    } else if (score >= 83.0) {
        grade.letter_grade = 'B';
        grade.description = "B (Satisfactory)";
        grade.gpa_points = 3.0;
        grade.comment = "Satisfactory performance. Consider additional study.";
    } else if (score >= 80.0) {
        grade.letter_grade = 'B';
        grade.description = "B- (Below Average)";
        grade.gpa_points = 2.7;
        grade.comment = "Below average. Focus on understanding key concepts.";
    } else if (score >= 77.0) {
        grade.letter_grade = 'C';
        grade.description = "C+ (Marginal)";
        grade.gpa_points = 2.3;
        grade.comment = "Marginal performance. Extra help recommended.";
    } else if (score >= 73.0) {
        grade.letter_grade = 'C';
        grade.description = "C (Poor)";
        grade.gpa_points = 2.0;
        grade.comment = "Poor performance. Seek tutoring assistance.";
    } else if (score >= 70.0) {
        grade.letter_grade = 'C';
        grade.description = "C- (Very Poor)";
        grade.gpa_points = 1.7;
        grade.comment = "Very poor. Consider retaking or additional support.";
    } else if (score >= 67.0) {
        grade.letter_grade = 'D';
        grade.description = "D+ (Inadequate)";
        grade.gpa_points = 1.3;
        grade.comment = "Inadequate performance. Immediate intervention needed.";
    } else if (score >= 65.0) {
        grade.letter_grade = 'D';
        grade.description = "D (Minimal Pass)";
        grade.gpa_points = 1.0;
        grade.comment = "Minimal passing grade. Retake strongly recommended.";
    } else {
        grade.letter_grade = 'F';
        grade.description = "F (Failure)";
        grade.gpa_points = 0.0;
        grade.comment = "Failure. Must retake course.";
    }
    
    return grade;
}

void print_grade_report(double score, GradeInfo grade) {
    printf("\n=== GRADE REPORT ===\n");
    printf("Score: %.1f%%\n", score);
    printf("Grade: %s\n", grade.description);
    printf("GPA Points: %.1f\n", grade.gpa_points);
    printf("Comment: %s\n", grade.comment);
    
    // Additional academic standing information
    if (grade.gpa_points >= 3.5) {
        printf("Academic Standing: Dean's List\n");
    } else if (grade.gpa_points >= 3.0) {
        printf("Academic Standing: Good Standing\n");
    } else if (grade.gpa_points >= 2.0) {
        printf("Academic Standing: Academic Warning\n");
    } else if (grade.gpa_points >= 1.0) {
        printf("Academic Standing: Academic Probation\n");
    } else {
        printf("Academic Standing: Academic Dismissal Risk\n");
    }
}

int main() {
    double student_score;
    
    printf("Enter student score (0-100): ");
    scanf("%lf", &student_score);
    
    // Validate input
    if (student_score < 0 || student_score > 100) {
        printf("Error: Invalid score. Must be between 0 and 100.\n");
        return 1;
    }
    
    GradeInfo result = determine_grade(student_score);
    print_grade_report(student_score, result);
    
    return 0;
}
```

**2. Medical Diagnosis System:**
```c
#include <stdio.h>
#include <stdbool.h>

void diagnose_fever(double temperature, bool has_cough, bool has_headache, 
                   bool has_sore_throat, int days_sick) {
    printf("\n=== MEDICAL ASSESSMENT ===\n");
    printf("Temperature: %.1f°F\n", temperature);
    printf("Days sick: %d\n", days_sick);
    
    // Temperature categorization
    if (temperature >= 104.0) {
        printf("🚨 EMERGENCY: Dangerously high fever!\n");
        printf("Recommendation: Seek immediate medical attention\n");
    } else if (temperature >= 102.0) {
        printf("⚠️  HIGH FEVER: Significant concern\n");
        
        if (days_sick >= 3) {
            printf("Recommendation: See doctor immediately\n");
        } else {
            printf("Recommendation: Monitor closely, see doctor if persists\n");
        }
        
        // Additional symptom analysis for high fever
        if (has_cough && has_sore_throat) {
            printf("Possible condition: Severe respiratory infection\n");
        } else if (has_headache && !has_cough) {
            printf("Possible condition: Flu or viral infection\n");
        }
        
    } else if (temperature >= 100.4) {
        printf("🤒 MODERATE FEVER: Mild concern\n");
        
        if (has_cough && has_sore_throat && has_headache) {
            printf("Possible condition: Common flu\n");
            printf("Recommendation: Rest, fluids, over-counter medication\n");
        } else if (has_cough && has_sore_throat) {
            printf("Possible condition: Common cold or throat infection\n");
            printf("Recommendation: Rest and monitor symptoms\n");
        } else if (has_headache && days_sick <= 1) {
            printf("Possible condition: Early viral infection\n");
            printf("Recommendation: Rest and stay hydrated\n");
        } else {
            printf("Recommendation: Monitor symptoms, rest recommended\n");
        }
        
    } else if (temperature >= 99.0) {
        printf("🌡️ LOW-GRADE FEVER: Minor concern\n");
        printf("Recommendation: Rest and monitor for 24 hours\n");
        
    } else if (temperature >= 97.0) {
        printf("✅ NORMAL TEMPERATURE\n");
        
        if (has_cough || has_sore_throat || has_headache) {
            printf("Note: Symptoms present without fever\n");
            printf("Possible condition: Minor viral infection or allergies\n");
        } else {
            printf("Assessment: No significant symptoms detected\n");
        }
        
    } else {
        printf("🥶 LOW TEMPERATURE: Potential concern\n");
        printf("Recommendation: Monitor and consider medical consultation\n");
    }
    
    // Duration-based recommendations
    if (days_sick >= 7) {
        printf("\n⚠️  Extended illness duration - medical consultation advised\n");
    } else if (days_sick >= 3 && temperature >= 101.0) {
        printf("\n⚠️  Persistent fever - consider medical consultation\n");
    }
}

int main() {
    double temp;
    int days;
    char cough, headache, sore_throat;
    
    printf("=== SYMPTOM CHECKER ===\n");
    printf("Enter temperature (°F): ");
    scanf("%lf", &temp);
    
    printf("Days feeling sick: ");
    scanf("%d", &days);
    
    printf("Do you have a cough? (y/n): ");
    scanf(" %c", &cough);
    
    printf("Do you have a headache? (y/n): ");
    scanf(" %c", &headache);
    
    printf("Do you have a sore throat? (y/n): ");
    scanf(" %c", &sore_throat);
    
    bool has_cough = (cough == 'y' || cough == 'Y');
    bool has_headache = (headache == 'y' || headache == 'Y');
    bool has_sore_throat = (sore_throat == 'y' || sore_throat == 'Y');
    
    diagnose_fever(temp, has_cough, has_headache, has_sore_throat, days);
    
    printf("\n📋 Disclaimer: This is not professional medical advice.\n");
    printf("   Always consult healthcare professionals for medical concerns.\n");
    
    return 0;
}
```

### **2.4 Nested IF Statements**

Nested IF statements memungkinkan kita untuk menempatkan IF statement di dalam IF statement lainnya, menciptakan decision tree yang kompleks.

#### **When to Use Nested IF:**
- Multiple levels of conditions
- Hierarchical decision making
- Complex business rules
- Dependent conditions

#### **Advanced Nested IF Example:**

**Security Access Control System:**
```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

typedef enum {
    LEVEL_GUEST = 1,
    LEVEL_USER = 2,
    LEVEL_ADMIN = 3,
    LEVEL_SUPER_ADMIN = 4
} AccessLevel;

typedef enum {
    ZONE_PUBLIC = 1,
    ZONE_RESTRICTED = 2,
    ZONE_CLASSIFIED = 3,
    ZONE_TOP_SECRET = 4
} SecurityZone;

void check_access_permission(AccessLevel user_level, SecurityZone requested_zone, 
                            bool has_badge, bool biometric_verified, 
                            int time_hour, bool emergency_mode) {
    
    printf("\n=== ACCESS CONTROL SYSTEM ===\n");
    printf("User Level: %d, Requested Zone: %d\n", user_level, requested_zone);
    printf("Time: %02d:00, Emergency Mode: %s\n", time_hour, emergency_mode ? "YES" : "NO");
    
    // Emergency override
    if (emergency_mode) {
        if (user_level >= LEVEL_ADMIN) {
            printf("✅ EMERGENCY ACCESS GRANTED\n");
            printf("Reason: Emergency override for admin-level user\n");
            return;
        } else {
            printf("❌ EMERGENCY ACCESS DENIED\n");
            printf("Reason: Insufficient emergency privileges\n");
            return;
        }
    }
    
    // Normal access control
    if (user_level >= LEVEL_USER) {  // Must be at least user level
        
        if (requested_zone == ZONE_PUBLIC) {
            // Public zone - basic requirements
            if (has_badge) {
                printf("✅ ACCESS GRANTED to Public Zone\n");
            } else {
                printf("❌ ACCESS DENIED - Badge required for all zones\n");
            }
            
        } else if (requested_zone == ZONE_RESTRICTED) {
            // Restricted zone - additional requirements
            if (has_badge) {
                if (time_hour >= 6 && time_hour <= 22) {  // Business hours
                    if (user_level >= LEVEL_USER) {
                        printf("✅ ACCESS GRANTED to Restricted Zone\n");
                    } else {
                        printf("❌ ACCESS DENIED - Insufficient user level\n");
                    }
                } else {
                    printf("❌ ACCESS DENIED - Outside business hours (6-22)\n");
                }
            } else {
                printf("❌ ACCESS DENIED - Badge required\n");
            }
            
        } else if (requested_zone == ZONE_CLASSIFIED) {
            // Classified zone - high security requirements
            if (user_level >= LEVEL_ADMIN) {
                if (has_badge && biometric_verified) {
                    if (time_hour >= 8 && time_hour <= 18) {  // Strict hours
                        printf("✅ ACCESS GRANTED to Classified Zone\n");
                        printf("Note: All activities are logged and monitored\n");
                    } else {
                        printf("❌ ACCESS DENIED - Outside authorized hours (8-18)\n");
                    }
                } else {
                    printf("❌ ACCESS DENIED - Requires badge AND biometric verification\n");
                }
            } else {
                printf("❌ ACCESS DENIED - Admin level required for classified zone\n");
            }
            
        } else if (requested_zone == ZONE_TOP_SECRET) {
            // Top secret zone - maximum security
            if (user_level >= LEVEL_SUPER_ADMIN) {
                if (has_badge && biometric_verified) {
                    if (time_hour >= 9 && time_hour <= 17) {  // Very strict hours
                        printf("✅ ACCESS GRANTED to Top Secret Zone\n");
                        printf("⚠️  WARNING: Highest security level - dual authentication logged\n");
                    } else {
                        printf("❌ ACCESS DENIED - Outside authorized hours (9-17)\n");
                    }
                } else {
                    printf("❌ ACCESS DENIED - Badge AND biometric required for top secret\n");
                }
            } else {
                printf("❌ ACCESS DENIED - Super Admin level required\n");
            }
            
        } else {
            printf("❌ ACCESS DENIED - Invalid security zone\n");
        }
        
    } else {
        // Guest level or invalid
        if (requested_zone == ZONE_PUBLIC) {
            printf("❌ ACCESS DENIED - Guests require escort for any zone access\n");
        } else {
            printf("❌ ACCESS DENIED - Insufficient privileges\n");
        }
    }
}

int main() {
    int level, zone, hour;
    char badge, biometric, emergency;
    
    printf("=== SECURITY ACCESS REQUEST ===\n");
    printf("Enter access level (1=Guest, 2=User, 3=Admin, 4=SuperAdmin): ");
    scanf("%d", &level);
    
    printf("Enter requested zone (1=Public, 2=Restricted, 3=Classified, 4=TopSecret): ");
    scanf("%d", &zone);
    
    printf("Current hour (0-23): ");
    scanf("%d", &hour);
    
    printf("Have security badge? (y/n): ");
    scanf(" %c", &badge);
    
    printf("Biometric verified? (y/n): ");
    scanf(" %c", &biometric);
    
    printf("Emergency mode active? (y/n): ");
    scanf(" %c", &emergency);
    
    bool has_badge = (badge == 'y' || badge == 