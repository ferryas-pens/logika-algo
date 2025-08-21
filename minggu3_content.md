# MINGGU 3: FLOWCHART & PSEUDOCODE
## Mata Kuliah: Logika dan Algoritma Pemrograman

---

## **TUJUAN PEMBELAJARAN**

Setelah mengikuti pembelajaran pada minggu ini, mahasiswa diharapkan dapat:

1. **Memahami sejarah dan standar simbol flowchart** termasuk standar ISO untuk flowchart
2. **Membedakan jenis-jenis flowchart** (process, decision, data flow) dan penggunaannya
3. **Membuat pseudocode** sebagai representasi algoritma yang mudah dipahami
4. **Menggunakan draw.io** untuk membuat flowchart dengan professional
5. **Mengkonversi algoritma** ke dalam bentuk flowchart dan pseudocode dengan benar

---

## **BAGIAN 1: SEJARAH DAN STANDAR FLOWCHART**

### **1.1 Sejarah Perkembangan Flowchart**

Flowchart adalah representasi visual dari langkah-langkah dalam suatu proses atau algoritma. Konsep ini pertama kali dikembangkan pada awal abad ke-20 dan telah menjadi alat standar dalam berbagai industri.

#### **Timeline Perkembangan Flowchart:**

**1920s - Awal Mula:**
- **Frank Gilbreth** memperkenalkan "flow process charts" untuk menganalisis industrial processes
- Fokus pada efficiency dan optimization dalam manufacturing
- Menggunakan simbol sederhana untuk merepresentasikan steps dalam production process

**1940s - Standardisasi Awal:**
- **ASME (American Society of Mechanical Engineers)** mengembangkan standar simbol pertama
- Introduction of basic symbols: oval, rectangle, diamond
- Mulai digunakan secara luas dalam industrial engineering

**1960s - Era Komputer:**
- Flowchart mulai digunakan untuk memrepresentasikan computer programs
- **IBM** memperkenalkan flowcharting templates dan standards
- Integration dengan software development lifecycle

**1970s-1980s - Standarisasi Internasional:**
- **ISO 5807** (1985): International standard untuk flowchart symbols
- **ANSI (American National Standards Institute)** mengeluarkan guidelines
- **DIN (Deutsche Industrienorm)** standards untuk German-speaking countries

**1990s-2000s - Digital Revolution:**
- Microsoft Visio dan software flowcharting lainnya
- Integration dengan CASE (Computer-Aided Software Engineering) tools
- Web-based flowcharting tools

**2010s-Present - Modern Era:**
- **Cloud-based tools**: draw.io, Lucidchart, Miro
- **Collaborative features**: real-time editing, version control
- **AI-assisted diagramming**: automatic layout, smart suggestions

### **1.2 Standar ISO 5807 untuk Flowchart**

ISO 5807 adalah standar internasional yang mendefinisikan simbol-simbol yang digunakan dalam flowchart untuk dokumentasi sistem informasi.

#### **Kategori Simbol dalam ISO 5807:**

**1. Basic Symbols (Simbol Dasar):**
- **Process Symbol**: Persegi panjang untuk operasi/proses
- **Decision Symbol**: Belah ketupat untuk decision points
- **Terminator Symbol**: Oval untuk start/end points
- **Flow Lines**: Panah untuk menunjukkan alur

**2. Specialized Symbols (Simbol Khusus):**
- **Input/Output**: Parallelogram untuk data I/O
- **Predefined Process**: Persegi panjang dengan garis vertikal
- **Document**: Rectangle dengan bottom wavy line
- **Storage**: Cylinder untuk data storage

**3. Advanced Symbols (Simbol Lanjutan):**
- **Connector**: Circle untuk menghubungkan parts
- **Subroutine**: Rectangle dengan double vertical lines
- **Manual Operation**: Trapezoid untuk manual processes
- **Display**: Rectangle dengan curved right side

#### **Guidelines ISO 5807:**

**Flow Direction:**
- Default flow: top to bottom, left to right
- Use arrows hanya jika flow tidak mengikuti default direction
- Avoid crossing flow lines jika memungkinkan

**Labeling:**
- Use meaningful, concise labels
- Verbs untuk process boxes
- Questions untuk decision diamonds
- Clear start/end indicators

**Layout Principles:**
- Maintain consistent spacing
- Align shapes properly
- Use consistent text formatting
- Keep diagrams readable dan tidak terlalu complex

### **1.3 Flowchart dalam Berbagai Industri**

#### **Software Development:**
- **System design**: High-level architecture flowcharts
- **Algorithm documentation**: Detailed process flows
- **User experience**: User journey mapping
- **Debugging**: Error handling flowcharts

**Contoh: Software Bug Fix Process**
```
Start → Receive Bug Report → Reproduce Bug? 
         ↓ Yes                    ↓ No
    Identify Root Cause → Request More Info
         ↓                       ↓
    Develop Fix          → Return to Start
         ↓
    Test Fix → Fix Works?
         ↓ Yes    ↓ No
    Deploy → Rollback & Debug
         ↓
    End
```

#### **Business Process Management:**
- **Workflow optimization**: Identifying bottlenecks
- **Quality assurance**: Process standardization
- **Training materials**: Step-by-step procedures
- **Compliance**: Audit trails dan documentation

#### **Healthcare:**
- **Clinical pathways**: Patient treatment protocols
- **Emergency procedures**: Crisis response workflows
- **Quality improvement**: Process analysis
- **Medical device operations**: Usage instructions

#### **Education:**
- **Learning pathways**: Curriculum design
- **Problem-solving**: Breaking down complex concepts
- **Assessment design**: Evaluation processes
- **Administrative procedures**: Student services workflows

---

## **BAGIAN 2: JENIS-JENIS FLOWCHART**

### **2.1 Process Flowchart**

Process flowchart adalah jenis flowchart yang paling umum digunakan, menggambarkan langkah-langkah sequential dalam suatu proses dari awal hingga akhir.

#### **Karakteristik Process Flowchart:**
- **Linear flow**: Mengikuti urutan logis step-by-step
- **Single purpose**: Fokus pada satu proses utama
- **Clear start/end**: Defined beginning dan termination points
- **Action-oriented**: Emphasis pada what needs to be done

#### **Komponen Utama:**

**1. Start/End Terminals:**
```
(START) → Process begins here
  ↓
[Process Steps]
  ↓
(END) → Process terminates here
```

**2. Process Blocks:**
```
┌─────────────────┐
│ Calculate Total │  ← Action/Operation
│ Price           │
└─────────────────┘
```

**3. Decision Points:**
```
    ┌─────────────┐
   ╱ Is Price >   ╲  Yes → [Apply Discount]
  ╱  $100?        ╲
  ╲               ╱
   ╲─────────────╱
         │ No
         ↓
   [Continue Process]
```

