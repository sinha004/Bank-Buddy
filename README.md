# Bank Buddy: A C++ Bank Management System

This is a console-based **Bank Management System** implemented in C++. It allows for managing bank accounts, including creating, modifying, and deleting accounts, as well as handling deposits, withdrawals, and money transfers. It also includes an advanced feature for running transaction scripts with deadlock detection and prevention using a simplified Banker's Algorithm.

## Features

- **Account Management:**
    - Create new accounts with a 6-digit account number, name, mobile number, and password.
    - Set minimum and maximum balance limits for each account.
    - Modify existing account details.
    - Delete accounts.
    - View details of a specific account or all accounts in a tabular format.
- **Transaction Handling:**
    - **Deposit:** Add funds to an account.
    - **Withdrawal:** Remove funds from an account, with checks for insufficient balance and minimum balance limits.
    - **Money Transfer:** Transfer funds between two accounts, validating for balance and limits on both sides.
- **User Authentication:**
    - **Admin Mode:** Access all features with a predefined password (`"123"`).
    - **User Mode:** Log in with an account number and password to manage a single account.
- **Concurrency Simulation:**
    - **Transaction Script:** A feature to simulate multiple concurrent transactions.
    - **Deadlock Prevention (Banker's Algorithm):** The system analyzes a set of transactions to find a "safe sequence" in which they can be executed without causing a deadlock or violating account balance limits.
- **Data Persistence:**
    - Account data is saved to a binary file (`account.dat`) to ensure data is retained between program runs.

## Prerequisites

- A C++ compiler (e.g., g++, MinGW).
- Standard C++ libraries.

## How to Compile and Run

1.  Save the code as a `.cpp` file (e.g., `bank_buddy.cpp`).
2.  Compile the program using your C++ compiler.
    ```bash
    g++ -o bank_buddy bank_buddy.cpp -std=c++11
    ```
    *Note: The `tr1/unordered_map` header is deprecated; `unordered_map` is now part of the standard library `<unordered_map>`. The `-std=c++11` flag ensures compatibility.*

3.  Run the executable.
    ```bash
    ./bank_buddy
    ```

## Usage

When you run the program, you'll be presented with a login screen to select either **Admin Mode** or **User Mode**.

### Admin Mode

- **Password:** `123`
- **Options:**
    1.  **ACCOUNTS:** Access a sub-menu for creating, modifying, deleting, and viewing accounts.
    2.  **ACCOUNT ENQUIRY:** Look up a specific account by its number.
    3.  **MONEY TRANSFER:** Transfer funds between any two accounts.
    4.  **MONEY WITHDRAW/DEPOSIT:** Deposit or withdraw money from an account.
    5.  **RUN TRANSACTION SCRIPT:** Test a series of transactions for deadlock and find a safe execution sequence.

### User Mode

- You must enter a valid 6-digit account number and password.
- **Options:**
    1.  **SHOW ACCOUNT DETAILS:** View your account information.
    2.  **MODIFY ACCOUNT DETAILS:** Update your account details.
    3.  **MONEY TRANSFER:** Transfer funds from your account to another.
    4.  **MONEY WITHDRAW/DEPOSIT:** Manage deposits and withdrawals for your account.

## Technical Details

- **`account` Class:** A class to represent a bank account, including personal details, balance, and account limits.
- **`Transaction` Struct:** A structure for representing individual transactions, used primarily by the transaction script feature.
- **Data Storage:** Data is saved to a binary file (`account.dat`) for persistence. A temporary file (`Temp.dat`) is used during the saving process to prevent data corruption.
- **Concurrency Logic:** The `bankers_algo` function, a key part of the transaction script, checks for all possible permutations of transactions to find a safe sequence, a classic approach to deadlock avoidance. It ensures that transactions will not lead to a state where an account's balance falls below its minimum limit or exceeds its maximum limit.

## Developers

- Pulkit Sinha
- Priyanshu Sharma
- Raghvan Pareek
- Swamy Pulaparthi
