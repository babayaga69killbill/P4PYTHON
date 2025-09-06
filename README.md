# P4PYTHON
# Computer Science & Engineering Concepts Summary

This document provides a brief overview of key concepts in computer science and engineering, compiled from various diagrams and infographics.

---

## 1. Processing Units: CPU vs. GPU vs. TPU

Different processors are designed for different types of tasks, which is reflected in their architecture and how they handle computation and memory.

| Feature             | CPU (Central Processing Unit)    | GPU (Graphics Processing Unit) | TPU (Tensor Processing Unit)      |
| ------------------- | -------------------------------- | ------------------------------ | --------------------------------- |
| **Compute Primitive** | **Scalar** (single data operations) | **Vector** (1D arrays of data)   | **Tensor** (multi-dimensional arrays) |
| **Parallelism** | Parallelized scalar operations     | Parallelized vector operations   | Parallelized matrix operations      |
| **Memory Management** | Implicitly managed (L1, L2, L3 caches) | Mixed (L1/L2 caches, Shared Memory) | Explicitly managed (Activation Buffer)  |
| **Best For** | General-purpose, sequential tasks  | Highly parallel tasks (graphics, ML) | Deep learning matrix operations     |

Other notable processor types include **APUs** (CPU+GPU), **FPGAs** (reconfigurable hardware), and **RISC-V** (an open-source instruction set architecture).

---

## 2. Memory and Storage Hierarchy

Computer memory and storage are organized in a hierarchy based on speed, cost, and capacity. The closer a memory type is to the CPU, the faster, smaller, and more expensive it is.

**The Hierarchy (Fastest to Slowest):**
1.  **On-Chip Memory:**
    * **Registers:** Directly inside the CPU, holding data for immediate processing.
    * **CPU Caches (SRAM):** L1, L2, L3 caches that store frequently accessed data to reduce latency. SRAM is faster than DRAM.
2.  **Main Memory (Volatile):**
    * **DRAM (e.g., DDR4, DDR5):** The system's main working memory (RAM).
3.  **Storage (Non-Volatile):**
    * **SSD (Solid State Drive):** Fast persistent storage.
    * **HDD (Hard Disk Drive):** Slower, mechanical persistent storage with large capacity.

* **Memory** is typically volatile (loses data when power is off), while **Storage** is non-volatile (retains data).
* **ROM (Read-Only Memory)** is a type of non-volatile memory that holds firmware like the BIOS.

---

## 3. Networking Fundamentals

### The OSI Model
The Open Systems Interconnection (OSI) model is a conceptual framework that standardizes the functions of a telecommunication or computing system into seven abstract layers.

1.  **Application Layer** (Software)
2.  **Presentation Layer** (Software)
3.  **Session Layer** (Software)
4.  **Transport Layer** (Heart of OSI)
5.  **Network Layer** (Hardware)
6.  **Data Link Layer** (Hardware)
7.  **Physical Layer** (Hardware)

### Life of a DNS Query
The Domain Name System (DNS) translates human-readable domain names (like `example.com`) into machine-readable IP addresses (like `93.184.216.34`). The process is as follows:
1.  Your browser checks its local cache for the IP address.
2.  If not found, it asks the OS's resolver (often your ISP's DNS server).
3.  The resolver checks its cache.
4.  If not found, the resolver queries a **Root Nameserver**.
5.  The root server directs it to the appropriate **Top-Level Domain (TLD) Nameserver** (e.g., for `.com`).
6.  The TLD server directs it to the domain's **Authoritative Nameserver**.
7.  The authoritative nameserver provides the final IP address.
8.  The IP is returned to your browser, which can now send the HTTP request.

---

## 4. Programming Language Performance

Programming languages show significant differences in performance regarding energy use, execution time, and memory consumption.

* **General Trend:** Compiled languages tend to be the most efficient, followed by languages running on a virtual machine, with interpreted languages being the least efficient.
* **Top Performers (Energy, Time, Memory):** Languages like **C, Rust, and C++** consistently rank at the top for efficiency.
* **Lower Performers (Energy, Time, Memory):** Interpreted languages like **Python, Ruby, Perl, and Lua** tend to consume significantly more resources.