#### **Contoh Lengkap: Process Flowchart untuk Online Shopping**
```
(START: Customer visits website)
         ↓
┌─────────────────────┐
│ Browse Products     │
└─────────────────────┘
         ↓
    ┌─────────────┐
   ╱ Item Found?  ╲ No → [Search for Item] → (Return to Browse)
  ╱              ╲
  ╲              ╱
   ╲─────────────╱
         │ Yes
         ↓
┌─────────────────────┐
│ Add Item to Cart    │
└─────────────────────┘
         ↓
    ┌─────────────┐
   ╱ Continue     ╲ Yes → (Return to Browse)
  ╱ Shopping?     ╲
  ╲              ╱
   ╲─────────────╱
         │ No
         ↓
┌─────────────────────┐
│ Proceed to Checkout │
└─────────────────────┘
         ↓
┌─────────────────────┐
│ Enter Payment Info  │
└─────────────────────┘
         ↓
    ┌─────────────┐
   ╱ Payment      ╲ No → [Show Error Message] → (Return to Payment)
  ╱ Successful?   ╲
  ╲              ╱
   ╲─────────────╱
         │ Yes
         ↓
┌─────────────────────┐
│ Send Confirmation   │
│ Email               │
└─────────────────────┘
         ↓
(END: Order Complete)
```

### **2.2 Decision Flowchart**

Decision flowchart fokus pada decision-making processes dan branching logic. Jenis ini sangat berguna untuk complex conditional scenarios.

#### **Karakteristik Decision Flowchart:**
- **Multiple branches**: Various paths berdasarkan conditions
- **Complex logic**: Nested decisions dan multiple conditions
- **Conditional outcomes**: Different results berdasarkan inputs
- **Decision trees**: Hierarchical decision structure

#### **Jenis Decision Structures:**

**1. Simple Binary Decision:**
```
    ┌─────────────┐
   ╱ Condition?   ╲ TRUE → [Action A]
  ╱              ╲
  ╲              ╱
   ╲─────────────╱
         │ FALSE
         ↓
    [Action B]
```

**2. Multiple Choice Decision:**
```
    ┌─────────────┐
   ╱ Select       ╲
  ╱ Option?       ╲
  ╲              ╱
   ╲─────────────╱
    ┌─────┼─────┐
Option A │ Option B │ Option C
    ↓     ↓      ↓
[Action A][Action B][Action C]
```

**3. Nested Decisions:**
```
    ┌─────────────┐
   ╱ Primary      ╲ YES
  ╱ Condition?    ╲ ──→ ┌─────────────┐
  ╲              ╱      ╱ Secondary   ╲ YES → [Final Action A]
   ╲─────────────╱      ╱ Condition?  ╲
         │ NO            ╲            ╱
         ↓                ╲───────────╱
    [Alternative]               │ NO
                               ↓
                          [Final Action B]
```

#### **Contoh Lengkap: Student Grading System Decision Flowchart**
```
(START: Input Student Scores)
         ↓
┌─────────────────────┐
│ Read: Assignment,   │
│ Midterm, Final      │
└─────────────────────┘
         ↓
┌─────────────────────┐
│ Calculate Weighted  │
│ Average             │
└─────────────────────┘
         ↓
    ┌─────────────┐
   ╱ Average ≥ 90 ╲ YES → ┌─────────────┐
  ╱              ╲       │ Assign      │
  ╲              ╱       │ Grade 'A'   │
   ╲─────────────╱       └─────────────┘
         │ NO                   ↓
         ↓                [Record Grade]
    ┌─────────────┐             ↓
   ╱ Average ≥ 80 ╲ YES → ┌─────────────┐
  ╱              ╲       │ Assign      │
  ╲              ╱       │ Grade 'B'   │
   ╲─────────────╱       └─────────────┘
         │ NO                   ↓
         ↓                [Record Grade]
    ┌─────────────┐             ↓
   ╱ Average ≥ 70 ╲ YES → ┌─────────────┐
  ╱              ╲       │ Assign      │
  ╲              ╱       │ Grade 'C'   │
   ╲─────────────╱       └─────────────┘
         │ NO                   ↓
         ↓                [Record Grade]
    ┌─────────────┐             ↓
   ╱ Average ≥ 60 ╲ YES → ┌─────────────┐
  ╱              ╲       │ Assign      │
  ╲              ╱       │ Grade 'D'   │
   ╲─────────────╱       └─────────────┘
         │ NO                   ↓
         ↓                [Record Grade]
┌─────────────────────┐           ↓
│ Assign Grade 'F'    │     ┌─────────────┐
└─────────────────────┘     ╱ Grade < C?  ╲ YES
         ↓                 ╱              ╲ ──→ ┌─────────────┐
   [Record Grade]         ╲              ╱      │ Recommend   │
         ↓                 ╲─────────────╱      │ Remedial    │
         ↓                       │ NO           └─────────────┘
         ↓                       ↓                     ↓
         └─────→ (END: Grade Processing Complete) ←─────┘
```

### **2.3 Data Flow Diagram (DFD)**

Data Flow Diagram adalah specialized flowchart yang menggambarkan aliran data melalui suatu sistem, menunjukkan bagaimana data diinput, diproses, disimpan, dan dioutput.

#### **Komponen Utama DFD:**

**1. External Entities (Entitas Eksternal):**
```
┌─────────────┐
│ Customer    │  ← Sumber atau tujuan data di luar sistem
└─────────────┘
```

**2. Processes (Proses):**
```
    ╭─────────╮
   ╱  Process  ╲  ← Transformasi data
  ╱     1.0     ╲
  ╲ Validate    ╱
   ╲  Order    ╱
    ╰─────────╯
```

**3. Data Stores (Penyimpanan Data):**
```
│ D1 │ Customer Database │  ← Tempat penyimpanan data
```

**4. Data Flows (Aliran Data):**
```
Order Details ───→  ← Menunjukkan aliran data dengan label
```

#### **Level DFD:**

**Level 0 (Context Diagram):**
- Menunjukkan sistem secara keseluruhan
- Single process dengan external entities
- High-level view of system boundaries

**Level 1 (DFD Level 1):**
- Decomposition of context diagram
- Major processes dalam sistem
- Primary data flows between processes

**Level 2+ (Detailed DFD):**
- Further decomposition of Level 1 processes
- Detailed internal processes
- Specific data transformations

#### **Contoh: Library Management System DFD Level 1**
```
┌─────────────┐     Book Request     ╭─────────────╮
│  Library    │ ─────────────────→  ╱    1.0       ╲
│  Member     │                    ╱  Process Book  ╲
│             │ ←─────────────────  ╲   Request     ╱
└─────────────┘   Book Details      ╲              ╱
                                     ╰──────┬──────╯
                                           │ Member Info
                                           ↓
                                    │ D1 │ Member Database │
                                           ↑
                                           │ Book Info
                        ╭─────────────╮    │
                       ╱    2.0       ╲   │
                      ╱  Manage Book  ╲ ──┘
                     ╱   Inventory    ╱
                     ╲              ╱
                      ╲─────────────╱
                            │
                            ↓
                     │ D2 │ Book Database │
                            ↑
              Book Updates  │
                            │
┌─────────────┐            │
│ Librarian   │ ───────────┘
└─────────────┘
```

---

## **BAGIAN 3: PSEUDOCODE SEBAGAI REPRESENTASI ALGORITMA**

### **3.1 Definisi dan Konsep Pseudocode**

