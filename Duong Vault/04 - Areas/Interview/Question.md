## 1. Outline
- OOP, DSA
- C++
- Golang: Go routine, garbage collector, go template, gin framwork
- Clean Architecture, Hub Architecture
- bcrypt, jwt, cookie, session
- Docker, cors
- Database mirgration
- SQL server

## 2. Detail

**OOP and DSA:**

1. Explain the principles of Object-Oriented Programming (OOP) and give examples of each.
		- Abstraction
		- Encapsulation
		- Inheritance
		- Polymorphism
2. What is polymorphism in OOP? How is it implemented in different programming languages? -> Là việc một hành vi có tên gọi giống nhau nhưng thực hiện các hành động khác nhau
3. Describe the differences between a stack and a queue data structure. Provide use cases for each. -> Stack FIFO, Queue LIFO
4. Explain the concept of Big O notation and its significance in data structures and algorithms. -> đại diện cho độ phức tạp của thuật toán (số vòng lặp, thời gian chạy), độ phức tạp càng thấp thì thuật toán càng tối ưu
5. How would you implement a binary search tree in a programming language of your choice?
	```
		struct Node {
			int value;
			Node* left;
			Node* right;
		}
	```
1. Compare and contrast arrays and linked lists. When would you use one over the other? -> Các phần tử trong array thì nằm liên tiếp trong bộ nhớ, còn linked list có thể nằm ngẫu nhiên (cần thêm bộ nhớ để kết nối các vùng nhớ này lại). Array được dùng khi kích thước tập dữ liệu là nhỏ và cố định. Linked list được dùng cho dữ liệu lớn và có thể tăng thêm, để tận dụng được bộ nhớ.
1. What is an abstract class, and why might you use one in your code?
	Lớp trừu tượng là lớp có ít nhất một phương thức trừu tượng. Lớp trừu tượng không thể dùng để tạo object mà chỉ tạo được con trỏ của lớp này. 

**C++:**

1. What is the difference between C and C++? Can you give an example of a feature in C++ that is not present in C?
2. Explain the concept of constructors and destructors in C++.
3. What is the purpose of the "this" pointer in C++?
4. Discuss the differences between pass-by-value and pass-by-reference in C++. When would you use each?
5. How do you manage memory in C++? What is the significance of RAII (Resource Acquisition Is Initialization)?
6. What is operator overloading, and provide an example of its use.
7. Describe the difference between virtual functions and pure virtual functions.

**Golang:**

1. Explain what a goroutine is in Go. How does it differ from traditional threads?
	Goroutine cho phép sử dụng concurrency trong golang. Goroutine tương đương với một thread nhẹ. Goroutine được chạy một cách độc lập và đồng thời với các goroutine khác trong hệ thống
	- Goroutine: nhẹ, nhanh, chiếm ít tài nguyên, dễ sử dụng, an toàn và ít gặp lỗi
	- Thread thông thường: nặng, chậm, chiếm nhiều tài nguyên, khó sử dụng, không an toàn và dễ gặp lỗi
1. What is garbage collection in Go, and why is it important?
2. Describe the role of Go templates in web development. Provide an example of using Go templates.
3. What is the Gin framework in Go, and what are its advantages in building web applications?
4. How does Go handle concurrent programming, and what synchronization mechanisms are available?
5. Discuss the benefits and drawbacks of using channels for communication between goroutines.

**Clean Architecture and Hexagonal (Ports and Adapters) Architecture:**

1. What is Clean Architecture, and how does it differ from traditional layered architecture?
2. Explain the concepts of "ports" and "adapters" in Hexagonal Architecture. Why are they important?
3. How does Clean Architecture promote testability and maintainability in software projects?
4. Discuss the SOLID principles and their relevance in Clean Architecture.
5. Can you give an example of a real-world application that would benefit from Clean Architecture?

**Security and Authentication (bcrypt, JWT, Cookie, Session):**

1. What is bcrypt, and why is it used for password hashing?
2. Explain the purpose of JWT (JSON Web Tokens) in web authentication. How is it different from traditional session-based authentication?
3. Describe the advantages and disadvantages of using cookies for session management.
4. What is a session in web development, and how is it typically implemented?
5. How can you secure sensitive data in transit and at rest in a web application?
6. What are common security vulnerabilities in web applications, and how can they be mitigated?

**Docker and CORS:**

1. What is Docker, and how does it facilitate containerization of applications?
2. Explain the differences between a Docker image and a Docker container.
3. How do you manage multi-container applications using Docker Compose?
4. What is CORS (Cross-Origin Resource Sharing) in web development, and why is it necessary?
5. How can you configure CORS policies in a web application to enhance security?
6. Discuss the challenges and solutions related to deploying Docker containers in a production environment.

**Database Migration and SQL Server:**

1. What is database migration, and why is it important in software development?
2. Describe the typical workflow for performing database migrations in a project.
3. What tools and frameworks are commonly used for database migrations?
4. Explain the concept of a database schema and how it relates to SQL Server.
5. Discuss the differences between SQL Server and other relational database management systems.
6. How can you optimize SQL Server queries for better performance?

These questions cover a range of topics and should help you assess a candidate's knowledge in each area during an interview. Depending on the role and specific requirements, you can tailor the questions to focus on the most relevant topics.