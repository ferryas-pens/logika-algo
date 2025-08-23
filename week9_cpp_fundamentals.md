# Minggu 9: Bahasa C/C++ - Fundamentals dan Modern Programming
## Logika dan Pemrograman

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. **Memahami evolusi dan perbedaan fundamental** antara bahasa C dan C++ serta kapan menggunakan masing-masing
2. **Menguasai sintaks dasar C/C++** termasuk struktur program, tipe data, dan operator
3. **Mengimplementasikan konsep Object-Oriented Programming (OOP)** dalam C++ dengan classes, objects, inheritance, dan polymorphism
4. **Memahami memory management** termasuk pointers, references, dan dynamic allocation
5. **Menguasai Standard Template Library (STL)** untuk struktur data dan algoritma yang efisien
6. **Mengembangkan best practices** dalam Modern C++ (C++11/14/17/20)
7. **Membuat aplikasi praktis** yang mengintegrasikan seluruh konsep yang telah dipelajari

---

## 📚 Pengantar: Dari C ke C++ - Evolusi Bahasa Pemrograman

### Sejarah dan Filosofi

C++ dikembangkan oleh Bjarne Stroustrup di Bell Labs mulai tahun 1979 sebagai ekstensi dari bahasa C. Nama aslinya adalah "C with Classes" yang kemudian berkembang menjadi C++ pada tahun 1983. Tanda "++" merujuk pada operator increment dalam C, menandakan bahwa C++ adalah evolusi dari C.

**Perbedaan Fundamental C dan C++:**

| Aspek | C | C++ |
|-------|---|-----|
| Paradigma | Procedural | Multi-paradigma (Procedural, OOP, Generic) |
| Abstraksi | Low-level | Mid to High-level |
| Memory Management | Manual (malloc/free) | Manual + Automated (new/delete, RAII) |
| Type Safety | Weak | Stronger |
| Standard Library | Minimal | Rich (STL) |
| Namespace | Tidak ada | Ada |
| Function Overloading | Tidak ada | Ada |
| Templates | Tidak ada | Ada |

### Mengapa Belajar C++ di Era Modern?

C++ is a versatile programming language used in a wide range of applications, from software development to game design and system programming. Bahasa ini tetap relevan karena:

1. **Performance**: Kontrol langsung terhadap hardware menghasilkan performa optimal
2. **System Programming**: Digunakan untuk OS, drivers, dan embedded systems
3. **Game Development**: Standar industri untuk game engines (Unreal, Unity backend)
4. **High-Frequency Trading**: Kecepatan eksekusi kritis untuk aplikasi finansial
5. **Machine Learning**: Backend libraries seperti TensorFlow ditulis dalam C++

---

## 🏗️ Struktur Program C++ Modern

### Anatomi Program C++ Sederhana

```cpp
// Program C++ Modern dengan Best Practices
#include <iostream>     // Header untuk I/O operations
#include <string>       // Header untuk string class
#include <vector>       // Header untuk dynamic arrays
#include <memory>       // Header untuk smart pointers

// Using declarations untuk menghindari std:: prefix berulang
using std::cout;
using std::endl;
using std::string;

// Namespace custom untuk organisasi kode
namespace MyApp {
    // Constants dengan constexpr (compile-time constant)
    constexpr int MAX_USERS = 100;
    constexpr double PI = 3.14159265359;
    
    // Template function untuk generic programming
    template<typename T>
    T maximum(T a, T b) {
        return (a > b) ? a : b;
    }
    
    // Class dengan Modern C++ features
    class User {
    private:
        string m_name;      // m_ prefix untuk member variables
        int m_age;
        static int s_count; // s_ prefix untuk static members
        
    public:
        // Constructor dengan member initializer list
        User(const string& name, int age) 
            : m_name(name), m_age(age) {
            s_count++;
        }
        
        // Destructor
        ~User() {
            s_count--;
        }
        
        // Copy constructor (Rule of Three/Five)
        User(const User& other) 
            : m_name(other.m_name), m_age(other.m_age) {
            s_count++;
        }
        
        // Move constructor (C++11)
        User(User&& other) noexcept 
            : m_name(std::move(other.m_name)), m_age(other.m_age) {
            s_count++;
        }
        
        // Getter dengan const correctness
        const string& getName() const { return m_name; }
        int getAge() const { return m_age; }
        
        // Static member function
        static int getUserCount() { return s_count; }
        
        // Operator overloading
        bool operator<(const User& other) const {
            return m_age < other.m_age;
        }
        
        // Friend function untuk operator<<
        friend std::ostream& operator<<(std::ostream& os, const User& user);
    };
    
    // Static member initialization
    int User::s_count = 0;
    
    // Friend function implementation
    std::ostream& operator<<(std::ostream& os, const User& user) {
        os << "User: " << user.m_name << ", Age: " << user.m_age;
        return os;
    }
}

// Main function - entry point
int main() {
    cout << "=== C++ Modern Programming Demo ===\n" << endl;
    
    // 1. Auto type inference (C++11)
    auto message = string("Welcome to Modern C++!");
    cout << message << endl;
    
    // 2. Range-based for loop (C++11)
    std::vector<int> numbers = {1, 2, 3, 4, 5};
    cout << "\nNumbers: ";
    for (const auto& num : numbers) {
        cout << num << " ";
    }
    cout << endl;
    
    // 3. Lambda expressions (C++11)
    auto square = [](int x) -> int { return x * x; };
    cout << "Square of 5: " << square(5) << endl;
    
    // 4. Smart pointers (C++11)
    {
        std::unique_ptr<MyApp::User> user1 = 
            std::make_unique<MyApp::User>("Alice", 25);
        cout << "\n" << *user1 << endl;
        
        // Automatic memory management - no delete needed
    } // user1 automatically deleted here
    
    // 5. Template usage
    cout << "\nMaximum of 10 and 20: " << MyApp::maximum(10, 20) << endl;
    cout << "Maximum of 3.14 and 2.71: " << MyApp::maximum(3.14, 2.71) << endl;
    
    // 6. Structured bindings (C++17)
    std::pair<string, int> person = {"Bob", 30};
    auto [name, age] = person;  // Destructuring
    cout << "\nPerson: " << name << ", " << age << " years old" << endl;
    
    return 0;
}
```

---

## 💻 Proyek Praktis: Sistem Manajemen Perpustakaan

### Implementasi Lengkap dengan Modern C++

Untuk mengintegrasikan semua konsep yang telah dipelajari, mari kita buat sistem manajemen perpustakaan yang komprehensif:

