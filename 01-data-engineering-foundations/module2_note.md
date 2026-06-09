# Module 2: SQL & Storage Fundamentals - Learning Notes

## I. Structured Query Language (SQL) Basics
*   **Definition**: SQL is the language used to communicate with relational databases, allowing users to query, insert, update, and delete data.
*   **Relational Databases**: These function like spreadsheets, storing data in tables where rows represent individual entries and columns represent specific details.
*   **Declarative Nature**: Unlike many programming languages, SQL focuses on **what** data you need rather than **how** the system should retrieve it.
*   **Core Commands**: 
    *   `SELECT`: Retrieves specific information from the database.
    *   `INSERT`: Creates new entries for customers or products.
    *   `UPDATE`: Rectifies errors in existing records.
    *   `DELETE`: Removes unneeded material.
    *   `CREATE TABLE` / `ALTER TABLE`: Used to build or modify database structures.

## II. Advanced SQL Techniques
*   **Aggregation Functions**: Used to condense large datasets into summary statistics including `SUM`, `AVG`, `COUNT`, `MAX`, and `MIN`.
*   **Conditional Logic**: The `CASE` statement allows for applying rules to aggregations, such as summing sales only above a certain dollar amount.
*   **Grouping & Sorting**:
    *   `GROUP BY`: Categorizes data into groups (e.g., total sales by category) for detailed analysis.
    *   `ORDER BY`: Arranges data in ascending or descending order.
*   **Pivoting**: This process transforms data from a row-based format into a column-based format, which is often more suitable for reporting.
*   **Joins**: Used to combine data from different tables based on common keys.
    *   **Inner Join**: Returns only the rows that have matching values in both tables.
    *   **Left Join**: Retrieves all records from the left table and matching records from the right; unmatched right-side fields appear as `NULL`.
    *   **Right Join**: Contains all records from the right table and matching records from the left.
    *   **Full Outer Join**: Combines results of both Left and Right joins, showing all records from both tables.
    *   **Cross Join**: Produces a Cartesian product, pairing every row from the first table with every row from the second.
*   **Regular Expressions (Regex)**: In PostgreSQL, operators like `~` (case-sensitive) and `~*` (case-insensitive) enable advanced pattern matching. Symbols like `^` (beginning of string) and `$` (end of string) act as anchors to control matches.

## III. Version Control with Git
*   **Purpose**: Git is a version control system used to track file changes over time, creating a "timeline" for a project's history.
*   **Repositories**: A "repo" is the folder Git tracks, containing all logs, branches, and commits.
*   **Common Commands**:
    *   `git init`: Initializes a new Git repository in a folder.
    *   `git config`: Sets user identity (name and email) for labeling commits.
    *   `git clone`: Downloads an existing project and its history from a remote URL.
    *   `git status`: Displays the current state of files (updated, staged, or untracked).
    *   `git add .`: Stages modified files for the next commit.
    *   `git commit -m`: Saves a snapshot of staged changes with an explanatory message.
    *   `git branch` / `git checkout`: Used to create and switch between different lines of development.
    *   `git merge`: Integrates changes from one branch into another.
    *   `git push` / `git pull`: Synchronizes local commits with a remote repository.
    *   `git stash`: Temporarily hides unfinished work to allow switching branches without committing.

## IV. AWS Storage Services

### Amazon S3 (Simple Storage Service)
*   **Structure**: A flat, object-based storage system where data is stored in **buckets**. Each **object** consists of the data, a unique **key** (path), and **metadata**.
*   **Bucket Names**: Must be globally unique across all AWS accounts.
*   **Storage Classes**: Designed to balance cost and performance.
    *   **Standard**: High availability for frequently accessed data.
    *   **Intelligent-Tiering**: Automatically moves data between tiers based on changing access patterns to save costs.
    *   **Glacier / Deep Archive**: Low-cost options for long-term archival where data is rarely accessed.
*   **Data Protection**:
    *   **Versioning**: Preserves multiple versions of an object, protecting against accidental deletions or overwrites.
    *   **Replication**: Automatically copies objects between buckets in the same (SRR) or different (CRR) regions.
    *   **Lifecycle Rules**: Automate the transition of objects to cheaper classes or their eventual deletion based on age.
*   **Security**:
    *   **Bucket Policies**: JSON-based permissions attached to a bucket to control access.
    *   **Encryption**: Includes Server-Side (SSE-S3, SSE-KMS, SSE-C) and Client-Side options.
    *   **Access Points**: Specialized "entrances" to a bucket that simplify permission management for different teams.

### Block and File Storage
*   **Amazon EBS (Elastic Block Store)**: Acts like an external hard drive for a single EC2 instance. Data is persistent even if the instance is stopped. **Elastic Volumes** allow users to increase size or change volume types without downtime.
*   **Amazon EFS (Elastic File System)**: A managed network drive using the **NFS protocol**. It allows multiple EC2 instances to access the same data simultaneously across different Availability Zones and scales capacity automatically.

### Centralized Data Protection
*   **AWS Backup**: A centralized service to automate backup policies and retention for multiple AWS resources (EBS, RDS, EFS, etc.).
*   **Backup Vault Lock**: Provides **WORM (Write Once, Read Many)** protection, preventing any user—including root—from deleting backups before their retention period expires.