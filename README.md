# Pharmacy_Managament_System

# Project Overview
This repository contains the solution for the **BlueMedix Database Engineer Case Study**. The project involves designing a **Pharmacy Management System**, optimizing database queries, and implementing backup & recovery strategies using **PostgreSQL**.

# Project Structure
```
Pharmacy_DB/
│── schema.sql                # Database schema (tables & relationships)
│── queries.sql               # SQL queries for data retrieval & optimization
│── backup_recovery.md        # Documentation on backup & recovery strategies
│── access_control.sql        # User role permissions & access control queries
│── dataset/                  # Sample data for testing
│── README.md                 # Project documentation (this file)
```

# Task Breakdown
## 1. Database Schema Design & Optimization**
- **Schema Design:** Created tables for `users`, `products`, `orders`, and `payments`.
- **Normalization:** The schema is normalized to **Third Normal Form (3NF)**.
- **SQL Queries:** Implemented optimized queries for:
  - Retrieving **top-selling medicines per region**.
  - Calculating **inventory turnover rate**.
  - Identifying **frequent customers based on purchase history**.

## 2. Backup & Recovery Strategy**
- **Automated Backups:** Set up `pg_dump`/`mysqldump` for periodic database backups.
- **Disaster Recovery:** Simulated database restoration from backups.
- **Access Control:** Implemented role-based permissions for different users.

## How to Set Up & Run the Project
### ** Using PostgreSQL (Neon)**

1. Create the database:
   ```sh
   createdb pharmacy_db
   ```
2. Import the schema:
   ```sh
   psql -U postgres -d pharmacy_db -f schema.sql
   ```
3. Insert sample data:
   ```sh
   psql -U postgres -d pharmacy_db -f dataset/sample_data.sql
   ```
4. Run queries from `queries.sql` to test functionality.

## Access Control Implementation
- `admin_user`: Full privileges on the database.
- `pharmacist_user`: Read & write access to inventory tables.
- `support_user`: Read-only access for customer support.

### **Example SQL Commands for Role-Based Access**
```sql
CREATE USER support_user WITH PASSWORD 'password123';
GRANT SELECT ON ALL TABLES IN SCHEMA public TO support_user;
```

##  Backup & Restore Commands
## Backup Database**
## PostgreSQL:
```sh
pg_dump -U postgres -d pharmacy_db -F c -f backup.dump
```

## Restore Database**
## PostgreSQL:
```sh
pg_restore -U postgres -d pharmacy_db backup.dump
```


