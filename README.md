# Student Data Management Application

## Overview
This Python application reads student information from a YAML file and provides functionalities to display and filter students based on their GPA. It demonstrates the use of YAML for structured data storage and Python for data processing.

## Features
- Load student data from a YAML file.
- Display all student records in a structured format.
- Filter students based on a user-defined minimum GPA.
- Simple and easy-to-understand implementation using Python.

## Prerequisites
- Python 3.x
- PyYAML library

## Installation
Ensure you have Python installed, then install the required package:
```sh
pip install pyyaml
```

## YAML File Structure
The student data is stored in `students.yaml` in the following format:
```yaml
students:
  - name: Alice
    age: 21
    major: Computer Science
    gpa: 3.8
  - name: Bob
    age: 22
    major: Mathematics
    gpa: 3.5
  - name: Charlie
    age: 20
    major: Physics
    gpa: 3.9
  - name: David
    age: 23
    major: Chemistry
    gpa: 3.2
  - name: Eva
    age: 21
    major: Computer Science
    gpa: 3.7
```

## Usage
1. Save the student data in a file named `students.yaml`.
2. Create a Python script `app.py` and add the following code:

```python
import yaml

def load_data(file_path):
    """Load data from a YAML file."""
    with open(file_path, 'r') as file:
        return yaml.safe_load(file)

def display_students(students):
    """Display all students."""
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    """Filter students with GPA >= min_gpa."""
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]
    print(f"\nStudents with GPA >= {min_gpa}:")
    for student in filtered_students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    if not filtered_students:
        print("No students found.")

def main():
    data = load_data('students.yaml')
    students = data['students']
    display_students(students)
    min_gpa = float(input("\nEnter minimum GPA to filter students: "))
    filter_students_by_gpa(students, min_gpa)

if __name__ == "__main__":
    main()
```

## Running the Application
1. Ensure `students.yaml` and `app.py` are in the same directory.
2. Run the script using:
   ```sh
   python app.py
   ```
3. The script will display all students and prompt the user to enter a minimum GPA for filtering.

## Example Output
```
All Students:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Bob, Age: 22, Major: Mathematics, GPA: 3.5
...

Enter minimum GPA to filter students: 3.6

Students with GPA >= 3.6:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7
```

## Enhancements
Future improvements could include:
- Sorting students by GPA or name.
- Allowing updates and deletions of student records.
- Saving filtered results back to a new YAML file.

## Conclusion
This simple project demonstrates how YAML can be used to store structured data, which can then be processed efficiently using Python. It's a great starting point for more advanced applications involving structured data management.

