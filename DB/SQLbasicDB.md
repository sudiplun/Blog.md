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

### Create EmployeeInfo stored procedure

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

### stored procedure call

```sql
EXEC [dbo].[SpEmployeeInfo]
    @EmployeeName = 'Ubina',
    @EmployeeAddress = 'KTM',
    @PhoneNumber = '98555554',
    @Email = 'email@gmal.com',
    @DepartmentId = 1;
```

#### Insert into EmployeeInfo

```sql
INSERT INTO EmployeeInfo (EmployeeName, EmployeeAddress, PhoneNumber, Email, DepartmentId)
VALUES
    ('John Doe', '123 Main St', '555-1234', 'johndoe@example.com', 1),
    ('Jane Smith', '456 Oak St', '555-5678', 'janesmith@example.com', 2),
    ('Bob Johnson', '789 Maple Ave', '555-9012', 'bobjohnson@example.com', 1);
```

### Create Department stored procedure

```sql
CREATE PROCEDURE SpDepartment
@DepartmentName NVARCHAR(200)

AS
BEGIN

INSERT INTO Department (DepartmentName)
VALUES(@DepartmentName);
END;
```

### stored procedure call

```sql
EXEC SpDepartment
@DepartmentName = 'IT';
```

### Create EmployeeSalary stored procedure

```sql
CREATE PROCEDURE SpEmployeeSalary
    @EmployeeId INT,
    @MonthName NVARCHAR(100),
    @Salary DECIMAL(18,2)
AS
BEGIN
    INSERT INTO EmployeeSalary(EmployeeId, MonthName, Salary)
    VALUES(@EmployeeId, @MonthName, @Salary);
END;
```

### stored procedure call

```sql
EXEC SpEmployeeSalary
    @EmployeeId = 1,
    @MonthName = 'jun',
    @Salary = 100000.00;
```

### Retrieve Employee Information and Department Names Using an INNER JOIN

```sql
SELECT E.EmployeeName, E.EmployeeAddress, E.PhoneNumber, D.DepartmentName FROM  EmployeeInfo AS E INNER JOIN Department as D on E.DepartmentId = D.DepartmentId
```

### Retrieve Employee Information and Department Names Using a RIGHT JOIN

```sql
SELECT E.EmployeeName, E.EmployeeAddress, E.PhoneNumber, D.DepartmentName FROM  EmployeeInfo AS E Right JOIN Department as D on E.DepartmentId = D.DepartmentId
```

# Creating an SQL Server Function to Add Two Integers and Returning the Result

```sql
create FUNCTION FnSum
(
@FirstNumber INT,
@SeconNumber  INT
)
RETURNS INT
BEGIN
DECLARE @Result INT
SET @Result=@FirstNumber+@SeconNumber
RETURN @Result
END
PRINT [dbo].FnSum('110',12)
```
