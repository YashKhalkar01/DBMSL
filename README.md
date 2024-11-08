Got it! Let's tackle each question from the provided sheet, question by question, with specific SQL commands as requested. I'll be precise with each SQL solution to match each question in the document.


---

1. Student Table Operations

1. Create the Student table and display it.

CREATE TABLE Student (
    student_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT,
    grade CHAR(1),
    major VARCHAR(50)
);

SELECT * FROM Student;


2. Change the name of student Jane to Jenne.

UPDATE Student
SET first_name = 'Jenne'
WHERE first_name = 'Jane';


3. Find Students with a Specific Grade 'A'.

SELECT * FROM Student
WHERE grade = 'A';


4. Count the Number of Students in Each Major.

SELECT major, COUNT(*) AS student_count
FROM Student
GROUP BY major;


5. Order Students by Age in Ascending Order.

SELECT * FROM Student
ORDER BY age ASC;


6. Find the Oldest and Youngest Student.

Oldest Student:

SELECT * FROM Student
ORDER BY age DESC
LIMIT 1;

Youngest Student:

SELECT * FROM Student
ORDER BY age ASC
LIMIT 1;



7. Update a Student's Major for student_id = 2.

UPDATE Student
SET major = 'New Major'
WHERE student_id = 2;


8. Delete a Student Record with student_id = 6.

DELETE FROM Student
WHERE student_id = 6;


9. Count the Number of Students in Each Major where grade = 'A'.

SELECT major, COUNT(*) AS student_count
FROM Student
WHERE grade = 'A'
GROUP BY major;


10. Count the Number of Students in Each Grade with a Count Greater Than 2.



SELECT grade, COUNT(*) AS grade_count
FROM Student
GROUP BY grade
HAVING COUNT(*) > 2;


---

2. Employee Table Operations

1. Select All Data from Employee Table.

SELECT * FROM Employee;


2. Select Employees in the IT Department.

SELECT * FROM Employee
WHERE department = 'IT';


3. Count the Number of Employees in Each Department.

SELECT department, COUNT(*) AS employee_count
FROM Employee
GROUP BY department;


4. Find the Average Salary in Each Department.

SELECT department, AVG(salary) AS average_salary
FROM Employee
GROUP BY department;


5. List Employees Hired After February 1, 2021.

SELECT * FROM Employee
WHERE hire_date > '2021-02-01';


6. Increase the Salary of Employees in the IT Department by 5000.

UPDATE Employee
SET salary = salary + 5000
WHERE department = 'IT';


7. Find the Highest Salary in Each Department.

SELECT department, MAX(salary) AS highest_salary
FROM Employee
GROUP BY department;


8. Count the Number of Employees in Each Department Having More Than 1 Employee.

SELECT department, COUNT(*) AS employee_count
FROM Employee
GROUP BY department
HAVING COUNT(*) > 1;


9. Find the Employee with the Highest and Lowest Salary.

Highest Salary:

SELECT * FROM Employee
ORDER BY salary DESC
LIMIT 1;

Lowest Salary:

SELECT * FROM Employee
ORDER BY salary ASC
LIMIT 1;



10. Delete an Employee Record with last_name = 'Dev'.

DELETE FROM Employee
WHERE last_name = 'Dev';




---

3. Operations on Eid, Ename, Address, Salary, Commission Table

1. Find Different Locations of Employees.

SELECT DISTINCT Address
FROM Employee;


2. Find Maximum and Minimum Salary.

SELECT MAX(Salary) AS max_salary, MIN(Salary) AS min_salary
FROM Employee;


3. Display Employee Table Sorted by Salary in Ascending Order.

SELECT * FROM Employee
ORDER BY Salary ASC;


4. Find Employees Living in Nasik or Pune.

SELECT * FROM Employee
WHERE Address IN ('Nasik', 'Pune');


5. Find Employees Who Don’t Receive a Commission.

SELECT * FROM Employee
WHERE Commission IS NULL;


