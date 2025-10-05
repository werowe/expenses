This Python program reads financial transactions from a CSV file and loads them into a MySQL database. Here’s what it does step-by-step:

---

### 1. Connecting to the MySQL Database

- Uses the `mysql.connector` library to connect to a MySQL database server on `localhost`.
- Uses the `root` user and reads the password from the environment variable `MYSQL_PASS`.
- Connects to a database named `finances`.

---

### 2. Table Creation

- Executes a SQL statement to create the table `pocketsmith_search` **if it doesn’t already exist**.
- The table schema matches columns in the CSV:
  - Includes fields for dates, merchant name, amounts, currency, account details, transaction type, and several descriptive fields.

---

### 3. CSV Data Insertion

- Opens the file `pocketsmith-search.csv` for reading.
- Skips the header row and reads each transaction row.
- Converts any empty string fields in each row to `None` (allowing them to be stored as SQL `NULL`).
- For each row, executes an `INSERT INTO pocketsmith_search VALUES ...` SQL statement to add the record to the database.

---

### 4. Committing and Closing

- After all rows are processed, commits the transaction to MySQL to save changes.
- Closes the cursor and the connection to clean up resources.

---

### Summary

- **Purpose:** Quickly and reliably import CSV financial transaction data into a MySQL table.
- **Automation:** Handles table creation, data type matching, empty field conversion, and commits all changes without manual intervention.
- **Usage:** Useful for finance or accounting applications needing bulk imports, ETL processes, or database population for analytics from CSV files.