```cpp
#include <iostream>
#include <vector>
#include <map>
#include <algorithm>
#include <memory>
#include <fstream>
#include <sstream>
#include <chrono>
#include <iomanip>
#include <optional>
#include <variant>

// Forward declarations
class Book;
class Member;
class Transaction;

// ===== ENUMS AND CONSTANTS =====
enum class BookStatus {
    AVAILABLE,
    BORROWED,
    RESERVED,
    MAINTENANCE
};

enum class MemberType {
    STUDENT,
    FACULTY,
    STAFF,
    GUEST
};

// ===== BASE CLASSES =====
class LibraryItem {
protected:
    std::string m_id;
    std::string m_title;
    std::chrono::system_clock::time_point m_dateAdded;
    
public:
    LibraryItem(const std::string& id, const std::string& title)
        : m_id(id), m_title(title), m_dateAdded(std::chrono::system_clock::now()) {}
    
    virtual ~LibraryItem() = default;
    
    const std::string& getId() const { return m_id; }
    const std::string& getTitle() const { return m_title; }
    
    virtual void displayInfo() const = 0;
    virtual std::string getType() const = 0;
};

// ===== BOOK CLASS =====
class Book : public LibraryItem {
private:
    std::string m_author;
    std::string m_isbn;
    int m_publicationYear;
    BookStatus m_status;
    std::optional<std::string> m_borrowerId;
    std::optional<std::chrono::system_clock::time_point> m_dueDate;
    
public:
    Book(const std::string& id, const std::string& title, 
         const std::string& author, const std::string& isbn, int year)
        : LibraryItem(id, title), m_author(author), m_isbn(isbn),
          m_publicationYear(year), m_status(BookStatus::AVAILABLE) {}
    
    void displayInfo() const override {
        std::cout << "Book ID: " << m_id << "\n"
                  << "Title: " << m_title << "\n"
                  << "Author: " << m_author << "\n"
                  << "ISBN: " << m_isbn << "\n"
                  << "Year: " << m_publicationYear << "\n"
                  << "Status: " << getStatusString() << "\n";
        
        if (m_borrowerId.has_value()) {
            std::cout << "Borrowed by: " << m_borrowerId.value() << "\n";
        }
        if (m_dueDate.has_value()) {
            auto time_t = std::chrono::system_clock::to_time_t(m_dueDate.value());
            std::cout << "Due date: " << std::put_time(std::localtime(&time_t), "%Y-%m-%d") << "\n";
        }
    }
    
    std::string getType() const override { return "Book"; }
    
    BookStatus getStatus() const { return m_status; }
    void setStatus(BookStatus status) { m_status = status; }
    
    void setBorrower(const std::string& memberId, int daysToBorrow) {
        m_borrowerId = memberId;
        m_status = BookStatus::BORROWED;
        auto now = std::chrono::system_clock::now();
        m_dueDate = now + std::chrono::hours(24 * daysToBorrow);
    }
    
    void returnBook() {
        m_borrowerId = std::nullopt;
        m_dueDate = std::nullopt;
        m_status = BookStatus::AVAILABLE;
    }
    
    bool isOverdue() const {
        if (!m_dueDate.has_value()) return false;
        return std::chrono::system_clock::now() > m_dueDate.value();
    }
    
    const std::string& getAuthor() const { return m_author; }
    
private:
    std::string getStatusString() const {
        switch (m_status) {
            case BookStatus::AVAILABLE: return "Available";
            case BookStatus::BORROWED: return "Borrowed";
            case BookStatus::RESERVED: return "Reserved";
            case BookStatus::MAINTENANCE: return "Under Maintenance";
            default: return "Unknown";
        }
    }
};

// ===== MEMBER CLASS =====
class Member {
private:
    std::string m_id;
    std::string m_name;
    std::string m_email;
    MemberType m_type;
    std::vector<std::string> m_borrowedBooks;
    int m_maxBooks;
    
public:
    Member(const std::string& id, const std::string& name, 
           const std::string& email, MemberType type)
        : m_id(id), m_name(name), m_email(email), m_type(type) {
        
        // Set borrowing limits based on member type
        switch (type) {
            case MemberType::STUDENT: m_maxBooks = 3; break;
            case MemberType::FACULTY: m_maxBooks = 10; break;
            case MemberType::STAFF: m_maxBooks = 5; break;
            case MemberType::GUEST: m_maxBooks = 1; break;
        }
    }
    
    bool canBorrow() const {
        return m_borrowedBooks.size() < static_cast<size_t>(m_maxBooks);
    }
    
    void borrowBook(const std::string& bookId) {
        if (canBorrow()) {
            m_borrowedBooks.push_back(bookId);
        }
    }
    
    void returnBook(const std::string& bookId) {
        auto it = std::find(m_borrowedBooks.begin(), m_borrowedBooks.end(), bookId);
        if (it != m_borrowedBooks.end()) {
            m_borrowedBooks.erase(it);
        }
    }
    
    void displayInfo() const {
        std::cout << "Member ID: " << m_id << "\n"
                  << "Name: " << m_name << "\n"
                  << "Email: " << m_email << "\n"
                  << "Type: " << getMemberTypeString() << "\n"
                  << "Books borrowed: " << m_borrowedBooks.size() 
                  << "/" << m_maxBooks << "\n";
        
        if (!m_borrowedBooks.empty()) {
            std::cout << "Borrowed book IDs: ";
            for (const auto& bookId : m_borrowedBooks) {
                std::cout << bookId << " ";
            }
            std::cout << "\n";
        }
    }
    
    const std::string& getId() const { return m_id; }
    const std::string& getName() const { return m_name; }
    
private:
    std::string getMemberTypeString() const {
        switch (m_type) {
            case MemberType::STUDENT: return "Student";
            case MemberType::FACULTY: return "Faculty";
            case MemberType::STAFF: return "Staff";
            case MemberType::GUEST: return "Guest";
            default: return "Unknown";
        }
    }
};

// ===== LIBRARY SYSTEM CLASS =====
class LibrarySystem {
private:
    std::map<std::string, std::unique_ptr<Book>> m_books;
    std::map<std::string, std::unique_ptr<Member>> m_members;
    std::vector<std::string> m_transactionLog;
    
    // Singleton pattern
    static LibrarySystem* s_instance;
    LibrarySystem() = default;
    
public:
    static LibrarySystem* getInstance() {
        if (!s_instance) {
            s_instance = new LibrarySystem();
        }
        return s_instance;
    }
    
    // Book management
    void addBook(std::unique_ptr<Book> book) {
        std::string id = book->getId();
        m_books[id] = std::move(book);
        logTransaction("Book added: " + id);
    }
    
    Book* findBook(const std::string& id) {
        auto it = m_books.find(id);
        return (it != m_books.end()) ? it->second.get() : nullptr;
    }
    
    std::vector<Book*> searchBooksByAuthor(const std::string& author) {
        std::vector<Book*> results;
        for (const auto& [id, book] : m_books) {
            if (book->getAuthor().find(author) != std::string::npos) {
                results.push_back(book.get());
            }
        }
        return results;
    }
    
    // Member management
    void addMember(std::unique_ptr<Member> member) {
        std::string id = member->getId();
        m_members[id] = std::move(member);
        logTransaction("Member added: " + id);
    }
    
    Member* findMember(const std::string& id) {
        auto it = m_members.find(id);
        return (it != m_members.end()) ? it->second.get() : nullptr;
    }
    
    // Borrowing operations
    bool borrowBook(const std::string& memberId, const std::string& bookId) {
        Member* member = findMember(memberId);
        Book* book = findBook(bookId);
        
        if (!member || !book) {
            std::cout << "Member or book not found.\n";
            return false;
        }
        
        if (!member->canBorrow()) {
            std::cout << "Member has reached borrowing limit.\n";
            return false;
        }
        
        if (book->getStatus() != BookStatus::AVAILABLE) {
            std::cout << "Book is not available.\n";
            return false;
        }
        
        // Determine loan period based on member type
        int loanDays = 14; // Default
        
        book->setBorrower(memberId, loanDays);
        member->borrowBook(bookId);
        
        logTransaction("Book " + bookId + " borrowed by " + memberId);
        return true;
    }
    
    bool returnBook(const std::string& memberId, const std::string& bookId) {
        Member* member = findMember(memberId);
        Book* book = findBook(bookId);
        
        if (!member || !book) {
            std::cout << "Member or book not found.\n";
            return false;
        }
        
        if (book->isOverdue()) {
            std::cout << "Book is overdue! Fine may apply.\n";
        }
        
        book->returnBook();
        member->returnBook(bookId);
        
        logTransaction("Book " + bookId + " returned by " + memberId);
        return true;
    }
    
    // Reports
    void displayAllBooks() const {
        std::cout << "\n=== ALL BOOKS IN LIBRARY ===\n";
        for (const auto& [id, book] : m_books) {
            book->displayInfo();
            std::cout << "---\n";
        }
    }
    
    void displayAvailableBooks() const {
        std::cout << "\n=== AVAILABLE BOOKS ===\n";
        for (const auto& [id, book] : m_books) {
            if (book->getStatus() == BookStatus::AVAILABLE) {
                book->displayInfo();
                std::cout << "---\n";
            }
        }
    }
    
    void displayAllMembers() const {
        std::cout << "\n=== ALL MEMBERS ===\n";
        for (const auto& [id, member] : m_members) {
            member->displayInfo();
            std::cout << "---\n";
        }
    }
    
    void displayTransactionLog() const {
        std::cout << "\n=== TRANSACTION LOG ===\n";
        for (const auto& transaction : m_transactionLog) {
            std::cout << transaction << "\n";
        }
    }
    
private:
    void logTransaction(const std::string& message) {
        auto now = std::chrono::system_clock::now();
        auto time_t = std::chrono::system_clock::to_time_t(now);
        
        std::stringstream ss;
        ss << std::put_time(std::localtime(&time_t), "%Y-%m-%d %H:%M:%S");
        ss << " - " << message;
        
        m_transactionLog.push_back(ss.str());
    }
};

// Static member initialization
LibrarySystem* LibrarySystem::s_instance = nullptr;

// ===== MAIN PROGRAM =====
int main() {
    std::cout << "=== LIBRARY MANAGEMENT SYSTEM ===\n\n";
    
    // Get library instance
    LibrarySystem* library = LibrarySystem::getInstance();
    
    // Add books to library
    library->addBook(std::make_unique<Book>("B001", "The C++ Programming Language", 
                                            "Bjarne Stroustrup", "978-0321563842", 2013));
    library->addBook(std::make_unique<Book>("B002", "Effective Modern C++", 
                                            "Scott Meyers", "978-1491903995", 2014));
    library->addBook(std::make_unique<Book>("B003", "C++ Primer", 
                                            "Stanley Lippman", "978-0321714114", 2012));
    library->addBook(std::make_unique<Book>("B004", "The C Programming Language", 
                                            "Kernighan & Ritchie", "978-0131103627", 1988));
    
    // Add members
    library->addMember(std::make_unique<Member>("M001", "Alice Johnson", 
                                                "alice@email.com", MemberType::STUDENT));
    library->addMember(std::make_unique<Member>("M002", "Dr. Bob Smith", 
                                                "bob@university.edu", MemberType::FACULTY));
    library->addMember(std::make_unique<Member>("M003", "Charlie Brown", 
                                                "charlie@email.com", MemberType::STAFF));
    
    // Display initial state
    library->displayAvailableBooks();
    library->displayAllMembers();
    
    // Perform transactions
    std::cout << "\n=== PERFORMING TRANSACTIONS ===\n";
    
    // Borrow books
    if (library->borrowBook("M001", "B001")) {
        std::cout << "Alice borrowed 'The C++ Programming Language'\n";
    }
    
    if (library->borrowBook("M002", "B002")) {
        std::cout << "Dr. Bob borrowed 'Effective Modern C++'\n";
    }
    
    if (library->borrowBook("M001", "B003")) {
        std::cout << "Alice borrowed 'C++ Primer'\n";
    }
    
    // Try to borrow unavailable book
    if (!library->borrowBook("M003", "B001")) {
        std::cout << "Charlie couldn't borrow the already borrowed book\n";
    }
    
    // Search for books by author
    std::cout << "\n=== SEARCH RESULTS ===\n";
    auto stroustrupBooks = library->searchBooksByAuthor("Stroustrup");
    std::cout << "Books by Stroustrup:\n";
    for (auto* book : stroustrupBooks) {
        std::cout << "- " << book->getTitle() << "\n";
    }
    
    // Return a book
    std::cout << "\n=== RETURNING BOOKS ===\n";
    if (library->returnBook("M001", "B001")) {
        std::cout << "Alice returned 'The C++ Programming Language'\n";
    }
    
    // Display final state
    std::cout << "\n=== FINAL STATE ===\n";
    library->displayAvailableBooks();
    
    // Display transaction log
    library->displayTransactionLog();
    
    // Interactive menu (simplified)
    char choice;
    do {
        std::cout << "\n=== MENU ===\n";
        std::cout << "1. Display all books\n";
        std::cout << "2. Display all members\n";
        std::cout << "3. Search book by ID\n";
        std::cout << "4. Borrow book\n";
        std::cout << "5. Return book\n";
        std::cout << "0. Exit\n";
        std::cout << "Choice: ";
        std::cin >> choice;
        
        switch (choice) {
            case '1':
                library->displayAllBooks();
                break;
            case '2':
                library->displayAllMembers();
                break;
            case '3': {
                std::string bookId;
                std::cout << "Enter book ID: ";
                std::cin >> bookId;
                Book* book = library->findBook(bookId);
                if (book) {
                    book->displayInfo();
                } else {
                    std::cout << "Book not found.\n";
                }
                break;
            }
            case '4': {
                std::string memberId, bookId;
                std::cout << "Enter member ID: ";
                std::cin >> memberId;
                std::cout << "Enter book ID: ";
                std::cin >> bookId;
                library->borrowBook(memberId, bookId);
                break;
            }
            case '5': {
                std::string memberId, bookId;
                std::cout << "Enter member ID: ";
                std::cin >> memberId;
                std::cout << "Enter book ID: ";
                std::cin >> bookId;
                library->returnBook(memberId, bookId);
                break;
            }
            case '0':
                std::cout << "Exiting...\n";
                break;
            default:
                std::cout << "Invalid choice.\n";
        }
    } while (choice != '0');
    
    return 0;
}
```