Pseudocode adalah deskripsi langkah-langkah dalam algoritma yang menggunakan campuran konvensi bahasa pemrograman dengan notasi informal yang biasanya self-explanatory.

#### **Karakteristik Pseudocode:**

**1. Human-Readable:**
- Menggunakan bahasa natural yang mudah dipahami
- Tidak terikat syntax programming language tertentu
- Focus pada logic rather than implementation details

**2. Structured:**
- Menggunakan control structures: sequence, selection, iteration
- Indentation untuk menunjukkan hierarchy
- Clear flow of execution

**3. Algorithm-Focused:**
- Emphasis pada problem-solving approach
- Abstract dari programming language specifics
- Bridge between algorithm design dan implementation

#### **Keuntungan Menggunakan Pseudocode:**

**1. Language Independence:**
- Dapat diimplementasikan dalam bahasa pemrograman apapun
- Tidak terikat pada syntax rules tertentu
- Universal understanding across programmers

**2. Easier Communication:**
- Dapat dipahami oleh non-programmers
- Effective untuk team collaboration
- Good documentation tool

**3. Focus on Logic:**
- Eliminates distraction dari syntax errors
- Concentrates pada algorithm correctness
- Easier to debug logical issues

**4. Rapid Prototyping:**
- Quick to write dan modify
- Easy to iterate on design
- Supports top-down design approach

### **3.2 Struktur dan Konvensi Pseudocode**

#### **Core Programming Constructs dalam Pseudocode:**

Pseudocode dapat merepresentasikan enam programming constructs utama (selalu ditulis dalam UPPERCASE):

**1. SEQUENCE:**
Represents linear tasks performed sequentially one after another.
```
BEGIN
  DECLARE variables
  READ input
  PROCESS data
  WRITE output
END
```

**2. IF-THEN-ELSE:**
Conditional statement yang mengubah flow algoritma.
```
IF condition THEN
  action_if_true
ELSE
  action_if_false
ENDIF
```

**3. WHILE:**
Loop dengan kondisi di awal.
```
WHILE condition DO
  action_to_repeat
ENDWHILE
```

**4. REPEAT-UNTIL:**
Loop dengan kondisi di akhir.
```
REPEAT
  action_to_repeat
UNTIL condition
```

**5. FOR:**
Counted loop untuk iterasi tertentu.
```
FOR counter = start TO end STEP increment DO
  action_to_repeat
ENDFOR
```

**6. CASE:**
Generalization dari IF-THEN-ELSE untuk multiple conditions.
```
CASE variable OF
  value1: action1
  value2: action2
  DEFAULT: default_action
ENDCASE
```

#### **Extended Constructs:**

**7. CALL (Function/Procedure Invocation):**
```
CALL function_name(parameters)
result = FUNCTION function_name(parameters)
```

**8. EXCEPTION (Error Handling):**
```
TRY
  risky_operation
CATCH exception_type
  handle_error
ENDTRY
```

#### **Konvensi Penulisan Pseudocode:**

**1. Naming Conventions:**
- **Variables**: descriptive_lowercase_with_underscores
- **Constants**: UPPERCASE_WITH_UNDERSCORES
- **Functions**: CamelCase atau descriptive_names

**2. Indentation:**
- Use consistent indentation (2 or 4 spaces)
- Nest related blocks properly
- Align similar level statements

**3. Comments:**
- Use // untuk single line comments
- Use /* */ untuk multi-line comments
- Explain complex logic atau business rules

**4. Keywords:**
- Reserved words dalam UPPERCASE: IF, THEN, ELSE, WHILE, FOR
- Operators dalam mixed case: AND, OR, NOT, MOD
- Built-in functions: READ, WRITE, PRINT, INPUT

### **3.3 Contoh Pseudocode untuk Berbagai Algoritma**

#### **Contoh 1: Linear Search Algorithm**
```
ALGORITHM Linear_Search
INPUT: array[], n, search_key
OUTPUT: index of search_key or -1 if not found

BEGIN
  // Initialize variables
  found_index = -1
  
  // Search through array
  FOR i = 0 TO n-1 DO
    IF array[i] = search_key THEN
      found_index = i
      BREAK  // Exit loop early when found
    ENDIF
  ENDFOR
  
  RETURN found_index
END
```

#### **Contoh 2: Bubble Sort Algorithm**
```
ALGORITHM Bubble_Sort
INPUT: array[], n
OUTPUT: sorted array in ascending order

BEGIN
  // Outer loop for number of passes
  FOR i = 0 TO n-2 DO
    swapped = FALSE
    
    // Inner loop for comparisons in each pass
    FOR j = 0 TO n-i-2 DO
      IF array[j] > array[j+1] THEN
        // Swap elements
        temp = array[j]
        array[j] = array[j+1]
        array[j+1] = temp
        swapped = TRUE
      ENDIF
    ENDFOR
    
    // If no swapping occurred, array is sorted
    IF swapped = FALSE THEN
      BREAK
    ENDIF
  ENDFOR
  
  RETURN array
END
```

#### **Contoh 3: Factorial Calculation (Recursive)**
```
ALGORITHM Factorial_Recursive
INPUT: n (non-negative integer)
OUTPUT: factorial of n

BEGIN
  IF n = 0 OR n = 1 THEN
    RETURN 1
  ELSE
    RETURN n * Factorial_Recursive(n-1)
  ENDIF
END
```

#### **Contoh 4: Complex Business Logic - Bank ATM Withdrawal**
```
ALGORITHM ATM_Withdrawal
INPUT: account_number, pin, withdrawal_amount
OUTPUT: success/failure message, updated_balance

BEGIN
  // Validate account and PIN
  IF NOT Validate_Account(account_number, pin) THEN
    PRINT "Invalid account or PIN"
    RETURN "FAILURE"
  ENDIF
  
  // Get current balance
  current_balance = Get_Balance(account_number)
  
  // Check withdrawal limits and balance
  daily_limit = Get_Daily_Limit(account_number)
  daily_withdrawn = Get_Daily_Withdrawn(account_number)
  
  IF withdrawal_amount > (daily_limit - daily_withdrawn) THEN
    PRINT "Daily withdrawal limit exceeded"
    RETURN "FAILURE"
  ENDIF
  
  IF withdrawal_amount > current_balance THEN
    PRINT "Insufficient funds"
    RETURN "FAILURE"
  ENDIF
  
  // Check if amount is valid denomination
  IF NOT Valid_Denomination(withdrawal_amount) THEN
    PRINT "Amount must be in multiples of $10"
    RETURN "FAILURE"
  ENDIF
  
  // Process withdrawal
  TRY
    new_balance = current_balance - withdrawal_amount
    Update_Balance(account_number, new_balance)
    Update_Daily_Withdrawn(account_number, withdrawal_amount)
    Dispense_Cash(withdrawal_amount)
    Print_Receipt(account_number, withdrawal_amount, new_balance)
    
    PRINT "Transaction successful"
    PRINT "New balance: $", new_balance
    RETURN "SUCCESS"
    
  CATCH database_error
    PRINT "Transaction failed. Please try again."
    RETURN "FAILURE"
  ENDTRY
END

// Supporting functions
FUNCTION Validate_Account(account_number, pin)
  stored_pin = Get_Stored_PIN(account_number)
  account_active = Check_Account_Status(account_number)
  RETURN (stored_pin = pin) AND account_active
ENDFUNCTION

FUNCTION Valid_Denomination(amount)
  RETURN (amount MOD 10 = 0) AND (amount > 0)
ENDFUNCTION
```

