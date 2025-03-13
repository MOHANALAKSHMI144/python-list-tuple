# Case Study: Employee Attendance Management System

## Objective

Build a simple Employee Attendance System using lists and tuples in Python.

## Problem Statement

A company wants to track employee attendance using Python. The system should:

- Store employee records (ID, Name, Department).
- Mark attendance (Present/Absent) for each employee.
- Allow searching for attendance records by employee ID.
- Display a summary of attendance.

**Employee Details Tuple**

```python
(employee_id, employee_name, department)
```

**Attenance Records**

This will be a list of tuples.
```python
[(employee_id, date, status), ...]
```

### Tasks

- Create functions to mark attendance, search for attendance by id

### Sample Data

```python
attendance_records = [
    (101, "2025-03-01", "Present"),
    (102, "2025-03-01", "Absent"),
    (103, "2025-03-01", "Present"),
    (104, "2025-03-01", "Present"),
    (105, "2025-03-01", "Absent"),
]

employees = [
    (101, "Alice Johnson", "HR"),
    (102, "Bob Smith", "IT"),
    (103, "Charlie Brown", "Finance"),
    (104, "David White", "IT"),
    (105, "Eve Black", "Marketing")
]

```

### Sample Output

```
Attendance marked for Employee 101: Present
Attendance marked for Employee 102: Present
Attendance marked for Employee 103: Absent
Attendance marked for Employee 104: Present
Attendance marked for Employee 105: Present

Searching Attendance for Employee ID 102:
Date: 2025-03-01, Status: Absent
Date: 2025-03-02, Status: Present

Attendance Summary:
Alice Johnson: 100.00% Present
Bob Smith: 50.00% Present
Charlie Brown: 50.00% Present
David White: 100.00% Present
Eve Black: 50.00% Present
```
# Employee details as tuples
employees = [
    (101, "Alice Johnson", "HR"),
    (102, "Bob Smith", "IT"),
    (103, "Charlie Brown", "Finance"),
    (104, "David White", "IT"),
    (105, "Eve Black", "Marketing")
]

# Attendance records as a list of tuples
attendance_records = [
    (101, "2025-03-01", "Present"),
    (102, "2025-03-01", "Absent"),
    (103, "2025-03-01", "Present"),
    (104, "2025-03-01", "Present"),
    (105, "2025-03-01", "Absent"),
]

# Function to mark attendance
def mark_attendance(emp_id, date, status):
    attendance_records.append((emp_id, date, status))
    print(f"Attendance marked for Employee {emp_id} on {date} as {status}")

# Function to search attendance by employee ID
def search_attendance(emp_id):
    records = [record for record in attendance_records if record[0] == emp_id]
    if records:
        print(f"Attendance records for Employee {emp_id}:")
        for record in records:
            print(f"Date: {record[1]}, Status: {record[2]}")
    else:
        print(f"No attendance records found for Employee {emp_id}")

# Function to display attendance summary
def attendance_summary():
    summary = {}
    for emp in employees:
        emp_id = emp[0]
        present_days = sum(1 for record in attendance_records if record[0] == emp_id and record[2] == "Present")
        absent_days = sum(1 for record in attendance_records if record[0] == emp_id and record[2] == "Absent")
        summary[emp_id] = {"Present": present_days, "Absent": absent_days}
    
print("\nAttendance Summary:")
    for emp in employees:
        emp_id = emp[0]
        print(f"{emp[1]} ({emp[2]}): Present: {summary[emp_id]['Present']}, Absent: {summary[emp_id]['Absent']}")

# Example usage
mark_attendance(101, "2025-03-02", "Present")  
search_attendance(101)  
attendance_summary()
