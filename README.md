# 🎓 RTU Student Record Management System

## 📌 Project Overview
A lightweight, zero-dependency Python application built to manage student academic records. It uses Python Dictionaries for high-speed, in-memory CRUD operations and text-based File Handling for persistent storage.

## 🚀 Features
- **$O(1)$ Search Efficiency:** Uses Roll Numbers as dictionary keys for instant lookups.
- **Persistent Storage:** Automatically saves and loads data from a local `students.txt` file.
- **String Parsing:** Custom implementation of CSV-style reading/writing using `.split()` and formatting.

## ⚙️ How to Run
1. Clone the repository:
   ```bash
   git clone [https://github.com/yourusername/rtu-student-management.git](https://github.com/yourusername/rtu-student-management.git)
   ```
2. Run the script directly (no external libraries required):
   python main.py

3. UI Idea: HTML Frontend (Student Dashboard)
*Save as `student_dashboard.html`*
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>RTU Student Portal</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="bg-light p-5">
    <div class="container bg-white p-4 rounded shadow">
        <h2 class="text-primary border-bottom pb-2">🎓 Academic Record Manager</h2>
        
        <div class="row mt-4">
            <div class="col-md-4">
                <h4>Add New Student</h4>
                <form>
                    <input type="text" class="form-control mb-2" placeholder="Roll Number (e.g. 21CS01)" required>
                    <input type="text" class="form-control mb-2" placeholder="Full Name" required>
                    <input type="text" class="form-control mb-2" placeholder="Branch (e.g. CSE)" required>
                    <input type="number" step="0.1" class="form-control mb-3" placeholder="CGPA" required>
                    <button class="btn btn-success w-100">Save Record</button>
                </form>
            </div>
            
            <div class="col-md-8">
                <h4>Current Records</h4>
                <table class="table table-striped border">
                    <thead class="table-dark">
                        <tr>
                            <th>Roll No</th><th>Name</th><th>Branch</th><th>CGPA</th><th>Action</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>21CS01</td><td>Rahul Sharma</td><td>CSE</td><td>8.5</td>
                            <td><button class="btn btn-sm btn-danger">Delete</button></td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</body>
</html>
