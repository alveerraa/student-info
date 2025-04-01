# Student Information Application

This is a detailed Python application that utilizes a YAML file to store and read student information. The application allows users to view all students and filter them based on their GPA.

# Step-by-Step Guide

Step 1: Install Required Packages

To work with YAML files in Python, we need to install the PyYAML library. This library helps us read and write YAML files.

Installation:
Open your terminal.

Run the following command to install PyYAML:

pip install pyyaml

Step 2: Create the YAML File

Before writing the Python script, we need a students.yaml file that contains the student data. Here's an example of how the students.yaml file might look:

students:
  - name: John Doe
    age: 20
    major: Computer Science
    gpa: 3.5
  - name: Jane Smith
    age: 21
    major: Electrical Engineering
    gpa: 3.8
  - name: Mark Johnson
    age: 22
    major: Mechanical Engineering
    gpa: 3.2
    
Step 3: Write the Python Application

Create a new Python file named app.py in the same directory as students.yaml. This script will:

Load student information from the students.yaml file.

Allow users to view all students.

Filter students based on their GPA.

Here's an example of the code for app.py:

import yaml

def load_student_data():
    with open("students.yaml", "r") as file:
        data = yaml.safe_load(file)
    return data["students"]

def display_students(students):
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    filtered_students = [student for student in students if student["gpa"] >= min_gpa]
    return filtered_students

def main():
    students = load_student_data()
    display_students(students)
    try:
        min_gpa = float(input("\nEnter minimum GPA to filter students: "))
        filtered_students = filter_students_by_gpa(students, min_gpa)
        print(f"\nStudents with GPA >= {min_gpa}:")
        if filtered_students:
            for student in filtered_students:
                print(f"Name: {student['name']}, GPA: {student['gpa']}")
        else:
            print("No students found.")
    except ValueError:
        print("Invalid input. Please enter a valid GPA.")

if __name__ == "__main__":
    main()
    
Step 4: Run the Application

Ensure that both the app.py and students.yaml files are in the same directory.

Open your terminal and navigate to the directory where the files are located.

Run the application by typing the following command:

python app.py

The application will display all students and ask you to enter a minimum GPA to filter the students.

Example Output

All Students:

Name: John Doe, Age: 20, Major: Computer Science, GPA: 3.5
Name: Jane Smith, Age: 21, Major: Electrical Engineering, GPA: 3.8
Name: Mark Johnson, Age: 22, Major: Mechanical Engineering, GPA: 3.2

Enter minimum GPA to filter students: 3.5

Students with GPA >= 3.5:
Name: John Doe, GPA: 3.5
Name: Jane Smith, GPA: 3.8

# How the Application Works

Loading Data: The script reads the students.yaml file using the PyYAML library and loads the student data into a Python list of dictionaries.

Displaying Students: It then prints the details of all students in the terminal.

Filtering: The user is prompted to enter a minimum GPA. The script filters the list of students based on the provided GPA and displays those who meet the condition.

Error Handling: If the user enters an invalid GPA (e.g., a string instead of a number), the program will handle the error and prompt the user again.

Conclusion
This simple Python application demonstrates how to use a YAML file to store and process data. It provides users with the ability to view and filter student information based on GPA, making it a useful tool for working with structured data.

