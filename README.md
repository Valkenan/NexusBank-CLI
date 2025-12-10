# NexusBank CLI

**A high-performance, file-based core banking system implemented in C++.**

![C++](https://img.shields.io/badge/Language-C++17-blue.svg) ![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey.svg) ![License](https://img.shields.io/badge/License-MIT-green.svg)

## 📖 Overview

NexusBank CLI is a robust simulation of a core banking backend. It handles client lifecycle management (CRUD), atomic financial transactions, and persistent data storage using a custom flat-file database engine. Designed with a focus on procedural modularity, this project demonstrates direct memory manipulation and low-level data serialization techniques.

## 🏗 Architecture

The application follows a **Modular Procedural Architecture**, separating the user interface layer from the business logic and data access layers.

* **Presentation Layer:** Handles user inputs and renders formatted tables using `iomanip`.
* **Business Logic Layer:** Validates transaction rules (e.g., overdraft protection).
* **Data Access Layer:** Interfaces between runtime memory and the physical disk (`Clients.txt`).

### Data Flow
1.  **Initialization:** The system loads the flat-file database into a `std::vector` of `sClient` structures.
2.  **Processing:** Operations (Update/Delete/Transact) modify the vector in memory for O(1) access speed.
3.  **Persistence:** Changes are serialized back to `Clients.txt` using a custom delimiter format (`#//#`).

## ⚙️ Technical Decisions

### 1. Custom Serialization Engine
Instead of using heavy libraries like JSON or XML, I implemented a custom tokenizer.
* **Why:** This reduces binary bloat and demonstrates a deep understanding of string manipulation and buffer parsing.
* **Format:** `AccountNumber#//#PinCode#//#Name#//#Phone#//#Balance`

### 2. In-Memory Vector Processing
The system utilizes `std::vector<sClient>` to hold the dataset in RAM.
* **Why:** Disk I/O is expensive. By loading the data once and manipulating it in the heap, the application achieves near-instantaneous response times for search and update operations.

## 🚀 Features

* **Client Management:** Add, delete, and update client records with duplicate detection.
* **Transaction Engine:** Deposit and Withdraw functionality with balance validation.
* **Reporting:** Generate total balance reports and individual client cards.

## 💻 Setup & Usage

1.  Clone the repository.
2.  Compile using g++:
    ```bash
    g++ NexusBank_CLI.cpp -o NexusBank
    ```
3.  Run the executable. Ensure `Clients.txt` is created in the same directory.