---

## **BAGIAN 4: PRAKTIK MEMBUAT FLOWCHART DENGAN DRAW.IO**

### **4.1 Pengenalan Draw.io**

Draw.io (sekarang diagrams.net) adalah free, open-source web-based diagramming application yang memungkinkan users untuk membuat, edit, dan collaborate pada berbagai jenis diagrams dan flowcharts.

#### **Keunggulan Draw.io:**

**1. Accessibility:**
- **Web-based**: Tidak perlu installation, akses langsung via browser
- **Cross-platform**: Bekerja di Windows, Mac, Linux
- **Mobile support**: Responsive design untuk tablet dan smartphone

**2. Features:**
- **Extensive shape libraries**: Flowcharts, UML, network diagrams, ERD
- **Professional templates**: Pre-built diagrams untuk quick start
- **Collaboration**: Real-time editing dan sharing capabilities
- **Export options**: PNG, JPEG, SVG, PDF, XML formats

**3. Integration:**
- **Cloud storage**: Google Drive, OneDrive, Dropbox integration
- **Confluence**: Seamless integration untuk documentation
- **GitHub**: Version control untuk diagrams
- **Embed capabilities**: HTML embedding untuk websites

**4. Cost:**
- **Completely free**: No subscription atau licensing fees
- **Open source**: Source code available on GitHub
- **No account required**: Optional registration untuk cloud features

### **4.2 Getting Started dengan Draw.io**

#### **Step 1: Accessing Draw.io**
1. Open browser dan navigate ke **https://app.diagrams.net**
2. Click **"Create New Diagram"**
3. Choose **"Blank Diagram"** atau select dari template library
4. Enter filename dan click **"Create"**

#### **Step 2: Interface Overview**

**Main Components:**
- **Drawing Canvas**: Central area untuk creating diagrams
- **Shape Libraries**: Left panel dengan various shape categories
- **Toolbar**: Top bar dengan common tools dan formatting options
- **Format Panel**: Right panel untuk styling shapes dan text
- **Menu Bar**: File operations, edit functions, view options

**Shape Libraries yang Relevant:**
- **General**: Basic shapes (rectangles, circles, arrows)
- **Flowchart**: Specialized flowchart symbols
- **Basic**: Additional geometric shapes
- **Arrows**: Various arrow styles dan connectors

#### **Step 3: Adding Shapes to Canvas**

**Method 1: Click to Add**
- Click pada shape dalam library
- Shape akan automatically appear pada canvas
- Drag untuk repositioning

**Method 2: Drag and Drop**
- Drag shape dari library ke specific position
- More precise placement
- Useful untuk complex layouts

**Method 3: Smart Shapes**
- Hover over existing shape untuk show direction arrows
- Click direction arrow untuk automatically add connected shape
- Maintains alignment dan spacing

#### **Step 4: Connecting Shapes**

**Floating Connectors:**
```
1. Hover over source shape until direction arrows appear
2. Drag dari direction arrow ke target shape
3. Release ketika target shape outline turns blue
4. Connector akan automatically route optimal path
```

**Fixed Connectors:**
```
1. Hover over source shape untuk show connection points (small crosses)
2. Drag dari specific connection point
3. Connect ke specific connection point pada target shape
4. Connector akan stay fixed to those exact points
```

**Connector Labels:**
- Double-click pada connector untuk add label
- Position labels menggunakan yellow diamond handle
- Multiple labels per connector (source, middle, target)

### **4.3 Hands-on Workshop: Membuat Flowchart Lengkap**

Mari kita buat flowchart untuk **"Student Registration System"** step by step.

#### **Scenario:**
Sistem pendaftaran mahasiswa baru dengan validation, document verification, dan fee payment.

#### **Step-by-Step Creation:**

**Step 1: Setup Canvas**
```
1. Open draw.io
2. Create new blank diagram
3. Filename: "Student_Registration_Flowchart"
4. Enable Flowchart shape library
```

**Step 2: Add Start Terminal**
```
1. Dari Flowchart library, select Oval shape
2. Place pada top-center of canvas
3. Double-click untuk edit text: "START"
4. Format: Center alignment, bold text
```

**Step 3: Build Main Flow**
```
(START)
   ↓
┌─────────────────────┐
│ Student Submits     │
│ Application Form    │
└─────────────────────┘
   ↓
    ┌─────────────┐
   ╱ Form         ╲ No → ┌─────────────────────┐
  ╱ Complete?     ╲      │ Display Validation  │
  ╲              ╱      │ Errors              │
   ╲─────────────╱       └─────────────────────┘
         │ Yes                     ↓
         ↓                    [Return to Form]
┌─────────────────────┐
│ Upload Required     │
│ Documents           │
└─────────────────────┘
   ↓
    ┌─────────────┐
   ╱ Documents    ╲ No → ┌─────────────────────┐
  ╱ Valid?        ╲      │ Request Missing/    │
  ╲              ╱      │ Correct Documents   │
   ╲─────────────╱       └─────────────────────┘
         │ Yes                     ↓
         ↓                    [Return to Upload]
┌─────────────────────┐
│ Calculate           │
│ Registration Fees   │
└─────────────────────┘
   ↓
┌─────────────────────┐
│ Display Fee         │
│ Information         │
└─────────────────────┘
   ↓
    ┌─────────────┐
   ╱ Payment      ╲ Online → ┌─────────────────────┐
  ╱ Method?       ╲         │ Process Online      │
  ╲              ╱         │ Payment             │
   ╲─────────────╱          └─────────────────────┘
         │ Bank Transfer             ↓
         ↓                    ┌─────────────┐
┌─────────────────────┐      ╱ Payment     ╲ No → ┌─────────────────────┐
│ Generate Bank       │     ╱ Successful?  ╲      │ Display Payment     │
│ Transfer Details    │     ╲              ╱      │ Error Message       │
└─────────────────────┘      ╲─────────────╱       └─────────────────────┘
   ↓                               │ Yes                   ↓
┌─────────────────────┐            ↓              [Return to Payment Method]
│ Wait for Payment    │    ┌─────────────────────┐
│ Confirmation        │    │ Generate Student    │
└─────────────────────┘    │ ID & Password       │
   ↓                       └─────────────────────┘
    ┌─────────────┐                 ↓
   ╱ Payment      ╲ No → [Return to Wait]
  ╱ Received?     ╲                 ↓
  ╲              ╱        ┌─────────────────────┐
   ╲─────────────╱        │ Send Welcome Email  │
         │ Yes            │ with Login Details  │
         ↓                └─────────────────────┘
         │                         ↓
         └────────────────────────→ │
                                   ↓
                          ┌─────────────────────┐
                          │ Update Database:    │
                          │ Registration Status │
                          │ = "CONFIRMED"       │
                          └─────────────────────┘
                                   ↓
                               (END)
```

#### **Step 4: Advanced Formatting Techniques**

