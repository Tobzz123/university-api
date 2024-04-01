**System Design Analysis**
Answer #1: Backend Tech Stack

**Rationale & Assumptions**

Faculty Table 
- Setup a profile for description of experiences - **Assumption** - Profile Description is just a varchar of text
- Create courses with course ID, credits, course fees, learning objectives, list required
course materials, course capacity - **Assumption** - Course ID is a varchar because of the abbreviation of program and number to specify the course: E.G BUSN 1022 - Business Fundamentals, BUSN 2034 - Microeconomics
- Relationship between Faculty & Course -  **Assumption** -  1 to Many
- Create Class Schedule for courses - **Assumption** - CREATE operation Relationship between Class Schedule & Courses - One course has many Class Schedules, but One Class Schedule is Unique to a Specific course. 1 to Many, 1 to 1 
- Flag classes as cancelled or moved -  **Assumption** - Course with specific date & time in Class Schedule - Boolean Flag UPDATE operation
- Delete classes - DELETE operation
- Add and remove students from classes they have access to -  **Assumption** - Student table defined
- Leave private notes about a student in their class which are visible to the specific student and all faculty staff members -  **Assumption** - Use student's id for unique notes
- Add and edit physical descriptions, demographic information, and past education records about the student when they are registered into the system.  **Assumption** - This can be broken into separate fields.
Gender, Birth Day, Ethnicity, High School, Highest Education Achieved, etc 

Course Table
- CourseID (Varchar, Primary key)  **Assumption**
- Credits - Double  **Assumption**
- Course Fees - Double  **Assumption**
- Learning Objective (Varchar(500))  **Assumption**
- Course Materials (List of Strings)  **Assumption**
- Course Capacity - int  **Assumption**
- Question: Would I have a DateTime in the object definition for this table or in the Class Schedule table? Most likely the class schedule table  **Assumption**

Student Table
- View Courses they are enrolled in -  **Assumption** - Each student object has a list of courses that is updated everytime they enroll
- View Information about the Courses they are enrolled in -  **Assumption** - Returns certain course columns - ID, credits, fees, learning objectives, required  course materials
- View a schedule of classes they are to attend -  **Assumption** - Different from Class Schedule for each course. This schedule has different classes for every course the student is enrolled in
- View notes from faculty -  **Assumption** - Depending on the boolean flag for the note, student will be able to see the note or not
- Enroll in new courses -  **Assumption** - Add to Course List
- Dropout from Courses -   **Assumption** - Remove from Course List

Schedule Table
- Each Class Schedule Object is for a Course **Assumption**
- Course ID as FK  **Assumption**
- Number of occurences in a week as a column  **Assumption**

Class Table (List of Classes)
- class_id  **Assumption**
- FK course_id  **Assumption**
- schedule_date_time datetime  **Assumption**
- class_flag = 0 = normal, 1 = cancelled, 2 = moved  **Assumption**

Enrollment Table
 **Assumption** - Join Table that represents Many to Many relationship between Students and Classes
- student_id FK 
- class_id FK

Registrations Table
 **Assumption** - Join Table that represents Many to Many relationship between Students and Courses
- student_id FK 
- course_id FK

Notes Table
- faculty_id
- student_id
- note_description
- is_visible_to_student = 0 No, 1 = Yes  **Assumption** - Flag that represents if a student can view the note or not - This would be processed in business logic layer


A.) Programming Language Options:
- TypeScript in Node.js environment: TypeScript can add strong typing to JavaScript, which helps catch errors during development. Node.js is a popular choice for building scalable and real-time applications.
- C# in Visual Studio Environment: C# is a strongly typed language, which can help catch errors at compile time and improve code maintainability. 


B.) Database Management System Options:
- Relational Database: Given the structured nature of university data (e.g., courses, schedules, student records), a relational database system like Microsoft SQL Server, PostgreSQL or MySQL is a solid choice.

C.) API Framework Options:
 - Express.js is a lightweight and flexible web application framework suitable for building RESTful APIs.
 - ASP.NET Web API is very structured and suitable for building simple and advanced RESTful APIs. This can streamline development and deployment.
 - By using these frameworks, we can provide data access to the frontend to be displayed on a UI by using appropriate HTTP methods (GET, POST, PUT, DELETE) for CRUD operations.

D.) Cloud Hosting
 - Considering the potential for high traffic, especially during registration periods, using load balancing for the API and cloud-based hosting solutions (AWS, Azure, Google Cloud) for scalability.




**API Endpoint Development Considerations**
 - Being created in the .NET ecosystem
 - Making use of Entity Framework to make database objects as entities in .NET environment.
 - This means we are using a Database first approach, and there are already connections to the database in place
 - This also means models and DB context have been scaffolded from the database. The context contains DBSet objects representing database tables
 - There is a BLL & DAL layer 


**Bonus Requirement**

Unit Tests: I would use NUnit or any other testing frameworks like xUnit or MSTest. This would allow me to set up tests using AAA (Arrange, Act, Assert) methods to test the endpoint for enrolling a student in a course. Using a testing environment like this means being mindful of different dependencies, like the database for example. I would have to employ the use of mocking for the database (Moq framework), meaning I'd only test the behaviours of calls made to the database, and making sure the request to the specified endpoint is returning back the correct data.

Swagger or Postman: I would make use of Swagger or Postman to test the API endpoint to be used when a student is enrolling for a course,. For a student to enrol in a course, this means the course would get added to the student's list of courses. On the database side, we should check the Registrations Table for a record that corresponds to the course ID and student ID passed in by sending a get request to that specific endpoint.



**Time Spent on Design**

ERD: 38mins 9 seconds
Rest of project: 1 hour 38 mins 14 seconds
Bonus Requirements: 1 hour 39 mins 8 seconds

Total: 3 hours 55 mins 31 seconds



**Feedback**

This was a really fun assessment. What I enjoyed was the thought process that had to go in to think about the Database Schema, and how to approach designing the API. 