---

## 5. The Map of Computer Science

Computer Science is a broad field encompassing theoretical foundations, hardware design, software development, and numerous applications. Major areas include:
* **Theoretical Computer Science:** Computability theory, algorithms & complexity, information theory, and cryptography.
* **Computer Engineering:** Hardware, computer architecture, operating systems, and networking.
* **Software Engineering:** Programming languages, compilers, software design, and databases.
* **Applications:** Artificial Intelligence (Machine Learning, NLP, Vision), Computer Graphics, Virtual/Augmented Reality, Big Data, and IoT.
# Linux Filesystem & Networking Concepts

This note summarizes the standard Linux filesystem hierarchy and the concept of Network Address Translation (NAT).

---

## 1. The Linux Filesystem Hierarchy

The Linux filesystem is a tree-like structure that starts from the root directory, denoted by a single slash (`/`). Every file and directory on the system is located under this root directory.

Here is a summary of the most common top-level directories and their purposes:

* **/bin**: Contains essential user binaries (executable programs) needed for the system to function, available to all users.
* **/sbin**: Holds essential system binaries, which are generally intended for use by the system administrator (root user).
* **/etc**: Stores system-wide configuration files for all programs.
* **/dev**: Contains device files that represent and allow access to hardware devices (e.g., hard drives, terminals).
* **/proc**: A virtual filesystem that provides information about system processes and kernel status.
* **/var**: For variable files—files whose content is expected to grow during the operation of the system, such as logs (`/var/log`), caches, and mail spools.
* **/tmp**: A directory for temporary files. These files are often deleted upon system reboot.
* **/usr**: Contains user-installed software, shared libraries, and documentation. For example, user-installed programs often go into `/usr/bin`.
* **/home**: Contains the personal home directories for each user on the system.
* **/boot**: Holds files needed for the boot process, including the Linux kernel and boot loader configuration.
* **/lib** & **/lib64**: Contain essential shared libraries needed by the binaries in `/bin` and `/sbin`. `lib64` is for 64-bit libraries.
* **/opt**: Reserved for optional or add-on software packages.
* **/mnt**: A temporary mount point for mounting filesystems (like a USB drive).
* **/media**: A directory where removable media (like USB drives, CD-ROMs) are automatically mounted.
* **/root**: The home directory for the root user.
* **/lost+found**: Used by the filesystem check tool (`fsck`) to store recovered corrupted files after a system crash or power outage.

---

## 2. Network Address Translation (NAT)

**NAT (Network Address Translation)** is a method used by routers to allow multiple devices on a private network (using private IP addresses like `10.x.x.x` or `192.168.x.x`) to share a single public IP address for accessing the internet.

### How NAT Works:
1.  A device on the local network with a **private IP** (e.g., `10.10.0.5`) sends a request to an external server on the internet (e.g., `example.com`).
2.  The router receives the outgoing packet and replaces the private source IP address with its own **public IP address** (e.g., `27.43.84.12`), which it gets from the Internet Service Provider (ISP).
3.  The external server receives the request, sees it as coming from the router's public IP, and sends its response back to that public address.
4.  The router receives the response and translates it back, forwarding it to the original device on the private network that made the request.

This process conserves public IPv4 addresses and adds a layer of security by hiding the internal network structure.
# 🐍 Python Learning Notes & Concepts

A collection of notes and roadmaps covering the Python programming language, from its execution model to advanced specializations.

---

## ⚙️ How Python Works vs. Compiled Languages

Python is often called an "interpreted" language, but it's a bit more nuanced. It combines compilation and interpretation. In contrast, languages like C are purely compiled.

* **Python Execution Model:**
    1.  **Source Code (`.py`)**: You write your Python code.
    2.  **Compiler**: The Python compiler translates the source code into **Bytecode (`.pyc`)**. This is a low-level, platform-independent representation of your code.
    3.  **Python Virtual Machine (PVM)**: The PVM is the runtime engine that reads the bytecode and interprets it, executing the instructions on the host machine.
    
