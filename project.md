1. Project TitleStudent Academic Record Management System2. Problem StatementColleges need a lightweight, local system to track student details (Roll Number, Name, Branch, and CGPA). Managing this on paper is inefficient, and using a massive database is overkill for simple local tracking.3. ObjectiveTo build a Menu-Driven CRUD (Create, Read, Update, Delete) application that uses a Python Dictionary for fast in-memory data manipulation and a .txt file for permanent data storage.4. Python Concepts UsedDictionaries: Primary data structure (Roll Number is the key).File Handling: Reading from and writing to a text file.String Operations: split(',') to read data, join() to save data.Control Structures: while loop for the menu, if-elif-else for choices.User-Defined Functions: Modularizing the code.5. Data Handling (File Structure)The system uses a simple text file named students.txt.Each line represents one student, separated by commas (CSV format):21CS01,Rahul Sharma,CSE,8.521CS02,Priya Singh,IT,9.16. Complete Python CodePythonimport os

FILE_NAME = "students.txt"

def load_data():
    """Reads file and returns a dictionary of students."""
    students = {}
    if not os.path.exists(FILE_NAME):
        return students
        
    with open(FILE_NAME, 'r') as file:
        for line in file:
            line = line.strip()
            if line:
                # String operation: split
                details = line.split(',') 
                roll_no = details[0]
                # Storing details as a list inside the dictionary
                students[roll_no] = [details[1], details[2], details[3]]
    return students

def save_data(students):
    """Saves the dictionary back to the text file."""
    with open(FILE_NAME, 'w') as file:
        for roll_no, details in students.items():
            # String operation: join
            record = f"{roll_no},{details[0]},{details[1]},{details[2]}\n"
            file.write(record)

def add_student(students):
    roll_no = input("Enter Roll Number: ")
    if roll_no in students:
        print("Student already exists!")
    else:
        name = input("Enter Name: ")
        branch = input("Enter Branch: ")
        cgpa = input("Enter CGPA: ")
        students[roll_no] = [name, branch, cgpa]
        save_data(students)
        print("Record Added Successfully!")

def view_students(students):
    print("\n--- Student Records ---")
    print("Roll No | Name | Branch | CGPA")
    print("-" * 35)
    for roll_no, details in students.items():
        print(f"{roll_no} | {details[0]} | {details[1]} | {details[2]}")
    print("-" * 35)

def search_student(students):
    roll_no = input("Enter Roll Number to Search: ")
    if roll_no in students:
        details = students[roll_no]
        print(f"Found: Name: {details[0]}, Branch: {details[1]}, CGPA: {details[2]}")
    else:
        print("Student not found.")

def delete_student(students):
    roll_no = input("Enter Roll Number to Delete: ")
    if roll_no in students:
        del students[roll_no]
        save_data(students)
        print("Record Deleted Successfully!")
    else:
        print("Student not found.")

def main():
    students = load_data()
    while True:
        print("\n=== RTU Student Management ===")
        print("1. Add Student")
        print("2. View All Students")
        print("3. Search Student")
        print("4. Delete Student")
        print("5. Exit")
        
        choice = input("Enter your choice (1-5): ")
        
        if choice == '1':
            add_student(students)
        elif choice == '2':
            view_students(students)
        elif choice == '3':
            search_student(students)
        elif choice == '4':
            delete_student(students)
        elif choice == '5':
            print("Exiting System. Goodbye!")
            break
        else:
            print("Invalid choice! Please try again.")

# Run the program
if __name__ == "__main__":
    main()
7. Step-by-Step ExplanationLoading Data: When the program starts, it checks if students.txt exists. If yes, it reads line by line, uses split(',') to break the string into parts, and populates a dictionary where the Roll Number is the key.Menu Loop: A while True loop keeps the program running, presenting choices to the user.Operations: Adding a student puts a new key-value pair in the dictionary. Searching is $O(1)$ fast because we just check if roll_no in students. Deleting removes the key.Saving Data: Whenever we add or delete, save_data() triggers, rewriting the dictionary back into the .txt file using string formatting to simulate a .csv structure.8. Sample Input/OutputPlaintext=== RTU Student Management ===
1. Add Student
2. View All Students
3. Search Student
4. Delete Student
5. Exit
Enter your choice (1-5): 1
Enter Roll Number: 21CS45
Enter Name: Ananya Gupta
Enter Branch: CSE
Enter CGPA: 8.8
Record Added Successfully!
9. Algorithm ExplanationDictionary Lookup/Insert/Delete: Time complexity is O(1) on average, making the system highly efficient for searching records.File I/O: Reading and writing to the file takes O(n) time, where n is the number of students.10. Viva Questions & AnswersWhy did you use a Dictionary instead of a List to store students?Answer: Dictionaries use key-value pairs. By making the Roll Number the key, I achieved O(1) time complexity for searching and deleting students, which is much faster than looping through a list (O(n)).Explain the role of strip() and split(',') in your code.Answer: strip() removes hidden newline characters (\n) from the end of the file line. split(',') converts the single string into a list of elements based on the comma separator, allowing me to isolate the Roll No, Name, etc.What does open(FILE_NAME, 'w') do if the file already exists?Answer: The 'w' (write) mode will overwrite the existing file completely. That is why I load all data into the dictionary first, modify it in memory, and then overwrite the file with the updated dictionary.How is your program handling file errors if students.txt doesn't exist initially?Answer: I imported the os module and used os.path.exists(). If the file doesn't exist, it simply returns an empty dictionary, preventing a FileNotFoundError.What is if __name__ == "__main__": doing at the bottom?Answer: It ensures that the main() function only runs if this script is executed directly. If this script is imported as a module into another Python file, the menu won't accidentally start.
