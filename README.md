# 🐧 Linux File Operations Lab

### Experiment 04 | Linux Administration Laboratory

> **From creating a file to processing structured records — this experiment explores practical file-system operations through the Linux terminal.**

---

## 🔍 What This Experiment Covers

This laboratory exercise focuses on three different file-handling scenarios:

| Lab Task | Area of Practice | Main Outcome |
|----------|------------------|--------------|
| **01** | File & Directory Setup | Create, combine, rename and sort files |
| **02** | Student Data Handling | Filter, transform, secure and count records |
| **03** | File Content Processing | Merge files and extract selected data |

---

# 🧩 Task 01 — Organizing Department Files

## Scenario

A `CSE` directory is created to maintain separate information about staff, faculty and student representatives.

### Workflow

    Create CSE
       ↓
    Enter CSE
       ↓
    Create three files
       ↓
    Add information
       ↓
    Combine staff + faculty
       ↓
    Rename combined file
       ↓
    Sort the information

## Terminal Session

### Directory Setup

    $ mkdir CSE
    $ cd CSE
    $ pwd

**Output**

    /home/user/CSE

### File Creation

    $ touch staff faculty stud_rep
    $ ls

**Output**

    faculty  staff  stud_rep

### Input Data

**staff**

    Ravi
    Suresh
    Priya

**faculty**

    Dr. Kumar
    Dr. Meena
    Dr. Anand

**stud_rep**

    Arun

### Combining Files

    $ cat staff faculty > "S&F"
    $ cat "S&F"

**Output**

    Ravi
    Suresh
    Priya
    Dr. Kumar
    Dr. Meena
    Dr. Anand

### Renaming

    $ mv "S&F" "F&S"
    $ ls

**Output**

    F&S  faculty  staff  stud_rep

### Sorting

    $ sort "F&S" > "newF&S"
    $ cat "newF&S"

**Output**

    Dr. Anand
    Dr. Kumar
    Dr. Meena
    Priya
    Ravi
    Suresh

### Commands Learned

`mkdir` · `cd` · `pwd` · `touch` · `cat` · `mv` · `sort` · `ls`

---

# 👥 Task 02 — Student Record Management

## Scenario

Student information is stored in text files and processed using Linux utilities. The task demonstrates filtering, field selection, text conversion, permissions and record counting.

## Initial Dataset

### NameList

    Arun
    Bala
    Charan
    Divya
    Ezhil
    Farhana
    Ganesh
    Hari
    Indhu
    John

### MarkList

    Arun      23BCS001    Male      98
    Bala      23BCS002    Male      94
    Charan    23BCS003    Male      91
    Divya     23BCS004    Female    99
    Ezhil     23BCS005    Male      95
    Farhana   23BCS006    Female    96
    Ganesh    23BCS007    Male      92
    Hari      23BCS008    Male      90
    Indhu     23BCS009    Female    97
    John      23BCS010    Male      93

---

## 01 — Separate Records

### Male Records

    $ grep "Male" MarkList > MaleList

**Output**

    Arun      23BCS001    Male      98
    Bala      23BCS002    Male      94
    Charan    23BCS003    Male      91
    Ezhil     23BCS005    Male      95
    Ganesh    23BCS007    Male      92
    Hari      23BCS008    Male      90
    John      23BCS010    Male      93

### Female Records

    $ grep "Female" MarkList > FemaleList

**Output**

    Divya     23BCS004    Female    99
    Farhana   23BCS006    Female    96
    Indhu     23BCS009    Female    97

---

## 02 — Select Required Fields

The gender column is removed so that only the student name, register number and mark remain.

    $ awk '{print $1, $2, $4}' MaleList > temp
    $ mv temp MaleList

    $ awk '{print $1, $2, $4}' FemaleList > temp
    $ mv temp FemaleList

**MaleList**

    Arun 23BCS001 98
    Bala 23BCS002 94
    Charan 23BCS003 91
    Ezhil 23BCS005 95
    Ganesh 23BCS007 92
    Hari 23BCS008 90
    John 23BCS010 93

---

## 03 — Convert Male Records

    $ tr '[:lower:]' '[:upper:]' < MaleList > temp
    $ mv temp MaleList

**Output**

    ARUN 23BCS001 98
    BALA 23BCS002 94
    CHARAN 23BCS003 91
    EZHIL 23BCS005 95
    GANESH 23BCS007 92
    HARI 23BCS008 90
    JOHN 23BCS010 93

---

## 04 — Generate Index Files

Return to the parent directory:

    $ cd ..

Create a hidden directory listing:

    $ ls -laR > .Index

Generate detailed file information:

    $ find . -ls > FullIndex

---

## 05 — Apply Permissions

### FullIndex → Read Only

    $ chmod 444 FullIndex

### .Index → Write Only

    $ chmod 222 .Index

---

## 06 — Identify Regular Files

    $ find . -type f > type1