6. Change the City of Employee Amit to Nashik.

UPDATE Employee
SET Address = 'Nashik'
WHERE Ename = 'Amit';


7. Find Employees Whose Name Starts with 'A'.

SELECT * FROM Employee
WHERE Ename LIKE 'A%';


8. Count Staff from Each City.

SELECT Address, COUNT(*) AS staff_count
FROM Employee
GROUP BY Address;


9. Find City-wise Minimum Salary.

SELECT Address, MIN(Salary) AS min_salary
FROM Employee
GROUP BY Address;


10. Find City-wise Maximum Salary Greater Than 26000.

SELECT Address, MAX(Salary) AS max_salary
FROM Employee
GROUP BY Address
HAVING MAX(Salary) > 26000;




---

Continue with Remaining Sections

The remaining sections involve creating views, performing joins, working with MongoDB, and using PL/SQL blocks for stored procedures, triggers, and exception handling. Let me know if you want detailed solutions for each section within MongoDB and PL/SQL.

Each query above corresponds to questions in your sheet, designed to match what is expected in your practical exam. Let me know if you’d like additional help with specific areas such as MongoDB commands, PL/SQL triggers, or procedures, and I can guide you further!

Let's continue with the remaining questions on the sheet. I’ll provide the specific solutions for each type of table or command.


---

4. Operations on Employee and Project Tables

Tables:

Employee table with columns Eid, Ename, Address, Salary, Commission.

Project table with columns PrNo, Addr.


Questions:

1. Find employees belonging to Mumbai City.

SELECT * FROM Employee
WHERE Address = 'Mumbai';


2. Find the employee with the maximum salary.

SELECT * FROM Employee
ORDER BY Salary DESC
LIMIT 1;


3. Display Employee table content in descending order of salary.

SELECT * FROM Employee
ORDER BY Salary DESC;


4. Find the name of the employee who does not live in Nasik or Pune.

SELECT * FROM Employee
WHERE Address NOT IN ('Nasik', 'Pune');


5. Find employees whose name ends with 'R'.

SELECT * FROM Employee
WHERE Ename LIKE '%R';


6. Count staff from each city where the count is greater than or equal to 2.

SELECT Address, COUNT(*) AS staff_count
FROM Employee
GROUP BY Address
HAVING COUNT(*) >= 2;


7. Find city-wise maximum salary.

SELECT Address, MAX(Salary) AS max_salary
FROM Employee
GROUP BY Address;


8. Find city-wise maximum salary where maximum salary is greater than 19000.

SELECT Address, MAX(Salary) AS max_salary
FROM Employee
GROUP BY Address
HAVING MAX(Salary) > 19000;


9. Count staff from Mumbai.

SELECT COUNT(*) AS staff_count
FROM Employee
WHERE Address = 'Mumbai';


10. Delete the employee who has a salary greater than 30,000.

DELETE FROM Employee
WHERE Salary > 30000;




---

5. Employee, Position, and Duty-Allocation Tables

Tables:

Employee table with columns emp_no, skill, pay_rate.

Position table with columns posting_no, skill.

Duty-allocation table with columns posting_no, emp_no, day, shift.


Questions:

1. Find duty allocation details for emp_no = 101 for April 2003.

SELECT * FROM Duty_allocation
WHERE emp_no = 101 AND day LIKE '2003-04%';


2. Find the shift details of employee named 'Bhushan'.

SELECT DA.shift, DA.day
FROM Duty_allocation DA
JOIN Employee E ON DA.emp_no = E.emp_no
WHERE E.name = 'Bhushan';


3. Find employees whose pay rate is greater than or equal to that of employee 'Ahire'.

SELECT * FROM Employee
WHERE pay_rate >= (SELECT pay_rate FROM Employee WHERE name = 'Ahire');


4. Find the names and pay rates of employees with emp_no < 1000 and pay rate greater than at least one employee with emp_no >= 1000.

