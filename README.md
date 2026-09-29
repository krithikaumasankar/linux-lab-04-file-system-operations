# 📂 Linux File System Operations

> **Linux Administration Laboratory – Experiment 04**

A practical collection of Linux file and directory management exercises demonstrating file creation, directory handling, text processing, record management, permissions, searching, sorting, and file manipulation using Linux commands.

---

## 🎯 Experiment Objective

To practice Linux commands for:

- Creating and organizing directories
- Creating and editing files
- Navigating the file system
- Combining and renaming files
- Sorting and filtering file contents
- Extracting specific records
- Managing file permissions
- Creating hidden files
- Copying and deleting directories
- Counting records
- Manipulating file contents

---

# 📌 Question 1 – Basic File and Directory Operations

## 🎯 Objective

To create a directory, generate files, enter data, merge file contents, rename files, and sort the resulting data.

## ⌨️ Input / Commands

### 1. Create and enter the directory

    $ mkdir CSE
    $ cd CSE
    $ pwd

### Output

    /home/user/CSE

### 2. Create the required files

    $ touch staff faculty stud_rep
    $ ls

### Output

    faculty  staff  stud_rep

### 3. Enter data into `staff`

    Ravi
    Suresh
    Priya

### 4. Enter data into `faculty`

    Dr. Kumar
    Dr. Meena
    Dr. Anand

### 5. Enter representative information

    Arun

### 6. Merge `staff` and `faculty`

    $ cat staff faculty > "S&F"
    $ cat "S&F"

### Output

    Ravi
    Suresh
    Priya
    Dr. Kumar
    Dr. Meena
    Dr. Anand

### 7. Rename the merged file

    $ mv "S&F" "F&S"
    $ ls

### Output

    F&S  faculty  staff  stud_rep

### 8. Sort the contents

    $ sort "F&S" > "newF&S"
    $ cat "newF&S"

### Output

    Dr. Anand
    Dr. Kumar
    Dr. Meena
    Priya
    Ravi
    Suresh

## ✅ Result

The `CSE` directory and required files were created successfully. The files were merged, renamed, and sorted using Linux commands.

---

# 👨‍🎓 Question 2 – Student Record Processing

## 🎯 Objective

To create student records, separate data based on gender, modify file contents, manage permissions, create indexes, and perform directory operations.

## ⌨️ Input

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

## 💻 Commands and Outputs

### 1. Create the directory

    $ mkdir IBECSE
    $ cd IBECSE

### 2. Create student lists

    $ touch NameList MarkList

### 3. Extract male records

    $ grep "Male" MarkList > MaleList

### Output

    Arun      23BCS001    Male      98
    Bala      23BCS002    Male      94
    Charan    23BCS003    Male      91
    Ezhil     23BCS005    Male      95
    Ganesh    23BCS007    Male      92
    Hari      23BCS008    Male      90
    John      23BCS010    Male      93

### 4. Extract female records

    $ grep "Female" MarkList > FemaleList

### Output

    Divya     23BCS004    Female    99
    Farhana   23BCS006    Female    96
    Indhu     23BCS009    Female    97

### 5. Remove the Gender field

    $ awk '{print $1, $2, $4}' MaleList > temp
    $ mv temp MaleList

    $ awk '{print $1, $2, $4}' FemaleList > temp
    $ mv temp FemaleList

### Output – MaleList

    Arun 23BCS001 98
    Bala 23BCS002 94
    Charan 23BCS003 91
    Ezhil 23BCS005 95
    Ganesh 23BCS007 92
    Hari 23BCS008 90
    John 23BCS010 93

### Output – FemaleList

    Divya 23BCS004 99
    Farhana 23BCS006 96
    Indhu 23BCS009 97

### 6. Convert MaleList to uppercase

    $ tr '[:lower:]' '[:upper:]' < MaleList > temp
    $ mv temp MaleList

### Output

    ARUN 23BCS001 98
    BALA 23BCS002 94
    CHARAN 23BCS003 91
    EZHIL 23BCS005 95
    GANESH 23BCS007 92
    HARI 23BCS008 90
    JOHN 23BCS010 93