* **C Compilation Model (for comparison):**
    1.  **Preprocessor**: Handles directives like `#include`.
    2.  **Compiler**: Translates the preprocessed code into **Assembly code**.
    3.  **Assembler**: Converts assembly code into **Object code** (machine code).
    4.  **Linker**: Combines object code with necessary libraries to create a final **Executable file (`.exe`)**.
    
---

## 🗺️ Python Learning Roadmap

This roadmap outlines a path from beginner to advanced, covering core concepts and popular specializations.

### 1. The Fundamentals
* **Basic Syntax**: Variables, data types (integers, floats, strings, booleans).
* **Operators**: Arithmetic, assignment, comparison, logical.
* **Conditionals**: `if`, `elif`, `else` statements.
* **Loops**: `for` and `while` loops.
* **Functions**: Defining functions, arguments, return values, and scope.
* **Error Handling**: `try`, `except` blocks for handling exceptions.

### 2. Data Structures & Algorithms (DSA)
* **Built-in Data Structures**:
    * **Lists**: Ordered, mutable collections.
    * **Tuples**: Ordered, immutable collections.
    * **Sets**: Unordered collections of unique elements.
    * **Dictionaries**: Unordered collections of key-value pairs.
* **Advanced Data Structures**:
    * Stacks & Queues
    * Linked Lists
    * Trees & Binary Search Trees
    * Hash Tables
* **Core Algorithms**:
    * Sorting (e.g., Bubble Sort, Merge Sort)
    * Recursion

### 3. Intermediate & Advanced Python
* **Object-Oriented Programming (OOP)**:
    * Classes & Objects
    * Inheritance
    * Methods (including dunder methods like `__init__`)
* **Functional Concepts**: Lambdas, `map`, `reduce`, `filter`.
* **Advanced Features**: Decorators, Generators, Iterators, Regular Expressions.

### 4. The Python Ecosystem & Specializations
* **Package Management**: Using `pip` and `conda` to install libraries.
* **Version Control**: Basic Git usage (`clone`, `add`, `commit`, `push`).
* **Testing**: Writing tests with frameworks like `pytest` or `unittest`.
* **Web Frameworks**: Building web applications with **Django**, **Flask**, or **FastAPI**.
* **Data Science**: Analyzing data with **NumPy**, **Pandas**, **Matplotlib**, and building models with **Scikit-learn** or **PyTorch**.
* **Automation**: Scripting tasks like web scraping or file manipulation.

---

## 📊 A Closer Look at Python Data Structures

Data structures are categorized based on their organization and mutability.

| Data Structure | Type | Key Characteristics | Example Syntax |
| :------------- | :--------- |:------------------------------------------------ | :--------------- |
| **List** | Built-in | Ordered, **Mutable** (changeable), allows duplicates. | `my_list = [1, "a", 2]` |
| **Tuple** | Built-in | Ordered, **Immutable** (unchangeable), allows duplicates. | `my_tuple = (1, "a", 2)` |
| **Dictionary** | Built-in | Key-value pairs, **Mutable**, keys must be unique. | `my_dict = {"key": "value"}` |
| **Set** | Built-in | Unordered, **Mutable**, must contain unique elements. | `my_set = {1, 2, 3}` |

* **Primitive Types**: The most basic structures like `Integer`, `Float`, `String`, and `Boolean`.
* **Non-Primitive Types**: More complex structures like Lists, Tuples, etc. These can be further divided into:
    * **Linear**: Stacks, Queues (data arranged sequentially).
    * **Non-linear**: Trees, Graphs (data arranged hierarchically or networked).
  # 💻 Computer Science & Python Quick Reference

A curated collection of notes covering fundamental computer science concepts, Object-Oriented Programming (OOP), and Python essentials.

---

## 1. Core Computer Science Concepts

### Program vs. Process vs. Thread