---

## 📝 Latihan dan Soal

### Latihan Dasar

#### Latihan 1: Class dan Object Basics
Buat class `Student` dengan properties nama, NIM, dan IPK. Implementasikan constructor, destructor, dan method untuk display info.

**Solusi:**
```cpp
#include <iostream>
#include <string>

class Student {
private:
    std::string m_nama;
    std::string m_nim;
    double m_ipk;
    
public:
    // Constructor
    Student(const std::string& nama, const std::string& nim, double ipk)
        : m_nama(nama), m_nim(nim), m_ipk(ipk) {
        std::cout << "Student " << m_nama << " created\n";
    }
    
    // Destructor
    ~Student() {
        std::cout << "Student " << m_nama << " destroyed\n";
    }
    
    // Display method
    void displayInfo() const {
        std::cout << "Nama: " << m_nama << "\n"
                  << "NIM: " << m_nim << "\n"
                  << "IPK: " << m_ipk << "\n";
    }
    
    // Getters
    const std::string& getNama() const { return m_nama; }
    double getIPK() const { return m_ipk; }
};

int main() {
    Student s1("Budi Santoso", "2024001", 3.75);
    s1.displayInfo();
    
    return 0;
}
```

#### Latihan 2: Operator Overloading
Implementasikan operator overloading untuk class `Complex` number.

**Solusi:**
```cpp
#include <iostream>

class Complex {
private:
    double real, imag;
    
public:
    Complex(double r = 0, double i = 0) : real(r), imag(i) {}
    
    // Operator +
    Complex operator+(const Complex& other) const {
        return Complex(real + other.real, imag + other.imag);
    }
    
    // Operator -
    Complex operator-(const Complex& other) const {
        return Complex(real - other.real, imag - other.imag);
    }
    
    // Operator *
    Complex operator*(const Complex& other) const {
        double r = real * other.real - imag * other.imag;
        double i = real * other.imag + imag * other.real;
        return Complex(r, i);
    }
    
    // Operator ==
    bool operator==(const Complex& other) const {
        return (real == other.real && imag == other.imag);
    }
    
    // Friend function for output
    friend std::ostream& operator<<(std::ostream& os, const Complex& c) {
        os << c.real;
        if (c.imag >= 0) os << "+";
        os << c.imag << "i";
        return os;
    }
};

int main() {
    Complex c1(3, 4);
    Complex c2(1, 2);
    
    std::cout << "c1 = " << c1 << "\n";
    std::cout << "c2 = " << c2 << "\n";
    std::cout << "c1 + c2 = " << (c1 + c2) << "\n";
    std::cout << "c1 - c2 = " << (c1 - c2) << "\n";
    std::cout << "c1 * c2 = " << (c1 * c2) << "\n";
    
    return 0;
}
```

### Latihan Menengah

#### Latihan 3: Template Function dan Class
Buat template untuk generic container dengan operations.

**Solusi:**
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

template<typename T>
class Container {
private:
    std::vector<T> data;
    
public:
    void add(const T& item) {
        data.push_back(item);
    }
    