### 7. Create the hidden index file

    $ cd ..
    $ ls -laR > .Index

### 8. Create FullIndex

    $ find . -ls > FullIndex

### 9. Change permissions

    $ chmod 444 FullIndex
    $ chmod 222 .Index

### 10. Find regular files

    $ find . -type f > type1

### 11. Copy and remove the directory

    $ cp -r IBECSE R2023CSE
    $ rm -r IBECSE

### 12. Count student records

    $ wc -l MaleList
    $ wc -l FemaleList
    $ cat MaleList FemaleList | wc -l

### Output

    7 MaleList
    3 FemaleList
    10

## ✅ Result

Student records were successfully created, filtered, modified, counted, and organized using Linux file-management and text-processing commands.

---

# 📄 Question 3 – File Merging and Content Manipulation

## 🎯 Objective

To merge files, extract selected portions of data, create new files, and display file contents with line numbers.

## ⌨️ Input

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

## 💻 Commands and Outputs

### 1. Create the directory

    $ mkdir Ex3
    $ cd Ex3

### 2. Create the files

    $ touch MarkList NameList StudRep

### 3. Merge NameList and MarkList

    $ paste NameList MarkList > Detail1
    $ cat Detail1

### Output

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

### 4. Arrange Detail1 into a single line

    $ paste -s Detail1 > Detail2

### 5. Copy the first 8 lines

    $ head -8 Detail1 > file1
    $ cat file1

### Output

    Arun      98
    Bala      94
    Charan    91
    Divya     99
    Ezhil     95
    Farhana   96
    Ganesh    92
    Hari      90

### 6. Copy the last 4 lines of file1

    $ tail -4 file1 > file2
    $ cat file2

### Output

    Ezhil     95
    Farhana   96
    Ganesh    92
    Hari      90

### 7. Extract Detail1 from line 4

    $ tail -n +4 Detail1 > file3

### 8. Display file3 with line numbers

    $ cat -n file3

### Output

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

## ✅ Result

The required files were created and processed successfully. File contents were merged, selected lines were extracted, new files were generated, and the final contents were displayed with line numbers.

---

# 📚 Commands Used

| Command | Purpose |
|---------|---------|
| `mkdir` | Creates directories |
| `cd` | Changes directory |
| `pwd` | Displays current location |
| `touch` | Creates files |
| `nano` | Edits files |
| `cat` | Displays and combines contents |
| `mv` | Renames or moves files |
| `sort` | Sorts file contents |
| `grep` | Extracts matching records |
| `awk` | Selects specific fields |
| `tr` | Transforms text |
| `ls` | Lists files and directories |
| `find` | Searches for files |
| `chmod` | Changes permissions |
| `cp -r` | Copies directories |
| `rm -r` | Removes directories |
| `wc -l` | Counts lines |
| `paste` | Combines file contents |
| `head` | Extracts beginning lines |
| `tail` | Extracts ending or selected lines |
| `cat -n` | Displays line numbers |

---

# 🧠 Skills Practiced

- Linux file-system navigation
- File and directory creation
- File content management
- Text filtering and transformation
- Student record processing
- File merging
- Sorting and extraction
- Permission management
- Recursive directory operations
- Command-line problem solving

---

# 💻 Technologies Used

- **Operating System:** Linux
- **Shell:** Bash / Linux Terminal
- **Text Editor:** Nano

---

# 👩‍💻 Academic Information

**Name:** Krithika Umasankar  
**Course:** B.E. Computer Science and Engineering  
**Year:** 2nd Year  
**Institution:** Mepco Schlenk Engineering College  
**Laboratory:** Linux Administration Laboratory  
**Experiment:** 04 – File and Directory Management

---

## ⭐ Repository

This experiment provides hands-on practice with Linux commands used for managing files, directories, text data, permissions, and student records.

**Learn the command. Understand the operation. Practice it in the terminal.**