SELECT emp_no, name, pay_rate
FROM Employee
WHERE emp_no < 1000 AND pay_rate > (SELECT MIN(pay_rate) FROM Employee WHERE emp_no >= 1000);


5. Find the employees with the lowest pay rate.

SELECT * FROM Employee
WHERE pay_rate = (SELECT MIN(pay_rate) FROM Employee);




---

6. Doctor and Hospital Tables

Tables:

Doctor table with columns Doctor_no, Doctor_name, Address, City.

Hospital table with columns Hospital_no, Name, Street, City.

Doc_Hosp table with columns Doctor_no, Hospital_no, Date.


Questions:

1. Find doctor details and hospital names where each doctor has visited.

SELECT D.Doctor_name, H.Name
FROM Doctor D
JOIN Doc_Hosp DH ON D.Doctor_no = DH.Doctor_no
JOIN Hospital H ON DH.Hospital_no = H.Hospital_no;


2. Find doctors who have visited hospitals in their own city.

SELECT D.Doctor_name
FROM Doctor D
JOIN Doc_Hosp DH ON D.Doctor_no = DH.Doctor_no
JOIN Hospital H ON DH.Hospital_no = H.Hospital_no
WHERE D.City = H.City;


3. Find the hospital(s) visited by "Dr. Joshi".

SELECT H.Name
FROM Hospital H
JOIN Doc_Hosp DH ON H.Hospital_no = DH.Hospital_no
JOIN Doctor D ON DH.Doctor_no = D.Doctor_no
WHERE D.Doctor_name = 'Dr. Joshi';


4. Count the number of doctors who visited "Shree Clinic" on March 1, 2023.

SELECT COUNT(*) AS doctor_count
FROM Doc_Hosp DH
JOIN Hospital H ON DH.Hospital_no = H.Hospital_no
WHERE H.Name = 'Shree Clinic' AND DH.Date = '2023-03-01';


5. Find how many times "Dr. Joshi" visited "Shree Clinic".

SELECT COUNT(*) AS visit_count
FROM Doc_Hosp DH
JOIN Hospital H ON DH.Hospital_no = H.Hospital_no
JOIN Doctor D ON DH.Doctor_no = D.Doctor_no
WHERE D.Doctor_name = 'Dr. Joshi' AND H.Name = 'Shree Clinic';




---

7. Join and View Operations

Tables:

Student with columns StudentID, StudentName, CourseID.

Course with columns CourseID, CourseName.


Questions:

1. Demonstrate different types of joins (Inner, Left, Right, Full Outer).

-- Inner Join
SELECT S.StudentID, S.StudentName, C.CourseName
FROM Student S
INNER JOIN Course C ON S.CourseID = C.CourseID;

-- Left Join
SELECT S.StudentID, S.StudentName, C.CourseName
FROM Student S
LEFT JOIN Course C ON S.CourseID = C.CourseID;

-- Right Join
SELECT S.StudentID, S.StudentName, C.CourseName
FROM Student S
RIGHT JOIN Course C ON S.CourseID = C.CourseID;

-- Full Outer Join (if supported)
SELECT S.StudentID, S.StudentName, C.CourseName
FROM Student S
FULL OUTER JOIN Course C ON S.CourseID = C.CourseID;


2. Create and display different views.

CREATE VIEW StudentCourse AS
SELECT S.StudentID, S.StudentName, C.CourseName
FROM Student S
JOIN Course C ON S.CourseID = C.CourseID;

SELECT * FROM StudentCourse;




---

This covers questions related to joins, views, and aggregate functions, providing the necessary SQL solutions for each requirement in your practical sheet. Let me know if you need further help on any remaining parts, such as triggers, stored procedures, MongoDB operations, or PL/SQL blocks!

Let's continue with the remaining questions, covering triggers, stored procedures, PL/SQL blocks, cursors, JDBC connectivity, and MongoDB operations.


---

8. Triggers on Student Table

Table:

student with columns Rollno, Name, Address, Marks.