Understanding how software runs is crucial. The relationship is sequential:
* **Program**: A passive entity, like an executable file (`.exe`, `.app`), stored on disk. It's a set of instructions.
* **Process**: An active instance of a program that is loaded into memory (RAM) and is being executed. It's what you see in the Task Manager. A program can have multiple processes.
* **Thread**: The smallest unit of execution within a process. A process has at least one thread, and multiple threads can run concurrently to perform different tasks.

### Data Structures Cheatsheet

Data structures are formats for organizing, managing, and storing data. They are broadly classified into two types:

* **Linear Structures**: Elements are arranged in a sequential order.
    * **Array**: A collection of items stored at contiguous memory locations, accessed by an index. Fixed size.
    * **Linked List**: Elements (nodes) are linked using pointers. Efficient for insertions and deletions.
    * **Stack**: Follows a **LIFO** (Last-In, First-Out) order. Used for function calls, undo operations.
    * **Queue**: Follows a **FIFO** (First-In, First-Out) order. Used for task scheduling, message processing.

* **Non-linear Structures**: Elements are arranged in a hierarchical or networked manner.
    * **Hash Table**: A structure that maps keys to values for highly efficient lookup (e.g., Python's dictionary).
    * **Tree**: A hierarchical structure with a root node and child nodes. Used for file systems, searching.
    * **Graph**: A collection of nodes (vertices) connected by edges. Used for social networks, mapping.

---

## 2. Object-Oriented Programming (OOP) Principles

OOP is a programming paradigm based on the concept of "objects". The main pillars are:

* **Encapsulation**: Bundling data (variables) and the methods that operate on that data into a single unit, or "class". This is like putting ingredients and instructions inside a capsule to protect them from outside interference.
* **Abstraction**: Hiding complex implementation details and showing only the necessary features of an object.
* **Inheritance**: A mechanism where a new class inherits properties and methods from an existing class.
* **Polymorphism**: The ability for an object to take on many forms, allowing a single function or method to work with different data types.
* **Class**: A blueprint for creating objects.
* **Object**: An instance of a class.

---

## 3. Python Essentials 🐍

### Functions: `def` vs. `lambda`

Functions are reusable blocks of code. Python offers two primary ways to create them:

* **Normal Function**: Defined with the `def` keyword. It has a name, parameters, a body, and can have a `return` statement.
    ```python
    def add_two(a, b):
        """This function adds two numbers."""
        return a + b
    ```
* **Lambda Function**: A small, anonymous function defined with the `lambda` keyword. It's limited to a single expression and is useful for short, one-off tasks.
    ```python
    add_two_lambda = lambda a, b: a + b
    ```

### Python List Methods

Lists are one of the most versatile data structures in Python. Here are some common methods:

| Method | Description | Example |
| :--- | :--- | :--- |
| `list.append(x)` | Adds an item `x` to the end of the list. | `[1, 2].append(3) -> [1, 2, 3]` |
| `list.pop(i)` | Removes and returns the item at index `i`. | `[1, 2, 3].pop(1) -> [1, 3]` |
| `list.sort()` | Sorts the list in place. | `[3, 1, 2].sort() -> [1, 2, 3]` |
| `list.reverse()` | Reverses the elements of the list in place. | `[1, 2, 3].reverse() -> [3, 2, 1]` |
| `list.remove(x)` | Removes the first occurrence of item `x`. | `[1, 2, 2].remove(2) -> [1, 2]` |
| `list.insert(i, x)`| Inserts item `x` at index `i`. | `[1, 3].insert(1, 2) -> [1, 2, 3]`|
| `len(list)` | (Function) Returns the number of items in the list. | `len([1, 2, 3]) -> 3` |

### A Note on Performance

When choosing a language, performance can be a key factor. Based on benchmarks for energy, time, and memory usage:
* **Compiled languages** like **C, C++, and Rust** are generally the most efficient.
* **Interpreted languages** like **Python, Ruby, and Perl** are less performant in these raw metrics but offer high-level abstractions and faster development speed.