---

## 07 — Duplicate and Remove Directory

Create a copy:

    $ cp -r IBECSE R2023CSE

Remove the original:

    $ rm -r IBECSE

---

## 08 — Count Student Records

    $ wc -l MaleList
    $ wc -l FemaleList

**Output**

    7 MaleList
    3 FemaleList

Total:

    $ cat MaleList FemaleList | wc -l

**Output**

    10

### Commands Learned

`grep` · `awk` · `tr` · `find` · `ls` · `chmod` · `cp` · `rm` · `wc`

---

# 📄 Task 03 — Extracting and Rearranging File Data

## Scenario

Three files are prepared and their contents are manipulated to demonstrate merging, line extraction and numbered display.

---

## Source Files

### NameList

    Arun
    Bala
    Charan
    Divya
    Ezhil
    Farhana
    Ganesh
    Hari
    Indhu
    John
    Kavin
    Lakshmi
    Manoj
    Nisha
    Praveen

### MarkList

    98
    94
    91
    99
    95
    96
    92
    90
    97
    93
    89
    88
    94
    96
    91

### StudRep

    Arun

---

## 01 — Build the Working Directory

    $ mkdir Ex3
    $ cd Ex3
    $ touch MarkList NameList StudRep

---

## 02 — Combine Related Data

    $ paste NameList MarkList > Detail1
    $ cat Detail1

**Output**

    Arun      98
    Bala      94
    Charan    91
    Divya     99
    Ezhil     95
    Farhana   96
    Ganesh    92
    Hari      90
    Indhu     97
    John      93
    Kavin     89
    Lakshmi   88
    Manoj     94
    Nisha     96
    Praveen   91

---

## 03 — Convert the Arrangement

    $ paste -s Detail1 > Detail2

This produces a single-line arrangement of the contents of `Detail1`.

---

## 04 — Extract the First Eight Records

    $ head -8 Detail1 > file1
    $ cat file1

**Output**

    Arun      98
    Bala      94
    Charan    91
    Divya     99
    Ezhil     95
    Farhana   96
    Ganesh    92
    Hari      90

---

## 05 — Extract the Final Four Records

    $ tail -4 file1 > file2
    $ cat file2

**Output**

    Ezhil     95
    Farhana   96
    Ganesh    92
    Hari      90

---

## 06 — Start Extraction from Line Four

    $ tail -n +4 Detail1 > file3

Display the generated file with numbering:

    $ cat -n file3

**Output**

    1  Divya     99
    2  Ezhil     95
    3  Farhana   96
    4  Ganesh    92
    5  Hari      90
    6  Indhu     97
    7  John      93
    8  Kavin     89
    9  Lakshmi   88
    10 Manoj     94
    11 Nisha     96
    12 Praveen   91

### Commands Learned

`paste` · `head` · `tail` · `cat -n`

---

# 🛠️ Command Reference

| Command | Applied For |
|---------|-------------|
| `mkdir` | Directory creation |
| `cd` | Directory navigation |
| `pwd` | Location verification |
| `touch` | File creation |
| `nano` | Data entry and editing |
| `ls` | Directory listing |
| `cat` | Reading and combining files |
| `mv` | Renaming files |
| `sort` | Ordering text |
| `grep` | Record filtering |
| `awk` | Column extraction |
| `tr` | Character conversion |
| `find` | File discovery |
| `chmod` | Permission control |
| `cp` | Copying directories |
| `rm` | Removing directories |
| `wc` | Record counting |
| `paste` | Combining related data |
| `head` | Beginning-section extraction |
| `tail` | End/position-based extraction |

---

# 📊 Experiment Snapshot

    Files Created        → Multiple text and record files
    Directories Used     → CSE, IBECSE, R2023CSE, Ex3
    Data Operations      → Merge, filter, sort, extract
    Permission Tasks     → Read-only / Write-only
    Record Processing    → Student data
    Line Processing      → head / tail / cat -n

---

# 🎓 Skills Gained

By completing this experiment, I practiced:

- Linux file-system navigation
- Directory and file creation
- File-content manipulation
- Data filtering with patterns
- Column-based text processing
- Sorting and merging information
- File permission management
- Recursive copying and deletion
- Line-based data extraction
- Command-line record counting

---

# 💻 Environment

**Operating System:** Linux  
**Shell Environment:** Bash / Linux Terminal  
**Editor:** Nano  
**Laboratory:** Linux Administration Laboratory

---

# 👩‍💻 Student Details

**Name:** Krithika Umasankar  
**Course:** B.E. Computer Science and Engineering  
**Year:** 2nd Year  
**College:** Mepco Schlenk Engineering College  
**Experiment:** 04 – File and Directory Management

---

# ✅ Completion

This experiment provided practical experience in handling Linux files and directories while also introducing command-line techniques for processing structured text and student records.

**Create → Process → Organize → Verify**
