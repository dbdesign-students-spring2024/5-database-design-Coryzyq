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

2NF - The composite keys are `assignment_id` and `student_id`, but some attributes such as `due_date` is only a fact about the `assignment_id` rather than the whole composite key.

3NF - In terms of 3NF, the `professor_email` is dependent on `professor` rather than the composite key here. 

## TABLES CONTAINING THE 4NF-COMPLIANT VERSION OF THE DATA SET

### Assignments Table
| assignment_id | course_id | due_date | assignment_topic                | 
| :------------ | :-------- | :------- | :----------------------------—- |
| 1             | 1         | 23.02.21 | Data normalization              |
| 2             | 2         | 18.11.21 | Single table queries            |
| 5             | 3         | 05.05.21 | Python and pandas               |
| 4             | 4         | 04.07.21 | Spreadsheet aggregate functions |
| ...           | ...       | ...      | ...                             |

### Students Table
| student_id | student_name          |
| :--------- | :-------------------- |
| 1          | Cory Zou              |
| 2          | Arnold Schwarzenegger |
| 4          | Spongebob Squarepants |
| 7          | Elon Musk             |
|...         | ...                   |

### Student Assignments Table
| student_id | assignment_id | grade |
| :--------- | :------------ | :---- |
| 1          | 1             | 80    |
| 2          | 4             | 65    |
| 2          | 5             | 92    |
| 4          | 1             | 75    |
| 7          | 2             | 25    |
| ...        | ...           | ...   |

### Courses Table:
| course_id | course_name               |
|:--------- | :------------------------ |
|1          | Intro to Data Science     |
|2          | Intro to Computer Science |
|3          | Causal Inference          |
|4          | Data Science for Everyone |
|...        | ...                       |

### Professors Table
| professor_id | professor_name | professor_email   |
| :----------- | :------------- | :---------------- |
| 1            | Melvin         | l.melvin@foo.edu  |
| 2            | Logston        | e.logston@foo.edu |
| 3            | Nevarez        | i.nevarez@foo.edu |
|...           | ...            | ...               |

### Sections Table
| section_id | professor_id | course_id | classroom | relevant_reading    |
|:---------- | :----------- | :-------- | :-------- | :------------------ |
|1           | 1            | 1         | WWH 101   | Deumlich Chapter 3  |
|2           | 2            | 2         | 60FA 314  | Dümmlers Chapter 11 |
|3           | 2            | 4         | 60FA 314  | Dümmlers Chapter 14 |
|4           | 3            | 3         | WWH 201   | Zehnder Page 87     |
|...         | ...          | ...       | ...       | ...                 |

## ER DIAGRAM
[draw.io](/images/ER_diagram.svg)

## WHAT CHANGES I HAVE MADE TO MAKE THE DATA TABLE 4NF COMPLIANT
- Assignments Table with assignment_id, course_id, due_date, and assignment_topic. Assignment_id and course_id will be the composite key. 

- Students Table with student_id and student name. Student_id will be primary key.

- Student Assignments Table with student_id and assignment_id as acomposite primary keys, grade as attribute.

- Courses Table with course_id and course_name. Course_id will be primary key.

- Professors Table with professor_id, professor_name, and professor_email. Professor_id will be primary key.

- Sections Table with section_id, professor_id, course_id, classroom, and relevant_reading. Section_id and professor_id will be composite keys. 

- Courses Table with course_id and course_name. Course_id will be primary key.

These tables will eilimate multivalued dependency and partial dependencies in the original data table.
The resulting data tables will alsominimize data redendancy and prevent update anomalies.