**Color Coding untuk Better Visualization:**
```
Process Blocks (Rectangles): Light Blue (#E3F2FD)
Decision Diamonds: Light Orange (#FFF3E0)
Start/End Ovals: Light Green (#E8F5E8)
Error Messages: Light Red (#FFEBEE)
Connectors: Dark Blue (#1976D2)
```

**Text Formatting:**
- **Font**: Arial atau Helvetica, 10-12pt
- **Process blocks**: Bold, center-aligned
- **Decision questions**: Regular weight, center-aligned with question marks
- **Yes/No labels**: Bold, positioned clearly pada connector

**Alignment dan Spacing:**
- Use grid snapping untuk consistent positioning
- Maintain equal spacing between levels
- Align related elements vertically
- Keep decision branches symmetrical

#### **Step 5: Adding Advanced Elements**

**Subprocess Reference:**
```
┌─────────────────────┐
│ ║ Validate Student ║ │  ← Double vertical lines indicate predefined process
│ ║ Documents        ║ │
└─────────────────────┘
```

**Document Output:**
```
┌─────────────────────┐
│ Print Registration  │  
│ Certificate         │
└─────────────────────┘
         ╲╱╲╱╲╱╲╱╲    ← Wavy bottom line indicates document
```

**Data Storage:**
```
    ╭─────────╮
   ╱           ╲       ← Cylinder shape for database/storage
  │  Student    │
  │  Database   │
   ╲           ╱
    ╰─────────╯
```

**Off-page Connector:**
```
    ╭─ A ─╮             ← Pentagon shape untuk connection to another page
   ╱       ╲
  │    1    │           Numbers atau letters untuk referencing
   ╲       ╱
    ╰─────╯
```

### **4.4 Best Practices untuk Professional Flowcharts**

#### **Design Principles:**

**1. Clarity dan Readability:**
- Keep text concise but descriptive
- Use consistent terminology throughout
- Avoid crossing lines whenever possible
- Maintain adequate white space

**2. Logical Flow:**
- Follow natural reading direction (top-to-bottom, left-to-right)
- Group related processes together
- Use consistent decision branching (Yes/True typically goes right atau down)
- Show clear entry dan exit points

**3. Visual Hierarchy:**
- Use different colors untuk different types of activities
- Size shapes consistently within categories
- Bold important decision points
- Highlight critical paths atau error conditions

**4. Standardization:**
- Follow ISO 5807 symbols when possible
- Use consistent naming conventions
- Maintain standard spacing dan alignment
- Document any custom symbols atau conventions used

#### **Common Mistakes to Avoid:**

**1. Overcomplicated Diagrams:**
```
❌ BAD: Single flowchart with 50+ symbols
✅ GOOD: Break into multiple pages atau use subprocess references
```

**2. Ambiguous Decision Points:**
```
❌ BAD: "Check data" (unclear what to check)
✅ GOOD: "Is age >= 18?" (specific, testable condition)
```

**3. Missing Flow Directions:**
```
❌ BAD: Lines without arrows when flow direction isn't obvious
✅ GOOD: Clear arrows showing process direction
```

**4. Inconsistent Symbols:**
```
❌ BAD: Using rectangles untuk both processes dan decisions
✅ GOOD: Diamonds untuk decisions, rectangles untuk processes
```

---

## **BAGIAN 5: INTEGRASI FLOWCHART DAN PSEUDOCODE**

### **5.1 Mengkonversi Algoritma ke Flowchart dan Pseudocode**

Kemampuan untuk mengkonversi algoritma antara different representations adalah skill penting dalam software development. Mari explore systematic approach untuk conversion.

#### **Three-Step Conversion Process:**

**Step 1: Identify Algorithm Components**
- Input requirements
- Output specifications  
- Processing steps
- Decision points
- Loop structures
- Function calls

**Step 2: Choose Appropriate Representation**
- **Flowchart**: Visual learners, process documentation, stakeholder communication
- **Pseudocode**: Logic validation, code planning, algorithm analysis
- **Natural Language**: Initial brainstorming, requirement gathering

**Step 3: Apply Conversion Rules**
- Map algorithm structures to symbols/syntax
- Maintain logical consistency
- Preserve all decision paths
- Include error handling

### **5.2 Comprehensive Example: Password Validation System**

Mari implement complete password validation system dalam semua three representations.

#### **Natural Language Algorithm:**
```
Password Validation Algorithm:
1. Read user input password
2. Check if password length is at least 8 characters
3. Check if password contains at least one uppercase letter
4. Check if password contains at least one lowercase letter  
5. Check if password contains at least one digit
6. Check if password contains at least one special character
7. If all criteria are met, password is valid
8. Otherwise, display specific error messages for failed criteria
9. Return validation result
```

#### **Detailed Pseudocode Version:**
```
ALGORITHM Password_Validation
INPUT: password_string
OUTPUT: validation_result, error_messages[]

BEGIN
  // Initialize variables
  is_valid = TRUE
  error_messages = []
  min_length = 8
  
  // Check length requirement
  IF LENGTH(password_string) < min_length THEN
    is_valid = FALSE
    ADD "Password must be at least 8 characters long" TO error_messages
  ENDIF
  
  // Check for uppercase letter
  has_uppercase = FALSE
  FOR each character IN password_string DO
    IF character >= 'A' AND character <= 'Z' THEN
      has_uppercase = TRUE
      BREAK
    ENDIF
  ENDFOR
  
  IF has_uppercase = FALSE THEN
    is_valid = FALSE
    ADD "Password must contain at least one uppercase letter" TO error_messages
  ENDIF
  
  // Check for lowercase letter
  has_lowercase = FALSE
  FOR each character IN password_string DO
    IF character >= 'a' AND character <= 'z' THEN
      has_lowercase = TRUE
      BREAK
    ENDIF
  ENDFOR
  
  IF has_lowercase = FALSE THEN
    is_valid = FALSE
    ADD "Password must contain at least one lowercase letter" TO error_messages
  ENDIF
  
  // Check for digit
  has_digit = FALSE
  FOR each character IN password_string DO
    IF character >= '0' AND character <= '9' THEN
      has_digit = TRUE
      BREAK
    ENDIF
  ENDFOR
  
  IF has_digit = FALSE THEN
    is_valid = FALSE
    ADD "Password must contain at least one digit" TO error_messages
  ENDIF
  
  // Check for special character
  has_special = FALSE
  special_chars = "!@#$%^&*()_+-=[]{}|;:,.<>?"
  FOR each character IN password_string DO
    IF character IN special_chars THEN
      has_special = TRUE
      BREAK
    ENDIF
  ENDFOR
  
  IF has_special = FALSE THEN
    is_valid = FALSE
    ADD "Password must contain at least one special character" TO error_messages
  ENDIF
  
  // Return results
  validation_result = is_valid
  RETURN validation_result, error_messages
END
```