Questions:

1. Create different triggers (After Insertion, After Updation, After Deletion, Before Insertion).

Trigger After Insertion:

CREATE TRIGGER trg_after_insert
AFTER INSERT ON student
FOR EACH ROW
BEGIN
    DBMS_OUTPUT.PUT_LINE('New student added: ' || :new.Name);
END;

Trigger After Updation:

CREATE TRIGGER trg_after_update
AFTER UPDATE ON student
FOR EACH ROW
BEGIN
    DBMS_OUTPUT.PUT_LINE('Student details updated for: ' || :new.Name);
END;

Trigger After Deletion:

CREATE TRIGGER trg_after_delete
AFTER DELETE ON student
FOR EACH ROW
BEGIN
    DBMS_OUTPUT.PUT_LINE('Student removed: ' || :old.Name);
END;

Trigger Before Insertion:

CREATE TRIGGER trg_before_insert
BEFORE INSERT ON student
FOR EACH ROW
BEGIN
    DBMS_OUTPUT.PUT_LINE('Adding a new student: ' || :new.Name);
END;



2. Create and Display Views.

CREATE VIEW StudentView AS
SELECT Rollno, Name, Marks
FROM student;

SELECT * FROM StudentView;




---

9. PL/SQL Code Block with Control Structure and Exception Handling

Tables:

Borrower with columns Roll_no, Name, DateofIssue, NameofBook, Status.

Fine with columns Roll_no, Date, Amt.


Question:

Write a PL/SQL code block that accepts Roll_no and NameofBook from the user, checks the number of days (from DateofIssue), calculates a fine based on the days overdue, and updates the status.

DECLARE
    v_roll_no NUMBER := &Roll_no;
    v_book_name VARCHAR2(100) := '&NameofBook';
    v_date_of_issue DATE;
    v_days NUMBER;
    v_fine_amt NUMBER;
    overdue_exception EXCEPTION;

BEGIN
    -- Retrieve the date of issue for the given roll number and book
    SELECT DateofIssue INTO v_date_of_issue
    FROM Borrower
    WHERE Roll_no = v_roll_no AND NameofBook = v_book_name;

    -- Calculate the number of days overdue
    v_days := SYSDATE - v_date_of_issue;

    IF v_days BETWEEN 15 AND 30 THEN
        v_fine_amt := v_days * 5;
    ELSIF v_days > 30 THEN
        v_fine_amt := v_days * 50;
    ELSE
        v_fine_amt := 0;
    END IF;

    -- Update status to Returned (R) and record the fine if applicable
    UPDATE Borrower
    SET Status = 'R'
    WHERE Roll_no = v_roll_no AND NameofBook = v_book_name;

    IF v_fine_amt > 0 THEN
        INSERT INTO Fine (Roll_no, Date, Amt)
        VALUES (v_roll_no, SYSDATE, v_fine_amt);
    END IF;

    DBMS_OUTPUT.PUT_LINE('Fine amount: ' || v_fine_amt);

EXCEPTION
    WHEN overdue_exception THEN
        DBMS_OUTPUT.PUT_LINE('Error calculating overdue fine.');
END;


---

10. Stored Procedure and Function for Grade Classification

Tables:

Stud_Marks with columns Roll, name, total_marks.

Result with columns Roll, Name, Class.


Question:

Write a stored procedure for student grade categorization based on marks.

1. Stored Procedure for Categorizing Students:

CREATE OR REPLACE PROCEDURE proc_Grade (p_marks IN NUMBER, p_class OUT VARCHAR2) AS
BEGIN
    IF p_marks BETWEEN 990 AND 1500 THEN
        p_class := 'Distinction';
    ELSIF p_marks BETWEEN 900 AND 989 THEN
        p_class := 'First Class';
    ELSIF p_marks BETWEEN 825 AND 899 THEN
        p_class := 'Higher Second Class';
    ELSE
        p_class := 'Pass';
    END IF;
END proc_Grade;


