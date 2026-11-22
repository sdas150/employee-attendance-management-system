# Portfolio description

## Project title
Employee Attendance Management System – SQL Server

## Problem
Small organizations need a consistent way to record employee start and finish times, prevent duplicate punch events, and review attendance.

## Solution
A SQL Server database with employee master data, attendance sessions, stored procedures for punch-in/punch-out, validation rules, and daily/monthly reporting procedures.

## Technical highlights
- Primary keys, unique constraints and foreign keys
- Filtered unique index for one open session per employee
- T-SQL stored procedures
- TRY/CATCH, transactions and THROW
- DATEDIFF_BIG for elapsed-hours calculation
- Daily, monthly and employee-history reports

## Suggested portfolio summary
Built an Employee Attendance Management System in SQL Server using T-SQL. Designed normalized employee and attendance tables, implemented transactional punch-in/punch-out stored procedures with duplicate-session protection, calculated working hours, and developed daily/monthly attendance reports. Included sample data and repeatable test scripts.