#### **Flowchart Version:**
```
                    (START)
                       ↓
              ┌─────────────────────┐
              │ INPUT: password     │
              └─────────────────────┘
                       ↓
              ┌─────────────────────┐
              │ Initialize:         │
              │ is_valid = TRUE     │
              │ errors = []         │
              └─────────────────────┘
                       ↓
                ┌─────────────┐
               ╱ LENGTH(pwd)  ╲ No → ┌─────────────────────┐
              ╱ >= 8?         ╲      │ is_valid = FALSE    │
              ╲              ╱      │ ADD length error    │
               ╲─────────────╱       │ to errors[]         │
                     │ Yes           └─────────────────────┘
                     ↓                        ↓
                ┌─────────────┐               │
               ╱ Has          ╲ No ──────────┐│
              ╱ Uppercase?    ╲              ││
              ╲              ╱              ││
               ╲─────────────╱               ││
                     │ Yes                   ││
                     ↓                       ││
                ┌─────────────┐              ││
               ╱ Has          ╲ No ──────────┤│
              ╱ Lowercase?    ╲              ││
              ╲              ╱              ││
               ╲─────────────╱               ││
                     │ Yes                   ││
                     ↓                       ││
                ┌─────────────┐              ││
               ╱ Has Digit?   ╲ No ──────────┤│
              ╱              ╲              ││
              ╲              ╱              ││
               ╲─────────────╱               ││
                     │ Yes                   ││
                     ↓                       ││
                ┌─────────────┐              ││
               ╱ Has Special  ╲ No ──────────┤│
              ╱ Character?    ╲              ││
              ╲              ╱              ││
               ╲─────────────╱               ││
                     │ Yes                   ││
                     ↓                       ││
                     ↓←──────────────────────┤│
                     ↓←──────────────────────┘│
                     ↓←───────────────────────┘
                ┌─────────────┐
               ╱ is_valid =   ╲ No → ┌─────────────────────┐
              ╱ TRUE?         ╲      │ DISPLAY error       │
              ╲              ╱      │ messages            │
               ╲─────────────╱       └─────────────────────┘
                     │ Yes                   ↓
                     ↓                       │
              ┌─────────────────────┐        │
              │ DISPLAY "Password   │        │
              │ is valid"           │        │
              └─────────────────────┘        │
                     ↓                       │
                     ↓←──────────────────────┘
                   (END)
```

### **5.3 Advanced Flowchart Techniques**

#### **Multi-Page Flowcharts:**

Untuk complex systems, gunakan multi-page approach:

**Page 1: Main Process Flow**
```
(START: User Registration)
         ↓
┌─────────────────────┐
│ Collect User Info   │
└─────────────────────┘
         ↓
    ╭─────────╮
   ╱     A     ╲      ← Off-page connector
  │      1      │     ← Reference to Page 2
   ╲           ╱
    ╰─────────╯
```

**Page 2: Validation Subprocess**
```
    ╭─────────╮
   ╱     A     ╲      ← From Page 1
  │      1      │
   ╲           ╱
    ╰─────────╯
         ↓
┌─────────────────────┐
│ Validate Email      │
│ Format              │
└─────────────────────┘
         ↓
   [Validation Logic]
         ↓
    ╭─────────╮
   ╱     B     ╲      ← To Page 3 atau back to Page 1
  │      1      │
   ╲           ╱
    ╰─────────╯
```

#### **Parallel Processing Representation:**
```
┌─────────────────────┐
│ Initialize System   │
└─────────────────────┘
         ↓
    ┌────┴────┐
    ↓         ↓
┌─────────┐ ┌─────────┐
│Process A│ │Process B│  ← Parallel execution
└─────────┘ └─────────┘
    ↓         ↓
    └────┬────┘
         ↓
┌─────────────────────┐
│ Synchronize Results │
└─────────────────────┘
```

#### **Exception Handling dalam Flowcharts:**
```
┌─────────────────────┐
│ Risky Operation     │
└─────────────────────┘
         ↓
    ┌─────────────┐
   ╱ Operation    ╲ Success → [Continue Normal Flow]
  ╱ Successful?   ╲
  ╲              ╱
   ╲─────────────╱
         │ Exception
         ↓
┌─────────────────────┐
│ Handle Exception    │
└─────────────────────┘
         ↓
    ┌─────────────┐
   ╱ Can Recover? ╲ Yes → [Retry Operation]
  ╱              ╲
  ╲              ╱
   ╲─────────────╱
         │ No
         ↓
┌─────────────────────┐
│ Log Error &         │
│ Terminate Gracefully│
└─────────────────────┘
         ↓
       (END)
```

---

## **BAGIAN 6: STUDI KASUS KOMPLEKS**

### **6.1 E-Commerce Checkout Process**

Mari create comprehensive documentation untuk complex e-commerce checkout process menggunakan semua techniques yang telah dipelajari.

#### **Business Requirements:**
- Shopping cart validation
- User authentication
- Shipping calculation
- Payment processing
- Inventory management
- Order confirmation

