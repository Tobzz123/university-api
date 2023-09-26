**Bonus Challenges**


**Challenge 1: Endpoint Documentation**

api/faculty/CreateCourse (HTTPPost)
 - Purpose: For a faculty to create a course:
 - Required Parameters: Course object and it's fields are sent in request body (Credits, Course Fees, Learning Objectives, Required Course Materials, Course Capacity)
 - Expected Reponses: OK(HTTP 200) or Bad Request (HTTP 400)

api/faculty/DeleteClassByID/{id} (HTTPDelete)
 - Purpose: For a faculty to delete a class by ID
 - Required Parameters: The ID of a class
 - Expected Responses: OK status with True or False indicating if the delete operation was succesful or not OR Not Found (HTTP 404)

api/faculty/FlagClass/{id}/{value} (HTTPPut)
 - Purpose: To flag a class as cancelled or moved
 - Required Parameters: The ID of a class and the bit value that will update the class flag
 - Expected Responses: OK status with the bit value that represents the updated value OR Not Found (HTTP 404)

api/student/GetCoursesById/{id} (HTTPGet)
 - Purpose: For a student to view the courses they're enrolled in
 - Required Parameters: The id of the student
 - Expected Responses: OK status that displays list of student courses or NotFound (HTTP404)

api/student/DropCourse/{id}/{course_name} (HTTPDelete)
 - Purpose: For a student to dropout from any courses they are enrolled in
 - Required Parameters: Id of student and name of course
 - Expected Responses: OK representing succesful operation, or Not Found if the course isn't in the student's list of courses or the student does not exist


**Challenge 2: Search Optimization**

Searching through a million elements everytime can be very tasking, and it becomes challenging because the operations are done externally with a database instead of in memory data. This means paying attention to the different choke points of not just the database, but the API handling the requests and the responses.


**Data Indexing**

Bottleneck: Without proper indexing, queries searching for students based on various details can be slow, especially when filtering by non-indexed fields.

Strategies: Identify the most frequently used search criteria and create appropriate indexes for those columns

**Server Load**

Bottleneck: Handling 1 million student records requires a scalable infrastructure to avoid performance degradation as the dataset grows.

Strategies: Load Balancing - Implement load balancing to distribute incoming requests across multiple servers to ensure even distribution of the processing load.

**Response Data Size**

Bottleneck: Returning a large amount of data in responses can affect both server and client performance.

Strategies: Data Truncation - This involves retrieving and returning only the necessary fields from the database instead of returning all student details.
