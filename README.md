# 📂 Linux File System Operations

> **Linux Administration Laboratory – Experiment 04**

A practical collection of Linux file and directory management exercises demonstrating how standard shell commands can be used to organize files, process data, manage permissions, and perform basic file-system operations.

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

## 📌 Experiment Overview

This experiment is divided into three practical sections:

| Section | Main Focus |
|--------|------------|
| **Question 1** | Basic file and directory operations |
| **Question 2** | Student records and file management |
| **Question 3** | File merging and content manipulation |

---

# 🗂️ Question 1 – Basic File and Directory Operations

### Tasks Performed

- Create the `CSE` directory
- Navigate into the directory
- Display the current working location
- Create `staff`, `faculty`, and `stud_rep` files
- Add sample information
- Combine `staff` and `faculty`
- Rename the merged file
- Sort the contents into a new file

### Commands Practiced

| Command | Purpose |
|---------|---------|
| `mkdir` | Create a directory |
| `cd` | Move between directories |
| `pwd` | Display the current location |
| `touch` | Create empty files |
| `nano` | Edit file contents |
| `cat` | View or combine file contents |
| `mv` | Rename or move files |
| `sort` | Arrange file contents |

### File Flow

    staff + faculty
          ↓
        S&F
          ↓
        F&S
          ↓
       newF&S
      (sorted)

---

# 👨‍🎓 Question 2 – Student Record Processing

### Tasks Performed

A student information directory is created and used to demonstrate several Linux file-management techniques.

The practical includes:

- Creating the `IBECSE` directory
- Preparing a `NameList`
- Creating a `MarkList`
- Separating male and female records
- Removing unwanted fields
- Converting text to uppercase
- Creating hidden and detailed index files
- Changing file permissions
- Listing regular files
- Copying a directory
- Removing the original directory
- Counting student records

### Data Processing Flow

    MarkList
       │
       ├── Male records ──→ MaleList
       │
       └── Female records → FemaleList

### Commands Practiced

| Command | Purpose |
|---------|---------|
| `grep` | Select matching records |
| `awk` | Extract required fields |
| `tr` | Transform text |
| `ls -laR` | Display files including hidden entries |
| `find` | Search and list files |
| `chmod` | Modify permissions |
| `cp -r` | Copy directories recursively |
| `rm -r` | Remove directories recursively |
| `wc -l` | Count lines or records |

---

# 📄 Question 3 – File Merging and Content Processing

### Tasks Performed

- Create the `Ex3` directory
- Prepare `MarkList`, `NameList`, and `StudRep`
- Combine student names and marks
- Generate a single-line representation
- Extract the first 8 lines
- Extract the last 4 lines
- Extract data starting from a particular line
- Display extracted data with line numbers

### File Processing Flow

    NameList + MarkList
            ↓
         Detail1
            ↓
       ┌────┼─────┐
       ↓    ↓     ↓
    Detail2 file1  file3
             ↓
            file2

### Commands Practiced

| Command | Purpose |
|---------|---------|
| `paste` | Combine file contents |
| `head` | Extract beginning lines |
| `tail` | Extract ending or selected portions |
| `cat -n` | Display contents with line numbers |

---

# 🧰 Complete Command Set

The experiment provides hands-on practice with the following Linux utilities:

`mkdir` · `cd` · `pwd` · `touch` · `nano` · `cat` · `mv` · `sort` · `grep` · `awk` · `tr` · `ls` · `find` · `chmod` · `cp` · `rm` · `wc` · `paste` · `head` · `tail`

---

# 🔐 File Permission Practice

Permission management is demonstrated using `chmod`.

| File | Permission Requirement |
|------|------------------------|
| `FullIndex` | Read Only |
| `.Index` | Write Only |

Example commands:

    chmod 444 FullIndex
    chmod 222 .Index

This provides practical exposure to Linux file-access permissions.

---

# 🔎 File and Directory Operations Covered

- Directory creation
- Directory navigation
- File creation
- File editing
- File viewing
- File merging
- File renaming
- Content sorting
- Pattern-based extraction
- Field extraction
- Text conversion
- Hidden file creation
- Permission modification
- File searching
- Directory copying
- Directory deletion
- Record counting

---

# 📚 Learning Outcomes

After completing this experiment, the following skills are developed:

- Understanding the Linux file-system structure
- Working confidently with files and directories
- Using command-line utilities for data processing
- Extracting and transforming structured text
- Applying Linux file permissions
- Managing directories recursively
- Combining multiple commands for practical tasks
- Performing basic student-record processing through shell commands

---

# 💻 Technologies Used

- **Operating System:** Linux
- **Shell:** Bash / Linux Command Line
- **Editor:** Nano
- **Environment:** Linux Terminal

---

# 🧠 Key Takeaways

This experiment demonstrates that Linux provides simple command-line utilities that can be combined to perform complete file-management workflows.

The practical work covers both basic operations such as creating and renaming files and advanced tasks such as filtering records, modifying permissions, searching directories, and processing selected portions of files.

---

# 📁 Practical Areas

| Area | Skills |
|------|--------|
| File Management | Create, edit, rename and view files |
| Directory Management | Create, navigate, copy and remove directories |
| Text Processing | Search, extract, transform and sort data |
| Data Handling | Merge files and process records |
| Permissions | Modify file access permissions |
| File Searching | Locate and list required files |

---

# 👩‍💻 Academic Information

**Name:** Krithika Umasankar  
**Course:** B.E. Computer Science and Engineering  
**Year:** 2nd Year  
**Institution:** Mepco Schlenk Engineering College  
**Laboratory:** Linux Administration Laboratory  
**Experiment:** 04 – File and Directory Management

---

# 🌱 Learning Focus

This experiment strengthens practical Linux administration skills by connecting individual shell commands with real file-system management tasks.

The main focus is on **command-line efficiency, file organization, text processing, permissions, and systematic problem solving**.

---

## ⭐ Repository

If this laboratory work is useful for your Linux learning journey, feel free to explore the repository and use it as a reference for practicing Linux commands.

**Keep learning. Keep experimenting. Keep improving.**