#### **Pseudocode Implementation:**
```
ALGORITHM E_Commerce_Checkout
INPUT: user_session, cart_items[]
OUTPUT: order_confirmation, transaction_status

BEGIN
  // Phase 1: Cart Validation
  IF EMPTY(cart_items) THEN
    DISPLAY "Cart is empty"
    RETURN "CHECKOUT_FAILED"
  ENDIF
  
  total_amount = 0
  unavailable_items = []
  
  FOR each item IN cart_items DO
    current_stock = Get_Inventory(item.product_id)
    IF current_stock < item.quantity THEN
      ADD item TO unavailable_items
    ELSE
      item.price = Get_Current_Price(item.product_id)
      total_amount = total_amount + (item.price * item.quantity)
    ENDIF
  ENDFOR
  
  IF NOT EMPTY(unavailable_items) THEN
    DISPLAY "Some items are no longer available: " + unavailable_items
    RETURN "INVENTORY_INSUFFICIENT"
  ENDIF
  
  // Phase 2: User Authentication
  IF NOT Is_Logged_In(user_session) THEN
    auth_choice = PROMPT "Login atau Guest Checkout?"
    
    CASE auth_choice OF
      "LOGIN":
        credentials = Get_Login_Credentials()
        IF NOT Authenticate_User(credentials) THEN
          DISPLAY "Authentication failed"
          RETURN "AUTH_FAILED"
        ENDIF
        user_session = Create_User_Session(credentials.user_id)
        
      "GUEST":
        guest_info = Get_Guest_Information()
        IF NOT Validate_Guest_Info(guest_info) THEN
          DISPLAY "Invalid guest information"
          RETURN "GUEST_INFO_INVALID"
        ENDIF
        user_session = Create_Guest_Session(guest_info)
        
      DEFAULT:
        RETURN "CHECKOUT_CANCELLED"
    ENDCASE
  ENDIF
  
  // Phase 3: Shipping Information
  shipping_address = Get_Shipping_Address(user_session)
  IF EMPTY(shipping_address) THEN
    shipping_address = Prompt_New_Address()
    IF NOT Validate_Address(shipping_address) THEN
      DISPLAY "Invalid shipping address"
      RETURN "ADDRESS_INVALID"
    ENDIF
  ENDIF
  
  shipping_options = Get_Shipping_Options(shipping_address, cart_items)
  selected_shipping = Prompt_Shipping_Choice(shipping_options)
  shipping_cost = Calculate_Shipping_Cost(selected_shipping, total_amount)
  
  // Phase 4: Payment Processing
  total_with_shipping = total_amount + shipping_cost
  taxes = Calculate_Taxes(total_amount, shipping_address)
  final_total = total_with_shipping + taxes
  
  DISPLAY "Order Summary:"
  DISPLAY "Subtotal: $" + total_amount
  DISPLAY "Shipping: $" + shipping_cost  
  DISPLAY "Taxes: $" + taxes
  DISPLAY "Total: $" + final_total
  
  payment_method = Prompt_Payment_Method()
  
  CASE payment_method OF
    "CREDIT_CARD":
      card_info = Get_Credit_Card_Info()
      payment_result = Process_Credit_Card(card_info, final_total)
      
    "PAYPAL":
      payment_result = Process_PayPal_Payment(final_total)
      
    "BANK_TRANSFER":
      transfer_details = Generate_Bank_Transfer_Details(final_total)
      payment_result = "PENDING_TRANSFER"
      
    DEFAULT:
      RETURN "INVALID_PAYMENT_METHOD"
  ENDCASE
  
  // Phase 5: Order Finalization
  IF payment_result = "SUCCESS" OR payment_result = "PENDING_TRANSFER" THEN
    TRY
      // Reserve inventory
      FOR each item IN cart_items DO
        Reserve_Inventory(item.product_id, item.quantity)
      ENDFOR
      
      // Create order record
      order_id = Generate_Order_ID()
      order_details = {
        order_id: order_id,
        user_session: user_session,
        items: cart_items,
        shipping_address: shipping_address,
        payment_method: payment_method,
        total_amount: final_total,
        status: payment_result = "SUCCESS" ? "CONFIRMED" : "PENDING_PAYMENT"
      }
      
      Save_Order(order_details)
      
      // Send confirmations
      IF payment_result = "SUCCESS" THEN
        Send_Order_Confirmation_Email(order_details)
        Send_SMS_Notification(order_details)
        Clear_Shopping_Cart(user_session)
      ELSE
        Send_Payment_Instructions_Email(order_details, transfer_details)
      ENDIF
      
      RETURN "ORDER_PLACED_SUCCESSFULLY"
      
    CATCH database_error
      // Rollback operations
      FOR each item IN cart_items DO
        Release_Inventory_Reservation(item.product_id, item.quantity)
      ENDFOR
      
      IF payment_result = "SUCCESS" THEN
        Initiate_Payment_Refund(card_info, final_total)
      ENDIF
      
      DISPLAY "Order processing failed. Please try again."
      RETURN "SYSTEM_ERROR"
    ENDTRY
    
  ELSE
    DISPLAY "Payment failed: " + payment_result
    RETURN "PAYMENT_FAILED"
  ENDIF
END
```

#### **Corresponding Flowchart Structure:**

Due to complexity, kita akan create hierarchical flowchart dengan main process dan detailed subprocesses.

**Main Process Flowchart:**
```
(START: Begin Checkout)
         ↓
┌─────────────────────┐
│ Validate Shopping   │
│ Cart                │
└─────────────────────┘
         ↓
    ┌─────────────┐
   ╱ Cart Valid?  ╲ No → [Display Error] → (END)
  ╱              ╲
  ╲              ╱
   ╲─────────────╱
         │ Yes
         ↓
    ╭─────────╮
   ╱    A      ╲      ← To Authentication Subprocess
  │     1       │
   ╲           ╱
    ╰─────────╯

[Continue with similar structure for each major phase]
```

### **6.2 Problem-Solving Exercise: Academic Grading System**

#### **Challenge:**
Create complete documentation (natural language, pseudocode, dan flowchart) untuk comprehensive academic grading system dengan following features:

- Multiple assessment types (assignments, quizzes, exams)
- Weighted grading scheme
- Late penalty calculations
- Grade curve adjustments
- Academic standing determination
- Transcript generation

#### **Solution Framework:**

**Natural Language Algorithm:**
```
Academic Grading System Algorithm:

1. Input student enrollment dan course information
2. Configure grading scheme weights dan policies
3. For each assessment submission:
   a. Record submission timestamp
   b. Calculate late penalty jika applicable
   c. Score assessment based on rubric
   d. Apply any special conditions (extra credit, makeup exams)
4. Calculate weighted average based on category weights
5. Apply grade curve if enabled
6. Determine letter grade based on scale
7. Check academic standing (probation, honors, etc.)
8. Generate transcript entry
9. Send grade notification to student
10. Update academic records
```

**Key Components untuk Pseudocode:**
- Input validation functions
- Date/time calculations untuk late penalties
- Weighted average algorithms
- Grade curve mathematical functions
- Academic standing business rules
- Error handling untuk edge cases

**Flowchart Considerations:**
- Multi-page design dengan clear subprocess references
- Decision trees untuk complex grading policies
- Parallel processing untuk batch grade calculations
- Exception handling untuk system failures
- User interaction points untuk manual overrides

---

## **BAGIAN 7: LATIHAN DAN EVALUASI**

### **7.1 Hands-On Exercises**

#### **Exercise 1: Simple Decision Flowchart**
**Task:** Create flowchart untuk "Library Book Borrowing System"

**Requirements:**
- Check if user has library card
- Verify book availability
- Check borrowing limits
- Process loan atau denial
- Update records

**Deliverables:**
1. Hand-drawn sketch
2. Digital flowchart using draw.io
3. Corresponding pseudocode
4. Test cases dengan different scenarios

#### **Exercise 2: Loop Structure Practice**
**Task:** Document "Inventory Restock Algorithm"

**Requirements:**
- Check current inventory levels
- Compare with minimum thresholds
- Calculate reorder quantities
- Generate purchase orders
- Update inventory forecasts

**Focus Areas:**
- Proper loop structures dalam flowchart
- Clear iteration termination conditions
- Nested decision logic
- Data flow between processes

#### **Exercise 3: Complex Business Logic**
**Task:** Model "Insurance Claim Processing System"

**Requirements:**
- Policy verification
- Claim validation
- Damage assessment
- Approval workflow
- Payment processing
- Fraud detection checks

**Advanced Elements:**
- Exception handling paths
- Parallel approval processes
- Time-based decisions
- External system integrations

### **7.2 Assessment Criteria**

#### **Flowchart Evaluation Rubric:**

**Technical Accuracy (40%):**
- Correct symbol usage according to standards
- Logical flow dan connectivity
- Complete process coverage
- Proper termination conditions

**Clarity dan Readability (30%):**
- Clear, descriptive labels
- Appropriate level of detail
- Consistent formatting
- Easy to follow logic

**Design Quality (20%):**
- Professional appearance
- Good use of space dan alignment
- Color coding dan visual hierarchy
- Minimal line crossings

**Completeness (10%):**
- All requirements addressed
- Edge cases considered
- Error handling included
- Documentation quality

#### **Pseudocode Evaluation Rubric:**

**Logical Correctness (50%):**
- Algorithm produces correct results
- All paths tested dan verified
- Proper handling of edge cases
- Efficient solution approach

**Structure dan Syntax (30%):**
- Proper indentation dan formatting
- Consistent naming conventions
- Clear control structures
- Appropriate level of abstraction