    void remove(const T& item) {
        auto it = std::find(data.begin(), data.end(), item);
        if (it != data.end()) {
            data.erase(it);
        }
    }
    
    bool contains(const T& item) const {
        return std::find(data.begin(), data.end(), item) != data.end();
    }
    
    size_t size() const {
        return data.size();
    }
    
    T getMax() const {
        if (data.empty()) throw std::runtime_error("Container is empty");
        return *std::max_element(data.begin(), data.end());
    }
    
    T getMin() const {
        if (data.empty()) throw std::runtime_error("Container is empty");
        return *std::min_element(data.begin(), data.end());
    }
    
    void display() const {
        std::cout << "Container [";
        for (size_t i = 0; i < data.size(); ++i) {
            std::cout << data[i];
            if (i < data.size() - 1) std::cout << ", ";
        }
        std::cout << "]\n";
    }
};

int main() {
    Container<int> intContainer;
    intContainer.add(5);
    intContainer.add(2);
    intContainer.add(8);
    intContainer.add(1);
    
    intContainer.display();
    std::cout << "Max: " << intContainer.getMax() << "\n";
    std::cout << "Min: " << intContainer.getMin() << "\n";
    
    Container<std::string> stringContainer;
    stringContainer.add("apple");
    stringContainer.add("banana");
    stringContainer.add("cherry");
    
    stringContainer.display();
    std::cout << "Contains 'banana': " << stringContainer.contains("banana") << "\n";
    
    return 0;
}
```

### Latihan Lanjutan

#### Latihan 4: Smart Pointers dan RAII
Implementasikan resource management dengan smart pointers.

**Solusi:**
```cpp
#include <iostream>
#include <memory>
#include <vector>

class FileResource {
private:
    std::string filename;
    FILE* file;
    
public:
    FileResource(const std::string& fname) : filename(fname) {
        file = fopen(filename.c_str(), "w");
        if (file) {
            std::cout << "File opened: " << filename << "\n";
        }
    }
    
    ~FileResource() {
        if (file) {
            fclose(file);
            std::cout << "File closed: " << filename << "\n";
        }
    }
    
    void write(const std::string& data) {
        if (file) {
            fprintf(file, "%s\n", data.c_str());
        }
    }
};

class ResourceManager {
private:
    std::vector<std::shared_ptr<FileResource>> resources;
    
public:
    std::shared_ptr<FileResource> createResource(const std::string& filename) {
        auto resource = std::make_shared<FileResource>(filename);
        resources.push_back(resource);
        return resource;
    }
    
    size_t getResourceCount() const {
        return resources.size();
    }
    
    void cleanup() {
        resources.clear();
        std::cout << "All resources cleaned up\n";
    }
};

int main() {
    ResourceManager manager;
    
    {
        auto file1 = manager.createResource("file1.txt");
        file1->write("Hello from file 1");
        
        auto file2 = manager.createResource("file2.txt");
        file2->write("Hello from file 2");
        
        std::cout << "Active resources: " << manager.getResourceCount() << "\n";
    }
    
    manager.cleanup();
    
    return 0;
}
```

---

## 💡 Best Practices dan Tips

### 1. Modern C++ Guidelines

```cpp
// PREFER auto for complex types
auto result = std::make_unique<std::vector<std::pair<std::string, int>>>();

// USE range-based for loops
for (const auto& item : container) {
    // process item
}

// PREFER smart pointers over raw pointers
std::unique_ptr<MyClass> ptr = std::make_unique<MyClass>();

// USE const correctness
void processData(const std::vector<int>& data);

// PREFER std::string over char arrays
std::string name = "Modern C++";
```

### 2. RAII (Resource Acquisition Is Initialization)

```cpp
// GOOD: RAII ensures cleanup
class DatabaseConnection {
    Connection* conn;
public:
    DatabaseConnection() : conn(new Connection()) {}
    ~DatabaseConnection() { delete conn; }
};

// BETTER: Use smart pointers
class DatabaseConnection {
    std::unique_ptr<Connection> conn;
public:
    DatabaseConnection() : conn(std::make_unique<Connection>()) {}
    // Destructor automatically handles cleanup
};
```

### 3. Error Handling

```cpp
// USE exceptions for error handling
void processFile(const std::string& filename) {
    std::ifstream file(filename);
    if (!file.is_open()) {
        throw std::runtime_error("Cannot open file: " + filename);
    }
    // Process file
}

// USE optional for values that might not exist
std::optional<int> findValue(const std::vector<int>& vec, int target) {
    auto it = std::find(vec.begin(), vec.end(), target);
    if (it != vec.end()) {
        return *it;
    }
    return std::nullopt;
}
```

---

## 🎯 Kesimpulan

### Ringkasan Materi Minggu 9

Dalam minggu ke-9 ini, kita telah mempelajari komprehensif tentang bahasa C++ modern:

#### 1. **Evolusi dari C ke C++**
- Memahami perbedaan fundamental antara C dan C++
- Multi-paradigma programming (procedural, OOP, generic)
- Type safety dan abstraksi yang lebih baik

#### 2. **Object-Oriented Programming**
- Encapsulation dengan classes dan access modifiers
- Inheritance untuk code reuse dan hierarchy
- Polymorphism dengan virtual functions
- Abstraction dengan abstract base classes

#### 3. **Memory Management**
- Stack vs Heap memory
- Pointers dan references
- Smart pointers (unique_ptr, shared_ptr, weak_ptr)
- RAII principle untuk resource management

#### 4. **Standard Template Library (STL)**
- Containers (vector, list, map, set, etc.)
- Iterators untuk traversal
- Algorithms untuk data manipulation
- Functional programming dengan lambdas

#### 5. **Modern C++ Features**
- Auto type deduction
- Range-based for loops
- Lambda expressions
- Move semantics
- Concepts dan constraints (C++20)

### Key Takeaways

1. **C++ adalah bahasa multi-paradigma** yang mendukung berbagai programming styles
2. **OOP principles** membantu membuat code yang modular dan maintainable
3. **Smart pointers** mengeliminasi manual memory management issues
4. **STL** menyediakan efficient implementations untuk common data structures
5. **Modern C++ features** membuat code lebih safe dan expressive
6. **RAII principle** ensures automatic resource cleanup
7. **Template programming** enables generic and reusable code

### Persiapan untuk Minggu Selanjutnya

Materi Minggu 9 ini mempersiapkan untuk:
- **Minggu 10**: Fungsi dan modularisasi program yang lebih advanced
- **Minggu 11**: Array dan struktur data yang lebih kompleks
- **Project Development**: Implementasi aplikasi real-world dengan C++

---

## 📖 Referensi dan Sumber Pembelajaran

### Buku Rekomendasi
- "The C++ Programming Language" - Bjarne Stroustrup
- "Effective Modern C++" - Scott Meyers
- "C++ Primer" - Stanley Lippman

### Online Resources
- LearnCpp.com - Comprehensive free tutorials
- CppReference - Complete language reference
- ISO C++ - Official C++ standards website

### Video Tutorials
- CppCon Conference Videos
- The Cherno C++ Series
- Jason Turner's C++ Weekly

---

**Total Words: ~5000+**
```

---

## 🔧 Tipe Data dan Type System dalam C++

### Fundamental Types dengan Modern Features