2. PL/SQL Block to Call the Procedure:

DECLARE
    v_roll NUMBER := 1;
    v_marks NUMBER;
    v_class VARCHAR2(20);
BEGIN
    -- Get student marks
    SELECT total_marks INTO v_marks FROM Stud_Marks WHERE Roll = v_roll;

    -- Call the procedure to get class
    proc_Grade(v_marks, v_class);

    -- Insert into Result table
    INSERT INTO Result (Roll, Name, Class)
    VALUES (v_roll, (SELECT name FROM Stud_Marks WHERE Roll = v_roll), v_class);
END;




---

11. Cursor Operations

Tables:

N_RollCall and O_RollCall tables for roll call data.


Question:

Write a PL/SQL block using a parameterized cursor to merge data from N_RollCall to O_RollCall.

DECLARE
    CURSOR roll_cursor (p_roll NUMBER) IS
        SELECT * FROM N_RollCall WHERE roll_no = p_roll;

    v_record N_RollCall%ROWTYPE;
BEGIN
    FOR v_record IN roll_cursor(1) LOOP
        -- Check if record exists in O_RollCall
        IF NOT EXISTS (SELECT 1 FROM O_RollCall WHERE roll_no = v_record.roll_no) THEN
            INSERT INTO O_RollCall (roll_no, name)
            VALUES (v_record.roll_no, v_record.name);
        END IF;
    END LOOP;
END;


---

12. JDBC Connectivity Example

To perform JDBC connectivity in Java, set up your connection using JDBC APIs.

1. JDBC Code Example:

import java.sql.*;

public class DatabaseConnection {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost:3306/your_database";
        String username = "root";
        String password = "password";

        try (Connection conn = DriverManager.getConnection(url, username, password)) {
            System.out.println("Connected to database!");

            String query = "SELECT * FROM Student";
            Statement stmt = conn.createStatement();
            ResultSet rs = stmt.executeQuery(query);

            while (rs.next()) {
                System.out.println("Roll No: " + rs.getInt("Rollno") +
                                   ", Name: " + rs.getString("Name"));
            }
        } catch (SQLException e) {
            System.out.println("Connection failure.");
            e.printStackTrace();
        }
    }
}




---

13. MongoDB Queries

To perform MongoDB operations, connect to the database, and use commands similar to these examples.

Questions:

1. Find All Students.

db.Student.find({});


2. Find Students in a Specific Major Computer Science.

db.Student.find({ major: "Computer Science" });


3. Count the Number of Students in Each Major.

db.Student.aggregate([
    { $group: { _id: "$major", count: { $sum: 1 } } }
]);


4. Find Students with a Specific Grade A.

db.Student.find({ grade: "A" });


5. Count the Number of Students in Each Grade Having More Than 2 Students.

db.Student.aggregate([
    { $group: { _id: "$grade", count: { $sum: 1 } } },
    { $match: { count: { $gt: 2 } } }
]);


6. List Students Ordered by Age.

db.Student.find().sort({ age: 1 });


7. Update a Student’s Major for Emily.

db.Student.updateOne({ first_name: "Emily" }, { $set: { major: "New Major" } });


8. Find the Oldest Student.

db.Student.find().sort({ age: -1 }).limit(1);


9. Delete a Student Record by student_id = 6.

db.Student.deleteOne({ student_id: 6 });




---

This should cover all the remaining questions! Each section is solved with specific SQL, PL/SQL, JDBC, and MongoDB commands that match the requirements in your sheet. Let me know if you need further clarification or additional examples. Good luck with your practical!

Apologies for missing that! Let's cover Question Set 14, which involves operations on an emp table.

14. Operations on the emp Table

Table structure:

emp with columns emp_id, emp_name, dept_name, salary, gender.


Questions and SQL Solutions:

1. Display all records from the emp table.

SELECT * FROM emp;


2. Display distinct department names.

SELECT DISTINCT dept_name FROM emp;