**Documentation (20%):**
- Meaningful comments
- Clear variable descriptions
- Algorithm explanation
- Complexity analysis

---

## **BAGIAN 8: TOOLS DAN RESOURCES**

### **8.1 Recommended Software Tools**

#### **Free Flowchart Tools:**
1. **Draw.io/Diagrams.net**
   - Web-based, no installation required
   - Extensive shape libraries
   - Real-time collaboration
   - Multiple export formats

2. **Lucidchart (Free Tier)**
   - Professional templates
   - Team collaboration features
   - Integration dengan cloud services
   - Advanced formatting options

3. **Creately**
   - Intuitive drag-and-drop interface
   - Pre-built templates
   - Real-time collaboration
   - Mind mapping capabilities

#### **Advanced Tools:**
1. **Microsoft Visio**
   - Industry standard untuk enterprise
   - Advanced shape customization
   - Integration dengan Office suite
   - Professional templates dan stencils

2. **Gliffy**
   - Web-based collaborative platform
   - Integration dengan Confluence
   - Version control features
   - Team management tools

#### **Pseudocode Editors:**
1. **Online Pseudocode Compiler**
   - pseudocode.deepjain.com
   - Syntax highlighting
   - Basic execution capabilities
   - Educational focus

2. **Text Editors dengan Syntax Highlighting**
   - Visual Studio Code dengan pseudocode extensions
   - Sublime Text dengan custom themes
   - Notepad++ dengan user-defined languages

### **8.2 Learning Resources**

#### **Online Tutorials:**
- **Draw.io Documentation**: Official guides dan tutorials
- **Flowchart Best Practices**: Industry standard guidelines
- **Algorithm Visualization**: Interactive learning platforms

#### **Books dan References:**
- "The Art of Readable Code" by Dustin Boswell
- "Code Complete" by Steve McConnell
- "Introduction to Algorithms" by Cormen et al.

#### **Practice Platforms:**
- LeetCode untuk algorithm practice
- HackerRank untuk coding challenges
- CodeSignal untuk skill assessment

---

## **BAGIAN 9: RANGKUMAN DAN NEXT STEPS**

### **9.1 Key Learning Outcomes**

Pada pertemuan ini, kita telah berhasil:

**1. Master Flowchart Fundamentals:**
- Understanding dari sejarah dan evolution flowcharts
- Comprehensive knowledge dari ISO 5807 standards
- Proficiency dalam menggunakan different flowchart types

**2. Develop Pseudocode Skills:**
- Ability untuk write clear, structured pseudocode
- Understanding dari core programming constructs
- Skills dalam converting between algorithm representations

**3. Gain Practical Tool Experience:**
- Hands-on experience dengan draw.io
- Professional flowchart creation techniques
- Digital collaboration dan sharing capabilities

**4. Apply Integration Techniques:**
- Converting algorithms between different formats
- Creating comprehensive documentation packages
- Handling complex business logic scenarios

### **9.2 Professional Applications**

**In Software Development:**
- System design documentation
- Algorithm planning dan validation
- Team communication dan knowledge transfer
- Code review dan debugging processes

**In Business Analysis:**
- Process optimization dan improvement
- Workflow documentation untuk compliance
- Training material development
- Stakeholder communication tools

**In Project Management:**
- Project workflow planning
- Risk assessment dan mitigation strategies
- Resource allocation optimization
- Quality assurance processes

### **9.3 Assignment untuk Minggu Depan**

**Main Assignment: Flowchart untuk Even/Odd Number Detection**

Create comprehensive documentation package including:

1. **Natural Language Algorithm**
2. **Detailed Pseudocode** dengan proper formatting
3. **Professional Flowchart** using draw.io
4. **Test Cases** dengan expected outputs
5. **Complexity Analysis** (time dan space)

**Additional Requirements:**
- Include input validation
- Handle edge cases (negative numbers, zero)
- Add user-friendly error messages
- Document assumptions dan limitations

**Submission Format:**
- Digital flowchart (PNG atau PDF export)
- Pseudocode dalam formatted text document
- Test case documentation dengan screenshots
- Reflection essay (500 words) on learning experience

### **9.4 Preparation untuk Minggu Depan**

Minggu depan kita akan explore **"Tipe Data, Variabel, Operator, Ekspresi"** yang akan mencakup:

- **Identifiers & Keywords**: Naming conventions dan reserved words
- **Basic Data Types**: int, float, char, double, boolean
- **Variable Declarations**: Scope, lifetime, initialization
- **Operator Types**: Arithmetic, logical, relational, bitwise
- **Expression Evaluation**: Precedence, associativity, type conversion

**Recommended Preparation:**
1. Review basic mathematical operations
2. Familiarize dengan common programming terminology
3. Practice logical thinking dengan boolean expressions
4. Explore variable naming best practices

---

## **PENUTUP**

Kemampuan untuk create clear, professional flowcharts dan well-structured pseudocode adalah fundamental skills yang akan serve you throughout your programming career. Dari initial algorithm design hingga system documentation, tools ini akan menjadi constant companions dalam your development journey.

**Key Takeaways dari Minggu 3:**

1. **Visual Communication Power**: Flowcharts bridge the gap antara technical dan non-technical stakeholders, making complex processes accessible to everyone.

2. **Structured Thinking**: Pseudocode forces you untuk think logically dan systematically about problem-solving approaches.

3. **Documentation Excellence**: Professional flowcharts dan clear pseudocode serve sebagai living documentation yang evolves dengan your systems.

4. **Tool Mastery**: Proficiency dalam draw.io dan similar tools adalah valuable professional skill yang applicable across many domains.

5. **Standard Compliance**: Understanding ISO standards ensures your documentation dapat be understood dan maintained by other professionals.

**Moving Forward:**

As we transition ke more technical programming concepts next week, remember bahwa the visualization dan documentation skills you've developed akan remain relevant. Whether you're designing databases, planning user interfaces, atau architecting complex systems, the ability untuk clearly communicate your ideas through visual dan textual representations adalah invaluable.

**Industry Perspective:**

In modern software development, companies increasingly value developers who can:
- Document their work clearly
- Communicate complex ideas visually  
- Collaborate effectively across teams
- Maintain high-quality technical documentation

The skills you've practiced today position you well untuk these expectations.

**Final Challenge:**

Before our next meeting, try to identify a real-world process in your daily life (could be as simple as making coffee atau as complex as planning a trip) dan create both a flowchart dan pseudocode untuk it. This exercise akan help reinforce the concepts dan demonstrate the universal applicability of these tools.

Remember: **"A well-designed flowchart is worth a thousand lines of explanation, dan good pseudocode is the foundation of great code."**

See you next week as we dive into the building blocks of programming: data types, variables, dan operators!

**Happy Diagramming!** 📊💻

---

*Total kata: ~5000 kata*

**Referensi:**
- Draw.io Documentation: https://www.drawio.com/doc/getting-started-basic-flow-chart
- ISO 5807 Standard for Information processing — Documentation symbols and conventions for data, program and system flowcharts
- Programiz Algorithm Tutorials dan GeeksforGeeks Pseudocode Guidelines
- Various computer science textbooks on algorithm visualization dan documentation standards