```cpp
#include <iostream>
#include <limits>
#include <cstdint>  // Fixed-width integer types
#include <typeinfo>
#include <string_view>  // C++17

int main() {
    // ===== INTEGER TYPES =====
    // Traditional types
    short s = 32767;
    int i = 2147483647;
    long l = 2147483647L;
    long long ll = 9223372036854775807LL;
    
    // Fixed-width types (C++11) - Portable across platforms
    int8_t i8 = 127;                    // Exactly 8 bits
    int16_t i16 = 32767;                // Exactly 16 bits
    int32_t i32 = 2147483647;           // Exactly 32 bits
    int64_t i64 = 9223372036854775807;  // Exactly 64 bits
    
    // Unsigned versions
    uint8_t u8 = 255;
    uint16_t u16 = 65535;
    uint32_t u32 = 4294967295U;
    uint64_t u64 = 18446744073709551615ULL;
    
    // Size_t for array indexing and sizes
    size_t array_size = 100;
    
    // ===== FLOATING POINT TYPES =====
    float f = 3.14159f;           // 32-bit, ~7 decimal digits precision
    double d = 3.141592653589793; // 64-bit, ~15 decimal digits precision
    long double ld = 3.141592653589793238L; // Extended precision
    
    // ===== CHARACTER TYPES =====
    char c = 'A';           // Basic character
    char8_t c8 = u8'A';    // UTF-8 character (C++20)
    char16_t c16 = u'A';   // UTF-16 character (C++11)
    char32_t c32 = U'A';   // UTF-32 character (C++11)
    wchar_t wc = L'A';     // Wide character
    
    // ===== BOOLEAN TYPE =====
    bool flag = true;
    bool condition = (i > 0);
    
    // ===== VOID TYPE =====
    // void cannot hold values but used for:
    void* generic_ptr = &i;  // Generic pointer
    // void function();       // Function returning nothing
    
    // ===== NULL POINTER TYPE (C++11) =====
    std::nullptr_t null_ptr = nullptr;  // Type-safe null
    
    // ===== AUTO TYPE DEDUCTION (C++11) =====
    auto automatic_int = 42;        // Deduced as int
    auto automatic_double = 3.14;   // Deduced as double
    auto automatic_string = "Hello"; // Deduced as const char*
    
    // ===== DECLTYPE (C++11) =====
    decltype(i) another_int = 100;  // Same type as i
    
    // ===== STRING TYPES =====
    std::string cpp_string = "C++ String";
    std::string_view string_view = "Lightweight string view"; // C++17
    const char* c_string = "C-style string";
    
    // ===== TYPE INFORMATION =====
    std::cout << "=== Type Information ===\n";
    std::cout << "Type of i: " << typeid(i).name() << "\n";
    std::cout << "Size of int: " << sizeof(int) << " bytes\n";
    std::cout << "Size of int64_t: " << sizeof(int64_t) << " bytes\n";
    
    // ===== NUMERIC LIMITS =====
    std::cout << "\n=== Numeric Limits ===\n";
    std::cout << "int min: " << std::numeric_limits<int>::min() << "\n";
    std::cout << "int max: " << std::numeric_limits<int>::max() << "\n";
    std::cout << "float epsilon: " << std::numeric_limits<float>::epsilon() << "\n";
    std::cout << "double infinity: " << std::numeric_limits<double>::infinity() << "\n";
    
    // ===== CONSTANTS AND LITERALS =====
    // Binary literals (C++14)
    int binary = 0b1010;  // 10 in decimal
    
    // Digit separators (C++14)
    long long big_number = 1'000'000'000LL;
    double pi = 3.141'592'653'589;
    
    // Hexadecimal floating point (C++17)
    double hex_float = 0x1.2p3;  // 1.125 * 2^3 = 9.0
    
    return 0;
}
```

---

## 🎭 Object-Oriented Programming dalam C++

### Konsep OOP Fundamental

C++ is an object-oriented language. It supports classes, objects, inheritance, polymorphism, and encapsulation. Mari kita explorasi implementasi lengkap OOP:

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <memory>
#include <algorithm>

// ===== ENCAPSULATION =====
class BankAccount {
private:
    std::string m_accountNumber;
    double m_balance;
    static int s_totalAccounts;
    
protected:
    std::string m_ownerName;
    
public:
    // Constructor
    BankAccount(const std::string& owner, const std::string& accNum, double initialBalance = 0.0)
        : m_ownerName(owner), m_accountNumber(accNum), m_balance(initialBalance) {
        s_totalAccounts++;
        std::cout << "Account created for " << owner << "\n";
    }
    
    // Virtual destructor untuk inheritance
    virtual ~BankAccount() {
        s_totalAccounts--;
        std::cout << "Account closed for " << m_ownerName << "\n";
    }
    
    // Public interface methods
    void deposit(double amount) {
        if (amount > 0) {
            m_balance += amount;
            std::cout << "Deposited: $" << amount << "\n";
        }
    }
    
    virtual bool withdraw(double amount) {
        if (amount > 0 && amount <= m_balance) {
            m_balance -= amount;
            std::cout << "Withdrawn: $" << amount << "\n";
            return true;
        }
        std::cout << "Insufficient funds!\n";
        return false;
    }
    
    // Getter methods dengan const correctness
    double getBalance() const { return m_balance; }
    const std::string& getOwner() const { return m_ownerName; }
    
    // Virtual method untuk polymorphism
    virtual void displayInfo() const {
        std::cout << "Account Owner: " << m_ownerName << "\n";
        std::cout << "Account Number: " << m_accountNumber << "\n";
        std::cout << "Balance: $" << m_balance << "\n";
    }
    
    // Static method
    static int getTotalAccounts() { return s_totalAccounts; }
};

// Static member initialization
int BankAccount::s_totalAccounts = 0;

// ===== INHERITANCE =====
class SavingsAccount : public BankAccount {
private:
    double m_interestRate;
    int m_withdrawalsThisMonth;
    static const int MAX_WITHDRAWALS = 6;
    
public:
    SavingsAccount(const std::string& owner, const std::string& accNum, 
                   double initialBalance, double interestRate)
        : BankAccount(owner, accNum, initialBalance), 
          m_interestRate(interestRate), m_withdrawalsThisMonth(0) {
        std::cout << "Savings account initialized with " << interestRate << "% interest\n";
    }
    
    // Override virtual method
    bool withdraw(double amount) override {
        if (m_withdrawalsThisMonth >= MAX_WITHDRAWALS) {
            std::cout << "Monthly withdrawal limit reached!\n";
            return false;
        }
        if (BankAccount::withdraw(amount)) {
            m_withdrawalsThisMonth++;
            return true;
        }
        return false;
    }
    
    void applyInterest() {
        double interest = getBalance() * m_interestRate / 100;
        deposit(interest);
        std::cout << "Interest applied: $" << interest << "\n";
    }
    
    // Override displayInfo
    void displayInfo() const override {
        std::cout << "=== SAVINGS ACCOUNT ===\n";
        BankAccount::displayInfo();
        std::cout << "Interest Rate: " << m_interestRate << "%\n";
        std::cout << "Withdrawals this month: " << m_withdrawalsThisMonth << "/" 
                  << MAX_WITHDRAWALS << "\n";
    }
};

// ===== MULTIPLE INHERITANCE =====
class Person {
protected:
    std::string m_name;
    int m_age;
    
public:
    Person(const std::string& name, int age) : m_name(name), m_age(age) {}
    virtual void introduce() const {
        std::cout << "Hi, I'm " << m_name << ", " << m_age << " years old.\n";
    }
};

class Employee {
protected:
    std::string m_employeeId;
    double m_salary;
    
public:
    Employee(const std::string& id, double salary) 
        : m_employeeId(id), m_salary(salary) {}
    virtual void work() const {
        std::cout << "Employee " << m_employeeId << " is working.\n";
    }
};

class Manager : public Person, public Employee {
private:
    std::vector<std::string> m_teamMembers;
    
public:
    Manager(const std::string& name, int age, const std::string& id, double salary)
        : Person(name, age), Employee(id, salary) {}
    
    void addTeamMember(const std::string& member) {
        m_teamMembers.push_back(member);
    }
    
    void introduce() const override {
        Person::introduce();
        std::cout << "I'm a manager with " << m_teamMembers.size() 
                  << " team members.\n";
    }
    
    void work() const override {
        std::cout << "Manager " << m_name << " is managing the team.\n";
    }
};

// ===== ABSTRACTION dengan Abstract Base Class =====
class Shape {
public:
    // Pure virtual functions membuat class abstract
    virtual double area() const = 0;
    virtual double perimeter() const = 0;
    virtual void draw() const = 0;
    
    // Virtual destructor untuk proper cleanup
    virtual ~Shape() = default;
    