3. Find the total number of employees in each department.

SELECT dept_name, COUNT(*) AS total_employees
FROM emp
GROUP BY dept_name;


4. Calculate the total salary in each department.

SELECT dept_name, SUM(salary) AS total_salary
FROM emp
GROUP BY dept_name;


5. Calculate the total salary of female employees in each department.

SELECT dept_name, SUM(salary) AS total_female_salary
FROM emp
WHERE gender = 'F'
GROUP BY dept_name;


6. Count the number of male employees in each department.

SELECT dept_name, COUNT(*) AS male_employee_count
FROM emp
WHERE gender = 'M'
GROUP BY dept_name;


7. Find the total number of male employees.

SELECT COUNT(*) AS total_male_employees
FROM emp
WHERE gender = 'M';


8. Find the minimum salary in the institute.

SELECT MIN(salary) AS minimum_salary
FROM emp;


9. Find the maximum salary in the Comp department.

SELECT MAX(salary) AS max_salary
FROM emp
WHERE dept_name = 'Comp';


10. Find all male employees, sorted in ascending order by emp_name.

SELECT * FROM emp
WHERE gender = 'M'
ORDER BY emp_name ASC;


11. Calculate total salary, max salary, and min salary using MapReduce (for MongoDB).



If you’re using MongoDB, here’s how you could approach these calculations using MapReduce:

db.emp.mapReduce(
    function() {
        emit("salary_stats", { total: this.salary, max: this.salary, min: this.salary });
    },
    function(key, values) {
        return {
            total: Array.sum(values.map(v => v.total)),
            max: Math.max.apply(Math, values.map(v => v.max)),
            min: Math.min.apply(Math, values.map(v => v.min))
        };
    },
    {
        out: "salary_stats_result"
    }
);

// To view the results:
db.salary_stats_result.find();


---

This completes Question Set 14 along with a MapReduce operation for the last part. Let me know if there’s anything else specific you'd like to discuss or if you need any more assistance with MongoDB or advanced SQL queries.

To solve Question 15, where we need to find the total salary, maximum salary, and minimum salary using MapReduce on the emp collection in MongoDB, here’s how you can set it up.

In MongoDB, MapReduce functions can be used to perform aggregation tasks like summing values, finding maximums, and finding minimums.

MongoDB MapReduce Solution for Salary Aggregation

1. Map Function: This function emits each employee's salary as a document that includes total, max, and min values.


2. Reduce Function: This function combines the emitted documents by summing the total salaries and finding the max and min salary values.


3. Output: Store the results in a collection named salary_stats_result.



Here’s the MapReduce code:

db.emp.mapReduce(
    function() {
        // Emit each salary as a document with total, max, and min fields
        emit("salary_stats", { total: this.salary, max: this.salary, min: this.salary });
    },
    function(key, values) {
        // Reduce function: aggregate total, find max and min salaries
        return {
            total: Array.sum(values.map(v => v.total)),
            max: Math.max.apply(Math, values.map(v => v.max)),
            min: Math.min.apply(Math, values.map(v => v.min))
        };
    },
    {
        out: "salary_stats_result"
    }
);

// To view the results:
db.salary_stats_result.find();

Explanation

Map Function: Emits each document's salary with keys for total, max, and min.

Reduce Function: Iterates over each value in the emitted documents, calculating:

Total Salary by summing all total values.

Max Salary by finding the highest max value in the group.

Min Salary by finding the lowest min value in the group.


Output Collection: Results are stored in salary_stats_result.


Viewing Results

After running the MapReduce, retrieve the aggregated salary statistics:

db.salary_stats_result.find().pretty();

This will display a document like:

{
    "_id": "salary_stats",
    "value": {
        "total": 250000,  // Example total of all salaries
        "max": 90000,     // Example maximum salary
        "min": 20000      // Example minimum salary
    }
}

This approach provides the total, maximum, and minimum salaries across the emp collection using MongoDB’s MapReduce functionality.
