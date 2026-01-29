# 🏦 NexusBank-CLI

> A robust, dual-application core banking system simulation built entirely in C++20.

![Language](https://img.shields.io/badge/Language-C%2B%2B20-00599C)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey)
![Build](https://img.shields.io/badge/Build-Visual%20Studio-5C2D91)

---

## 📖 Overview

**NexusBank-CLI** is a complete banking system simulation consisting of two standalone console applications that work together:

| Application           | Purpose                                         | Target User                 |
| --------------------- | ----------------------------------------------- | --------------------------- |
| **NexusBank Manager** | Administrative operations and client management | Bank Staff / Administrators |
| **NexusBank ATM**     | Self-service banking transactions               | Bank Clients                |

Both applications share a common flat-file database (`Data/`), enabling seamless data persistence and real-time synchronization between staff and client operations.

---

## ✨ Features

### 🖥️ NexusBank Manager (Admin Panel)

| Category               | Features                                                                               |
| ---------------------- | -------------------------------------------------------------------------------------- |
| **Client Management**  | Full CRUD operations: List, Add, Update, Delete, and Find clients                      |
| **User Management**    | Manage system users with granular permission controls                                  |
| **Permissions System** | Bitwise permission flags (List, Add, Delete, Update, Find, Transactions, Manage Users) |
| **Transactions**       | Process deposits, withdrawals, and view total bank balances                            |
| **Security**           | Role-based access control with login authentication                                    |

### 🏧 NexusBank ATM (Client Self-Service)

| Feature             | Description                                                                |
| ------------------- | -------------------------------------------------------------------------- |
| **Quick Withdraw**  | Pre-set withdrawal amounts ($20, $50, $100, $200, $400, $600, $800, $1000) |
| **Normal Withdraw** | Custom withdrawal amounts (multiples of 5)                                 |
| **Deposit**         | Add funds to account balance                                               |
| **Balance Inquiry** | View current account balance                                               |
| **Secure Login**    | Account Number + PIN authentication                                        |

---

## 🛠️ Tech Stack

| Technology         | Usage                                                   |
| ------------------ | ------------------------------------------------------- |
| **C++20**          | Core language standard                                  |
| **STL Containers** | `std::vector` for in-memory data processing             |
| **File I/O**       | `std::fstream` for persistent storage                   |
| **Modular Design** | Procedural architecture with clearly separated concerns |

### Architecture Highlights

- **Custom Serialization/Deserialization** — Records are converted to/from delimited strings
- **In-Memory Processing** — Data loaded into vectors for efficient manipulation
- **Flat-File Database** — Human-readable `.txt` files with custom delimiter

---

## 📁 Data Format

The system uses a custom flat-file database with `#//#` as the field delimiter.

### `Data/Clients.txt`

```
AccountNumber#//#PinCode#//#Name#//#Phone#//#Balance
```

**Example:**

```
A001#//#1234#//#John Doe#//#555-0100#//#5000.00
A002#//#5678#//#Jane Smith#//#555-0200#//#12500.50
```

### `Data/Users.txt`

```
Username#//#Password#//#Permissions
```

**Example:**

```
Admin#//#Admin#//#-1
Teller01#//#pass123#//#35
```

> **Note:** Permission value `-1` grants full access. Other values use bitwise flags:
> `1` = List Clients | `2` = Add Client | `4` = Delete Client | `8` = Update Client | `16` = Find Client | `32` = Transactions | `64` = Manage Users

---

## 🚀 Setup & Compilation

### Prerequisites

- C++20 compatible compiler (GCC 10+, Clang 10+, or MSVC 2019+)
- Windows OS (uses `system("cls")` and `system("pause")`)

### Option 1: Visual Studio (Recommended for Windows)

1. Open `NexusBank_CLI/NexusBank_CLI.slnx` or `NexusBank_ATM/NexusBank_ATM.slnx`
2. Set configuration to **Debug** or **Release**
3. Build the solution (`Ctrl+Shift+B`)
4. Run with `F5` or `Ctrl+F5`

> **Important:** Ensure the `Data` folder is located two levels up from the executable (`..\..\Data\`).

### Option 2: Command Line (g++)

```bash
# Compile NexusBank Manager
g++ -std=c++20 -o NexusBank_Manager.exe NexusBank_CLI/NexusBank_CLI.cpp

# Compile NexusBank ATM
g++ -std=c++20 -o NexusBank_ATM.exe NexusBank_ATM/NexusBank_ATM.cpp
```

### Option 3: Command Line (MSVC)

```cmd
:: Compile NexusBank Manager
cl /std:c++20 /EHsc NexusBank_CLI\NexusBank_CLI.cpp /Fe:NexusBank_Manager.exe

:: Compile NexusBank ATM
cl /std:c++20 /EHsc NexusBank_ATM\NexusBank_ATM.cpp /Fe:NexusBank_ATM.exe
```

---

## 🔐 Default Credentials

| Application | Username/Account | Password/PIN |
| ----------- | ---------------- | ------------ |
| Manager     | `Admin`          | `Admin`      |
| ATM         | `Admin`          | `Admin`      |

---

## 📂 Project Structure

```
NexusBank-CLI/
├── Data/
│   ├── Clients.txt          # Client database
│   └── Users.txt            # User/admin database
├── NexusBank_ATM/
│   ├── NexusBank_ATM.cpp    # ATM application source
│   └── *.vcxproj            # Visual Studio project files
├── NexusBank_CLI/
│   ├── NexusBank_CLI.cpp    # Manager application source
│   └── *.vcxproj            # Visual Studio project files
└── README.md
```

---

## 📄 License

This project is available for educational purposes.

---

<p align="center">
  <b>NexusBank-CLI</b> — Banking made simple. 💳
</p>