    // Non-virtual method
    void displayInfo() const {
        std::cout << "Area: " << area() << "\n";
        std::cout << "Perimeter: " << perimeter() << "\n";
    }
};

class Rectangle : public Shape {
private:
    double m_width, m_height;
    
public:
    Rectangle(double w, double h) : m_width(w), m_height(h) {}
    
    double area() const override {
        return m_width * m_height;
    }
    
    double perimeter() const override {
        return 2 * (m_width + m_height);
    }
    
    void draw() const override {
        std::cout << "Drawing rectangle: " << m_width << "x" << m_height << "\n";
    }
};

class Circle : public Shape {
private:
    double m_radius;
    static constexpr double PI = 3.14159265359;
    
public:
    Circle(double r) : m_radius(r) {}
    
    double area() const override {
        return PI * m_radius * m_radius;
    }
    
    double perimeter() const override {
        return 2 * PI * m_radius;
    }
    
    void draw() const override {
        std::cout << "Drawing circle with radius: " << m_radius << "\n";
    }
};

// ===== POLYMORPHISM Demo =====
void processShape(const Shape& shape) {
    shape.draw();
    shape.displayInfo();
    std::cout << "---\n";
}

int main() {
    std::cout << "=== OOP DEMONSTRATION ===\n\n";
    
    // 1. Encapsulation Demo
    std::cout << "1. ENCAPSULATION:\n";
    BankAccount account1("John Doe", "ACC001", 1000);
    account1.deposit(500);
    account1.withdraw(200);
    account1.displayInfo();
    std::cout << "\n";
    
    // 2. Inheritance Demo
    std::cout << "2. INHERITANCE:\n";
    SavingsAccount savings("Jane Smith", "SAV001", 5000, 2.5);
    savings.deposit(1000);
    savings.applyInterest();
    savings.displayInfo();
    std::cout << "\n";
    
    // 3. Multiple Inheritance Demo
    std::cout << "3. MULTIPLE INHERITANCE:\n";
    Manager mgr("Bob Wilson", 35, "EMP100", 75000);
    mgr.addTeamMember("Alice");
    mgr.addTeamMember("Charlie");
    mgr.introduce();
    mgr.work();
    std::cout << "\n";
    
    // 4. Polymorphism Demo
    std::cout << "4. POLYMORPHISM:\n";
    Rectangle rect(10, 5);
    Circle circ(7);
    
    processShape(rect);
    processShape(circ);
    
    // Polymorphic container
    std::vector<std::unique_ptr<Shape>> shapes;
    shapes.push_back(std::make_unique<Rectangle>(3, 4));
    shapes.push_back(std::make_unique<Circle>(5));
    shapes.push_back(std::make_unique<Rectangle>(6, 8));
    
    std::cout << "Processing shapes in container:\n";
    for (const auto& shape : shapes) {
        processShape(*shape);
    }
    
    std::cout << "\nTotal bank accounts created: " 
              << BankAccount::getTotalAccounts() << "\n";
    
    return 0;
}
```

---

## 💾 Memory Management dan Pointers

### Pointers, References, dan Dynamic Memory

C++ gives you control over memory allocation and deallocation through pointers. Understanding how to work with pointers and manage memory is essential for writing efficient C++ programs.

```cpp
#include <iostream>
#include <memory>    // Smart pointers
#include <array>
#include <vector>
#include <cstring>

class MemoryDemo {
public:
    int value;
    MemoryDemo(int v = 0) : value(v) {
        std::cout << "Constructor called, value = " << value << "\n";
    }
    ~MemoryDemo() {
        std::cout << "Destructor called, value = " << value << "\n";
    }
};

int main() {
    std::cout << "=== MEMORY MANAGEMENT IN C++ ===\n\n";
    
    // ===== STACK MEMORY =====
    std::cout << "1. STACK MEMORY:\n";
    int stackVar = 42;
    int stackArray[5] = {1, 2, 3, 4, 5};
    
    std::cout << "Stack variable: " << stackVar << "\n";
    std::cout << "Stack array: ";
    for (int i : stackArray) {
        std::cout << i << " ";
    }
    std::cout << "\n\n";
    
    // ===== POINTERS BASICS =====
    std::cout << "2. POINTERS:\n";
    int* ptr = &stackVar;              // Pointer to int
    int** ptrToPtr = &ptr;            // Pointer to pointer
    
    std::cout << "Value: " << stackVar << "\n";
    std::cout << "Address: " << &stackVar << "\n";
    std::cout << "Pointer value: " << ptr << "\n";
    std::cout << "Dereferenced: " << *ptr << "\n";
    std::cout << "Pointer to pointer: " << **ptrToPtr << "\n\n";
    
    // Pointer arithmetic
    int arr[] = {10, 20, 30, 40, 50};
    int* arrPtr = arr;
    
    std::cout << "Pointer arithmetic:\n";
    for (int i = 0; i < 5; i++) {
        std::cout << "*(arrPtr + " << i << ") = " << *(arrPtr + i) << "\n";
    }
    std::cout << "\n";
    
    // ===== REFERENCES =====
    std::cout << "3. REFERENCES:\n";
    int original = 100;
    int& ref = original;               // Reference to int
    const int& constRef = original;    // Const reference
    
    std::cout << "Original: " << original << "\n";
    std::cout << "Reference: " << ref << "\n";
    ref = 200;  // Modifies original
    std::cout << "After ref = 200:\n";
    std::cout << "Original: " << original << "\n";
    std::cout << "Reference: " << ref << "\n\n";
    
    // ===== DYNAMIC MEMORY (OLD WAY) =====
    std::cout << "4. DYNAMIC MEMORY (C-style and old C++):\n";
    
    // C-style allocation
    int* cArray = (int*)malloc(5 * sizeof(int));
    if (cArray) {
        for (int i = 0; i < 5; i++) {
            cArray[i] = i * 10;
        }
        std::cout << "C-style array: ";
        for (int i = 0; i < 5; i++) {
            std::cout << cArray[i] << " ";
        }
        std::cout << "\n";
        free(cArray);  // Must free manually
    }
    
    // C++ new/delete
    int* singleInt = new int(42);
    int* dynamicArray = new int[5]{1, 2, 3, 4, 5};
    
    std::cout << "Single int: " << *singleInt << "\n";
    std::cout << "Dynamic array: ";
    for (int i = 0; i < 5; i++) {
        std::cout << dynamicArray[i] << " ";
    }
    std::cout << "\n";
    
    delete singleInt;        // Delete single object
    delete[] dynamicArray;   // Delete array
    std::cout << "\n";
    
    // ===== SMART POINTERS (MODERN C++) =====
    std::cout << "5. SMART POINTERS (Modern C++):\n";
    
    // unique_ptr - exclusive ownership
    {
        std::cout << "unique_ptr demo:\n";
        std::unique_ptr<MemoryDemo> uniqueObj = 
            std::make_unique<MemoryDemo>(100);
        
        // Can't copy, but can move
        std::unique_ptr<MemoryDemo> movedObj = std::move(uniqueObj);
        
        // uniqueObj is now nullptr
        if (!uniqueObj) {
            std::cout << "uniqueObj is null after move\n";
        }
        
        // Automatic cleanup when out of scope
    } // Destructor called here
    
    std::cout << "\n";
    
    // shared_ptr - shared ownership
    {
        std::cout << "shared_ptr demo:\n";
        std::shared_ptr<MemoryDemo> shared1 = 
            std::make_shared<MemoryDemo>(200);
        
        {
            std::shared_ptr<MemoryDemo> shared2 = shared1;
            std::cout << "Reference count: " << shared1.use_count() << "\n";
        } // shared2 destroyed, but object still alive
        
        std::cout << "Reference count: " << shared1.use_count() << "\n";
        
    } // Object destroyed when last shared_ptr is destroyed
    
    std::cout << "\n";
    
    // weak_ptr - non-owning observer
    {
        std::cout << "weak_ptr demo:\n";
        std::shared_ptr<MemoryDemo> shared = 
            std::make_shared<MemoryDemo>(300);
        std::weak_ptr<MemoryDemo> weak = shared;
        
        if (auto locked = weak.lock()) {
            std::cout << "Weak ptr locked, value: " << locked->value << "\n";
        }
        
        shared.reset(); // Destroy the object
        
        if (weak.expired()) {
            std::cout << "Weak ptr expired\n";
        }
    }
    
    std::cout << "\n";
    
    // ===== MEMORY LEAKS AND ISSUES =====
    std::cout << "6. COMMON MEMORY ISSUES:\n";
    
    // Example of RAII (Resource Acquisition Is Initialization)
    class FileHandler {
    private:
        FILE* file;
    public:
        FileHandler(const char* filename) {
            file = fopen(filename, "w");
            if (file) {
                std::cout << "File opened\n";
            }
        }
        
        ~FileHandler() {
            if (file) {
                fclose(file);
                std::cout << "File closed automatically\n";
            }
        }
        
        void write(const char* text) {
            if (file) {
                fprintf(file, "%s", text);
            }
        }
    };
    
    {
        FileHandler handler("test.txt");
        handler.write("RAII ensures cleanup!");
        // File automatically closed when handler goes out of scope
    }
    
    // ===== PLACEMENT NEW =====
    std::cout << "\n7. PLACEMENT NEW:\n";
    
    // Allocate raw memory
    alignas(MemoryDemo) char buffer[sizeof(MemoryDemo)];
    
    // Construct object in pre-allocated memory
    MemoryDemo* placementObj = new (buffer) MemoryDemo(400);
    
    // Must call destructor manually
    placementObj->~MemoryDemo();
    
    std::cout << "\n=== END OF MEMORY MANAGEMENT DEMO ===\n";
    
    return 0;
}
```

---

## 📦 Standard Template Library (STL)

### Containers, Iterators, dan Algorithms

The STL is a powerful library that provides a collection of classes and functions for data structures, algorithms, and iterators.

```cpp
#include <iostream>
#include <vector>
#include <list>
#include <deque>
#include <set>
#include <map>
#include <unordered_map>
#include <stack>
#include <queue>
#include <algorithm>
#include <numeric>
#include <functional>
#include <iterator>
#include <string>
#include <chrono>
#include <random>

