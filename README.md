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
def mark_attendance(attendance_records, employee_id, date, status):
    """Marks attendance for an employee."""
    attendance_records.append((employee_id, date, status))
    print(f"Attendance marked for Employee {employee_id}: {status}")
def search_attendance(attendance_records, employee_id):
    """Searches attendance records for a specific employee ID."""
    print(f"\nSearching Attendance for Employee ID {employee_id}:")
    found = False
    for record in attendance_records:
        if record[0] == employee_id:
            print(f"Date: {record[1]}, Status: {record[2]}")
            found = True
    if not found:
        print("No attendance records found for this employee ID.")
def calculate_attendance_summary(attendance_records, employees):
    """Calculates and displays the attendance summary for all employees."""
    employee_attendance = {}
    for emp_id, _, _ in employees:
        employee_attendance[emp_id] = {"present": 0, "total": 0}
for record in attendance_records:
        emp_id = record[0]
        if emp_id in employee_attendance:
            employee_attendance[emp_id]["total"] += 1
            if record[2] == "Present":
                employee_attendance[emp_id]["present"] += 1
print("\nAttendance Summary:")
    for emp_id, name, _ in employees:
        if employee_attendance[emp_id]["total"] >0:
            percentage = (employee_attendance[emp_id]["present"] / employee_attendance[emp_id]["total"]) * 100
        else:
            percentage = 0
        print(f"{name}: {percentage:.2f}% Present")
        def add_new_days_attendance(attendance_records, employees, date, present_employees):
    """Adds attendance for a new day based on a list of present employee IDs."""
    for emp_id, _, _ in employees:
        if emp_id in present_employees:
            mark_attendance(attendance_records, emp_id, date, "Present")
        else:
            mark_attendance(attendance_records, emp_id, date, "Absent")

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
present_employees_day2 = [101, 102, 104, 105]
add_new_days_attendance(attendance_records, employees, "2025-03-02", present_employees_day2)

present_employees_day3 = [101, 103, 104]
add_new_days_attendance(attendance_records, employees, "2025-03-03", present_employees_day3)

search_attendance(attendance_records, 102)
calculate_attendance_summary(attendance_records, employees)
