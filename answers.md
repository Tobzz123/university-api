# raccoopack-backend-challenge
Ola's Backend Technical Challenge for RaccooPack Media

**Challenge Answers**
Answer #1: Backend Tech Stack


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


**Bonus Requirement**
Unit Tests: I would use NUnit or any other testing frameworks like xUnit or MSTest. This would allow me to set up tests using AAA (Arrange, Act, Assert) methods to test the endpoint for enrolling a student in a course. Using a testing environment like this means being mindful of different dependencies, like the database for example. I would have to employ the use of mocking for the database (Moq framework), meaning I'd only test the behaviours of calls made to the database, and making sure the request to the specified endpoint is returning back the correct data.

Swagger or Postman: I would make use of Swagger or Postman to test the API endpoint to be used when a student is enrolling for a course,. For a student to enrol in a course, this means the course would get added to the student's list of courses. On the database side, we should check the Registrations Table for a record that corresponds to the course ID and student ID passed in by sending a get request to that specific endpoint.

**Link Diagrams**




**Time Spent on Challenge**




**Feedback**
