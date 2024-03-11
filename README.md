# REPORT

## ORIGINAL TABLE
| assignment_id | student_id | due_date | professor | assignment_topic                | classroom | grade | relevant_reading    | professor_email   |
| :------------ | :--------- | :------- | :-------- | :------------------------------ | :-------- | :---- | :------------------ | :---------------- |
| 1             | 1          | 23.02.21 | Melvin    | Data normalization              | WWH 101   | 80    | Deumlich Chapter 3  | l.melvin@foo.edu  |
| 2             | 7          | 18.11.21 | Logston   | Single table queries            | 60FA 314  | 25    | Dümmlers Chapter 11 | e.logston@foo.edu |
| 1             | 4          | 23.02.21 | Melvin    | Data normalization              | WWH 101   | 75    | Deumlich Chapter 3  | l.melvin@foo.edu  |
| 5             | 2          | 05.05.21 | Logston   | Python and pandas               | 60FA 314  | 92    | Dümmlers Chapter 14 | e.logston@foo.edu |
| 4             | 2          | 04.07.21 | Nevarez   | Spreadsheet aggregate functions | WWH 201   | 65    | Zehnder Page 87     | i.nevarez@foo.edu |
| ...           | ...        | ...      | ...       | ...                             | ...       | ...   | ...                 | ...               |


## WHAT MAKES THE ORIGINAL DATA SET NOT COMPLIANT WITH 4NF

Given that the table is already 1NF compliant, we will test 2NF and 3NF first.

2NF - The composite keys are `assignment_id` and `student_id`, but some attributes such as due_date is only a fact about the assignment_id rather than the whole composite key.

3NF - In terms of 3NF, the `professor_email` is dependent on `professor` rather than the composite key here. 

## TABLES CONTAINING THE 4NF-COMPLIANT VERSION OF THE DATA SET
| assignment_id | due_date | assignment_topic                |
| :------------ | :------- | :------------------------------ |
| 1             | 23.02.21 | Data normalization              |
| 2             | 18.11.21 | Single table queries            |
| 3             | 05.05.21 | Python and pandas               |
| 4             | 04.07.21 | Spreadsheet aggregate functions |

## WHAT CHANGES I HAVE MADE TO MAKE THE DATA TABLE 4NF COMPLIANT
table with assignment_id and due date

student table with student_id and student name

studentassignment table with student_id and assignment_id as acomposite primary key, grade as attribute

professor table with professor_id and professor_email

section table with section_id as primary key and professor_id, course_id, classroom, assignment_topic, and relevant_reading.

course table with course_id and course_name