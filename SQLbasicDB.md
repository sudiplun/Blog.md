### Create database
```sql
CREATE DATABASE Employee;
```
### Switch to database
```sql
USE Employee;
```
### Create EmployeeInfo table
```sql
CREATE TABLE EmployeeInfo (
    EmployeeId INT IDENTITY(1,1) PRIMARY KEY,
    EmployeeName NVARCHAR(200),
    EmployeeAddress NVARCHAR(200), 
    PhoneNumber NVARCHAR(200), 
    Email NVARCHAR(200),
    DepartmentId INT
);
```
### Create Department table
```sql
CREATE TABLE Department (
    DepartmentId INT IDENTITY(1,1) PRIMARY KEY,
    DepartmentName NVARCHAR(200)
);
```

### Create EmployeeSalary table
```sql
CREATE TABLE EmployeeSalary (
    EmployeeSalaryId INT IDENTITY(1,1) PRIMARY KEY,
    EmployeeId INT,
    MonthName NVARCHAR(100), 
    Salary DECIMAL(18,2)
);
```

### Create SpEmployeeInfo stored procedure
```sql
CREATE PROCEDURE SpEmployeeInfo
    @EmployeeId INT,
    @EmployeeName NVARCHAR(200),
    @EmployeeAdress NVARCHAR(200),
    @PhoneNumber NVARCHAR(200),
    @Email NVARCHAR(200),
    @DepartmentId INT
AS
BEGIN 
   

INSERT INTO EmployeeInfo
 VALUES (@EmployeeName, @EmployeeAdress, @PhoneNumber, @Email, @DepartmentId);
 END
```
