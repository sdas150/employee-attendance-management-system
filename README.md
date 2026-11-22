<div align="center">

# 🕒 Employee Attendance Management System

### A SQL Server portfolio project | T-SQL • Stored Procedures • Reporting

[![SQL Server](https://img.shields.io/badge/Database-SQL%20Server-CC2927?logo=microsoftsqlserver&logoColor=white)](https://www.microsoft.com/sql-server)
[![Language](https://img.shields.io/badge/Language-T--SQL-blue)](https://learn.microsoft.com/en-us/sql/t-sql/)
[![Project](https://img.shields.io/badge/Project-Portfolio-success)](#)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**A practical attendance database that records employee punch-in and punch-out events, calculates working hours, prevents duplicate open sessions, and produces attendance reports.**

</div>

---

## 📌 Project overview

Small teams need a reliable way to record when employees start and finish work. This project demonstrates how a SQL Server database can manage employee attendance with validation, stored procedures, and reporting.

### ✨ Key features

| Feature | What it does |
|---|---|
| 👤 Employee master | Stores employee code, name, department, and active status |
| 🟢 Punch-in | Records the employee's login time |
| 🔴 Punch-out | Closes the open session and calculates elapsed hours |
| 🛡️ Duplicate protection | Prevents more than one open attendance session per employee |
| 📅 Daily report | Shows attendance sessions for a selected date |
| 📊 Monthly report | Summarizes sessions, days with punches, and completed hours |
| 🧾 Employee history | Returns attendance records for a selected employee and date range |

## 🧰 Technology stack

- Microsoft SQL Server
- T-SQL
- SQL Server Management Studio (SSMS)
- Relational database design, constraints, indexes, and stored procedures

## 🗂️ Repository structure

```text
Employee-Attendance-Management-System/
│
├── SQL_Scripts/
│   ├── 01_Create_Database.sql
│   ├── 02_Create_Tables.sql
│   ├── 03_Insert_Sample_Employees.sql
│   ├── 04_Create_Procedures.sql
│   └── 05_Create_Reports.sql
│
├── Test_Cases/
│   └── 06_Test_Project.sql
│
├── Documentation/
│   ├── Portfolio_Description.md
│   └── Testing_Guide.md
│
├── Screenshots/
│   └── Add-your-SSMS-screenshots-here.md
│
├── README.md
├── LICENSE
└── .gitignore
```

## 🚀 Getting started

### Prerequisites

- SQL Server 2016 or later
- SSMS
- A SQL Server login with permission to create a database

### Installation

1. Clone or download this repository.
2. Open SSMS and connect to your SQL Server instance.
3. Open and execute the SQL scripts in this order:

| Order | Script | Purpose |
|---:|---|---|
| 1 | `01_Create_Database.sql` | Creates and selects the project database |
| 2 | `02_Create_Tables.sql` | Creates employee and attendance tables, constraints, and indexes |
| 3 | `03_Insert_Sample_Employees.sql` | Inserts five sample employees |
| 4 | `04_Create_Procedures.sql` | Creates employee, punch-in, and punch-out procedures |
| 5 | `05_Create_Reports.sql` | Creates daily, monthly, and employee-history reports |
| 6 | `06_Test_Project.sql` | Runs example calls and report queries |

> **Important:** `02_Create_Tables.sql` drops and recreates the two project tables. Run it only in this sample project database when you are comfortable resetting its data.

## 💻 Example usage

### 1. Punch in

```sql
USE EmployeeAttendanceDB;
GO

EXEC dbo.usp_Employee_Login
    @EmployeeCode = 'EMP001';
```

### 2. Punch out

```sql
EXEC dbo.usp_Employee_Logout
    @EmployeeCode = 'EMP001';
```

### 3. View today's attendance

```sql
EXEC dbo.usp_Daily_Attendance_Report
    @AttendanceDate = CONVERT(date, SYSDATETIME());
```

### 4. View a monthly summary

```sql
EXEC dbo.usp_Monthly_Attendance_Report
    @Year = 2026,
    @Month = 11;
```

### 5. View employee attendance history

```sql
EXEC dbo.usp_Employee_Attendance_History
    @EmployeeCode = 'EMP001',
    @FromDate = '2026-11-01',
    @ToDate = '2026-11-30';
```

## 🧠 Database design

The project uses two core tables:

- **Employees** — one row per employee.
- **EmployeeAttendance** — one row per attendance session, linked to an employee through `EmployeeID`.

A filtered unique index on `EmployeeAttendance(EmployeeID)` where `LogoutTime IS NULL` enforces at most one open session for each employee.

See [`Documentation/Testing_Guide.md`](Documentation/Testing_Guide.md) for the test scenarios and expected outcomes.

## 🧪 Test scenarios

- Successful punch-in and punch-out
- Attempted duplicate punch-in
- Punch-out when no open session exists
- Invalid or inactive employee code
- Daily and monthly reporting
- Employee attendance history

## 📸 Screenshots

After running the scripts in SSMS, add screenshots to the `Screenshots/` folder. Good examples include:

1. Tables and sample employee rows
2. Successful punch-in result
3. Successful punch-out with calculated hours
4. Daily attendance report
5. Monthly attendance report

## ⚖️ Business rules and limitations

- Only active employees can punch in or out.
- An employee cannot have two simultaneously open sessions.
- Multiple completed sessions on the same day are allowed.
- Logout closes the most recent open session.
- Overnight sessions are associated with the date of punch-in.
- Working hours represent elapsed time; meal and other breaks are not deducted.

This is a learning and portfolio project, not a production payroll or workforce-management system. A production implementation should add authentication and authorization, audit controls, approved attendance corrections, break policies, time-zone rules, and organization-specific attendance policies.

## 👨‍💻 About this project

Created as a practical SQL development portfolio project to demonstrate database design, T-SQL programming, stored procedure development, validation, and reporting.

**Portfolio focus:** SQL Developer • SQL Server • T-SQL • Stored Procedures • Database Development
