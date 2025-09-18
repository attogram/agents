# Working with PostgreSQL

This document provides guidelines and best practices for AI agents working with PostgreSQL databases. PostgreSQL is a powerful, open-source object-relational database system known for its reliability, feature robustness, and performance.

## 1. Getting Started with `psql`

The primary way to interact with PostgreSQL from the command line is through the `psql` utility.

**Connecting to a Database:**

To connect to a database, you typically provide the database name, host, port, and username.

```bash
psql -d <database_name> -h <host> -p <port> -U <username>
```

If you are running `psql` on the same host as the database server and as the same user that the database expects, you can often just run `psql <database_name>`.

## 2. Essential `psql` Meta-Commands

`psql` provides a set of meta-commands that are very useful for database administration. These commands start with a backslash (`\`).

- `\?`: Get help on `psql` backslash commands.
- `\h`: Get help on SQL commands (e.g., `\h CREATE TABLE`).
- `\l`: List all available databases.
- `\c <database_name>`: Connect to a different database.
- `\dt`: List all tables in the current database.
- `\d <table_name>`: Describe a table (columns, types, indexes, etc.). Use `\d+` for more details.
- `\dn`: List all schemas.
- `\dv`: List all views.
- `\df`: List all functions.
- `\du`: List all roles (users).
- `\timing`: Toggle display of time taken for each query.
- `\q`: Quit `psql`.

## 3. Basic SQL Commands

Here is a quick refresher on the most common SQL commands.

- **Creating a Table**:

  ```sql
  CREATE TABLE users (
      id SERIAL PRIMARY KEY,
      username VARCHAR(50) UNIQUE NOT NULL,
      email VARCHAR(255) UNIQUE NOT NULL,
      created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
  );
  ```

- **Inserting Data**:

  ```sql
  INSERT INTO users (username, email) VALUES ('jules', 'jules@example.com');
  ```

- **Selecting Data**:

  ```sql
  SELECT id, username, email FROM users WHERE id = 1;
  ```

- **Updating Data**:

  ```sql
  UPDATE users SET email = 'jules.new@example.com' WHERE username = 'jules';
  ```

- **Deleting Data**:

  ```sql
  DELETE FROM users WHERE username = 'jules';
  ```

- **Joining Tables**:
  ```sql
  SELECT u.username, p.post_title
  FROM users u
  JOIN posts p ON u.id = p.author_id;
  ```

## 4. Key Concepts

### Transactions

Transactions are a fundamental concept of any ACID-compliant database. They allow you to run a group of statements as a single atomic unit.

- `BEGIN;`: Starts a transaction block.
- `COMMIT;`: Saves all changes made in the transaction.
- `ROLLBACK;`: Discards all changes made in the transaction.

```sql
BEGIN;
UPDATE accounts SET balance = balance - 100.00 WHERE name = 'Alice';
UPDATE accounts SET balance = balance + 100.00 WHERE name = 'Bob';
COMMIT;
```

### Indexing

Indexes are used to speed up the performance of `SELECT` queries. Without an index, the database has to scan the entire table to find the relevant rows.

- **Creating an Index**:

  ```sql
  CREATE INDEX idx_users_username ON users(username);
  ```

  This creates an index on the `username` column of the `users` table.

- **Analyzing Query Performance**: Use `EXPLAIN ANALYZE` to see how PostgreSQL is executing a query. This will show you if it's using an index.
  ```sql
  EXPLAIN ANALYZE SELECT * FROM users WHERE username = 'jules';
  ```

## 5. User and Role Management

PostgreSQL uses the concept of "roles" to manage database access permissions. A role can be a user or a group of users.

- **Creating a Role/User**:

  ```sql
  CREATE ROLE jules WITH LOGIN PASSWORD 'secure_password';
  ```

  `LOGIN` allows the role to log in (making it a user).

- **Granting Privileges**:

  ```sql
  GRANT SELECT, INSERT, UPDATE ON users TO jules;
  ```

  This gives the `jules` role specific permissions on the `users` table.

- **Revoking Privileges**:
  ```sql
  REVOKE UPDATE ON users FROM jules;
  ```

## 6. Backup and Restore

`pg_dump` and `pg_restore` are the standard command-line utilities for backing up and restoring PostgreSQL databases.

- **Creating a Backup**: `pg_dump` creates a plain-text SQL script or a compressed archive. The custom format (`-Fc`) is generally recommended.

  ```bash
  pg_dump -U <username> -h <host> -Fc --file=mydb.dump <database_name>
  ```

- **Restoring from a Backup**: `pg_restore` is used to restore from an archive created by `pg_dump`. You must create the database first.
  ```bash
  createdb -U <username> -h <host> <new_database_name>
  pg_restore -U <username> -h <host> -d <new_database_name> mydb.dump
  ```