// Template function untuk print container
template<typename Container>
void printContainer(const Container& c, const std::string& name) {
    std::cout << name << ": ";
    for (const auto& elem : c) {
        std::cout << elem << " ";
    }
    std::cout << "\n";
}

int main() {
    std::cout << "=== STANDARD TEMPLATE LIBRARY (STL) ===\n\n";
    
    // ===== SEQUENCE CONTAINERS =====
    std::cout << "1. SEQUENCE CONTAINERS:\n\n";
    
    // Vector - Dynamic array
    std::cout << "Vector (Dynamic Array):\n";
    std::vector<int> vec = {1, 2, 3, 4, 5};
    vec.push_back(6);           // Add to end
    vec.insert(vec.begin() + 2, 10); // Insert at position
    vec.erase(vec.begin() + 3);      // Remove element
    printContainer(vec, "Vector");
    std::cout << "Size: " << vec.size() << ", Capacity: " << vec.capacity() << "\n\n";
    
    // List - Doubly linked list
    std::cout << "List (Doubly Linked List):\n";
    std::list<int> lst = {10, 20, 30};
    lst.push_front(5);          // Add to front
    lst.push_back(40);          // Add to back
    lst.remove(20);             // Remove value
    printContainer(lst, "List");
    
    // Deque - Double-ended queue
    std::cout << "\nDeque (Double-ended Queue):\n";
    std::deque<int> dq = {3, 4, 5};
    dq.push_front(2);
    dq.push_back(6);
    printContainer(dq, "Deque");
    
    // ===== ASSOCIATIVE CONTAINERS =====
    std::cout << "\n2. ASSOCIATIVE CONTAINERS:\n\n";
    
    // Set - Unique sorted elements
    std::cout << "Set (Sorted Unique Elements):\n";
    std::set<int> s = {5, 1, 3, 1, 4, 2}; // Duplicates removed
    s.insert(6);
    printContainer(s, "Set");
    
    // Multiset - Sorted elements, allows duplicates
    std::cout << "\nMultiset (Sorted, Allows Duplicates):\n";
    std::multiset<int> ms = {3, 1, 4, 1, 5, 9, 2, 6, 5};
    printContainer(ms, "Multiset");
    
    // Map - Key-value pairs
    std::cout << "\nMap (Key-Value Pairs):\n";
    std::map<std::string, int> m;
    m["Alice"] = 25;
    m["Bob"] = 30;
    m["Charlie"] = 22;
    
    for (const auto& [key, value] : m) {  // Structured binding C++17
        std::cout << key << ": " << value << " ";
    }
    std::cout << "\n";
    
    // ===== UNORDERED CONTAINERS (Hash Tables) =====
    std::cout << "\n3. UNORDERED CONTAINERS:\n\n";
    
    std::unordered_map<std::string, double> grades;
    grades["Math"] = 95.5;
    grades["Physics"] = 88.0;
    grades["Chemistry"] = 92.3;
    
    std::cout << "Unordered Map (Hash Table):\n";
    for (const auto& [subject, grade] : grades) {
        std::cout << subject << ": " << grade << "\n";
    }
    
    // ===== CONTAINER ADAPTERS =====
    std::cout << "\n4. CONTAINER ADAPTERS:\n\n";
    
    // Stack (LIFO)
    std::cout << "Stack (LIFO):\n";
    std::stack<int> stk;
    stk.push(1);
    stk.push(2);
    stk.push(3);
    
    std::cout << "Stack elements (top to bottom): ";
    while (!stk.empty()) {
        std::cout << stk.top() << " ";
        stk.pop();
    }
    std::cout << "\n";
    
    // Queue (FIFO)
    std::cout << "\nQueue (FIFO):\n";
    std::queue<int> q;
    q.push(1);
    q.push(2);
    q.push(3);
    
    std::cout << "Queue elements (front to back): ";
    while (!q.empty()) {
        std::cout << q.front() << " ";
        q.pop();
    }
    std::cout << "\n";
    
    // Priority Queue (Heap)
    std::cout << "\nPriority Queue (Max Heap):\n";
    std::priority_queue<int> pq;
    pq.push(5);
    pq.push(1);
    pq.push(3);
    pq.push(7);
    pq.push(2);
    
    std::cout << "Priority Queue elements: ";
    while (!pq.empty()) {
        std::cout << pq.top() << " ";
        pq.pop();
    }
    std::cout << "\n";
    
    // ===== STL ALGORITHMS =====
    std::cout << "\n5. STL ALGORITHMS:\n\n";
    
    std::vector<int> data = {5, 2, 8, 1, 9, 3, 7, 4, 6};
    
    // Sorting
    std::cout << "Original: ";
    printContainer(data, "");
    
    std::sort(data.begin(), data.end());
    std::cout << "Sorted: ";
    printContainer(data, "");
    
    // Binary search
    bool found = std::binary_search(data.begin(), data.end(), 5);
    std::cout << "Binary search for 5: " << (found ? "Found" : "Not found") << "\n";
    
    // Find
    auto it = std::find(data.begin(), data.end(), 7);
    if (it != data.end()) {
        std::cout << "Found 7 at position: " << std::distance(data.begin(), it) << "\n";
    }
    
    // Count
    int count = std::count(data.begin(), data.end(), 3);
    std::cout << "Count of 3: " << count << "\n";
    
    // Accumulate (sum)
    int sum = std::accumulate(data.begin(), data.end(), 0);
    std::cout << "Sum of elements: " << sum << "\n";
    
    // Transform
    std::vector<int> squared(data.size());
    std::transform(data.begin(), data.end(), squared.begin(),
                   [](int x) { return x * x; });
    std::cout << "Squared: ";
    printContainer(squared, "");
    
    // Partition
    std::partition(data.begin(), data.end(), [](int x) { return x % 2 == 0; });
    std::cout << "Partitioned (even first): ";
    printContainer(data, "");
    
    // ===== ITERATORS =====
    std::cout << "\n6. ITERATORS:\n\n";
    
    std::vector<int> v = {10, 20, 30, 40, 50};
    
    // Different types of iterators
    std::cout << "Forward iteration: ";
    for (auto it = v.begin(); it != v.end(); ++it) {
        std::cout << *it << " ";
    }
    std::cout << "\n";
    
    std::cout << "Reverse iteration: ";
    for (auto rit = v.rbegin(); rit != v.rend(); ++rit) {
        std::cout << *rit << " ";
    }
    std::cout << "\n";
    
    // Iterator operations
    auto start = v.begin();
    auto middle = start + v.size() / 2;
    std::cout << "Middle element: " << *middle << "\n";
    
    // ===== LAMBDA WITH STL =====
    std::cout << "\n7. LAMBDA EXPRESSIONS WITH STL:\n\n";
    
    std::vector<int> nums = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    
    // Filter even numbers
    auto isEven = [](int n) { return n % 2 == 0; };
    
    std::cout << "Even numbers: ";
    std::copy_if(nums.begin(), nums.end(),
                 std::ostream_iterator<int>(std::cout, " "),
                 isEven);
    std::cout << "\n";
    
    // Custom sort with lambda
    std::vector<std::pair<std::string, int>> people = {
        {"Alice", 30},
        {"Bob", 25},
        {"Charlie", 35},
        {"David", 28}
    };
    
    std::sort(people.begin(), people.end(),
              [](const auto& a, const auto& b) {
                  return a.second < b.second;  // Sort by age
              });
    
    std::cout << "People sorted by age:\n";
    for (const auto& [name, age] : people) {
        std::cout << name << " (" << age << ") ";
    }
    std::cout << "\n";
    
    return 0;
}
```

---

## 🚀 Modern C++ Features (C++11/14/17/20)

### Fitur-Fitur Modern yang Mengubah Cara Kita Menulis C++

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <optional>      // C++17
#include <variant>       // C++17
#include <any>          // C++17
#include <tuple>
#include <functional>
#include <thread>
#include <mutex>
#include <future>
#include <chrono>
#include <filesystem>    // C++17
#include <span>         // C++20
#include <ranges>       // C++20
#include <concepts>     // C++20

// ===== C++11 FEATURES =====

// 1. Auto and decltype
auto getNumber() -> int {  // Trailing return type
    return 42;
}

// 2. Range-based for loop (shown earlier)

// 3. Lambda expressions
auto createMultiplier(int factor) {
    return [factor](int x) { return x * factor; };
}

// 4. Move semantics
class Resource {
private:
    int* data;
    size_t size;
    
public:
    // Constructor
    Resource(size_t s) : size(s), data(new int[s]) {
        std::cout << "Resource constructed\n";
    }
    
    // Destructor
    ~Resource() {
        delete[] data;
        std::cout << "Resource destroyed\n";
    }
    
    // Copy constructor
    Resource(const Resource& other) : size(other.size), data(new int[size]) {
        std::copy(other.data, other.data + size, data);
        std::cout << "Resource copied\n";
    }
    
    // Move constructor
    Resource(Resource&& other) noexcept : size(other.size), data(other.data) {
        other.data = nullptr;
        other.size = 0;
        std::cout << "Resource moved\n";
    }
    
    // Copy assignment
    Resource& operator=(const Resource& other) {
        if (this != &other) {
            delete[] data;
            size = other.size;
            data = new int[size];
            std::copy(other.data, other.data + size, data);
        }
        return *this;
    }
    
    // Move assignment
    Resource& operator=(Resource&& other) noexcept {
        if (this != &other) {
            delete[] data;
            size = other.size;
            data = other.data;
            other.data = nullptr;
            other.size = 0;
        }
        return *this;
    }
};

// 5. Variadic templates
template<typename... Args>
void print(Args... args) {
    ((std::cout << args << " "), ...);  // C++17 fold expression
    std::cout << "\n";
}

// ===== C++14 FEATURES =====

// 1. Generic lambdas
auto genericLambda = [](auto x, auto y) {
    return x + y;
};

// 2. Return type deduction
auto multiply(int x, int y) {  // Return type deduced
    return x * y;
}

// ===== C++17 FEATURES =====

// 1. Structured bindings (shown earlier)

// 2. If/switch with initializer
void processValue(int x) {
    if (auto result = x * 2; result > 10) {
        std::cout << "Result > 10: " << result << "\n";
    }
}

// 3. Optional
std::optional<int> divide(int a, int b) {
    if (b == 0) return std::nullopt;
    return a / b;
}

// 4. Variant
using VarType = std::variant<int, double, std::string>;

void processVariant(const VarType& v) {
    std::visit([](const auto& value) {
        std::cout << "Variant value: " << value << "\n";
    }, v);
}

// ===== C++20 FEATURES =====

// 1. Concepts
template<typename T>
concept Numeric = std::is_arithmetic_v<T>;

template<Numeric T>
T add(T a, T b) {
    return a + b;
}

// 2. Coroutines (simplified example)
// Note: Full coroutine implementation requires more setup

// 3. Ranges
void demonstrateRanges() {
    std::vector<int> numbers = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    
    // Filter and transform using ranges
    auto result = numbers 
        | std::views::filter([](int n) { return n % 2 == 0; })
        | std::views::transform([](int n) { return n * n; });
    
    std::cout << "Filtered and squared even numbers: ";
    for (int n : result) {
        std::cout << n << " ";
    }
    std::cout << "\n";
}

// ===== CONCURRENCY =====
void threadFunction(int id) {
    std::this_thread::sleep_for(std::chrono::milliseconds(100 * id));
    std::cout << "Thread " << id << " completed\n";
}

int main() {
    std::cout << "=== MODERN C++ FEATURES ===\n\n";
    
    // C++11 Features
    std::cout << "C++11 FEATURES:\n";
    
    // Auto and decltype
    auto value = getNumber();
    decltype(value) another = 100;
    std::cout << "Auto value: " << value << ", Decltype: " << another << "\n";
    
    // Lambda
    auto times3 = createMultiplier(3);
    std::cout << "5 * 3 = " << times3(5) << "\n";
    
    // Move semantics
    {
        Resource r1(1000);
        Resource r2 = std::move(r1);  // Move, not copy
    }
    
    // Variadic templates
    print("Hello", 42, 3.14, 'A');
    
    // C++14 Features
    std::cout << "\nC++14 FEATURES:\n";
    std::cout << "Generic lambda: 5 + 3.14 = " << genericLambda(5, 3.14) << "\n";
    
    // C++17 Features
    std::cout << "\nC++17 FEATURES:\n";
    
    // Optional
    auto result = divide(10, 2);
    if (result.has_value()) {
        std::cout << "10 / 2 = " << result.value() << "\n";
    }
    
    auto invalid = divide(10, 0);
    std::cout << "10 / 0 = " << invalid.value_or(-1) << " (default)\n";
    
    // Variant
    VarType v1 = 42;
    VarType v2 = 3.14;
    VarType v3 = "Hello";
    processVariant(v1);
    processVariant(v2);
    processVariant(v3);
    
    // Filesystem
    namespace fs = std::filesystem;
    fs::path currentPath = fs::current_path();
    std::cout << "Current path: " << currentPath << "\n";
    
    // C++20 Features
    std::cout << "\nC++20 FEATURES:\n";
    
    // Concepts
    std::cout << "Using concept: 5 + 3 = " << add(5, 3) << "\n";
    
    // Ranges
    demonstrateRanges();
    
    // Threading
    std::cout << "\nCONCURRENCY:\n";
    std::vector<std::thread> threads;
    
    for (int i = 1; i <= 3; ++i) {
        threads.emplace_back(threadFunction, i);
    }
    
    for (auto& t : threads) {
        t.join();
    }
    
    // Async operations
    auto future = std::async(std::launch::async, []() {
        std::this_thread::sleep_for(std::chrono::seconds(1));
        return 42;
    });
    
    std::cout << "Async result: " << future.get() << "\n";
    
    return 0;
}