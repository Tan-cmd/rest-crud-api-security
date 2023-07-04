# rest-crud-api-security
- In this project, I have initialized libraries such as Spring Data JPA, Spring Boot DevTools, Security, and the MySQL Driver to manipulate the project. 
- After initializing the project, I create packages such as Rest, Dao, Entity, Security, and Service to contain the corresponding classes. In addition, I also configure the application.properties file to connect to the database. 
- In the entity package, I created a class named Employee and used the @Entity annotation to mark this class, and @Table matches the table name in the database. There are also other annotations for the fields.
- Then I created an interface class in the dao package. In this class, I use JPARepository to manipulate add, delete, edit, and read API.
- Then I created an interface class (EmployeeService) and a class (EmployeeServiceImpl). In interface class, I write methods and in class, I create method from interface class. Then I use @Service annotation and declare an interface class (from dao package) to add, remove, edit, and read API methods. 
- Then I created an class in the rest package and use  @RestController and @RequestMapping annotations. Then declare the interface class (EmployeeService) and instantiate the constructor with arguments, then use the @Autowired annotation for injection. Then I call the method from the interface class that has been handled by the class (EmployeeServiceImpl).
  + getEmployees method: This method handles a GET request to "/employee" and retrieves a list of all employees from the employeeService.
  + findById method: This method handles a GET request to "/employee/{theId}" and retrieves an employee by their ID from the employeeService. If the employee is not found, it throws a RuntimeException.
  + addEmployee method: This method handles a POST request to "/employee" and adds a new employee. The employee object is received in the request body (@RequestBody) and is saved using the employeeService. The saved employee is then returned.
  + updateEmploy method: This method handles a PUT request to "/employee" and updates an existing employee. The updated employee object is received in the request body (@RequestBody) and is saved using the employeeService. The saved employee is then returned.
  + deleteEmploy method: This method handles a DELETE request to "/employee/{theId}" and deletes an employee by their ID. It first retrieves the employee from the employeeService and throws a RuntimeException if the employee is not found. Then, it calls the delete method on the employeeService to delete the employee. It returns a message indicating the deleted employee ID.
- After testing the functionality, I created a class in the security package and annotated @Configuration. In this class, I have created two methods and @Bean annotation.
  + The first method (userDetailsManager): This method configures and returns an instance of JdbcUserDetailsManager. It takes a DataSource as a parameter, which is used to connect to the database. It sets the SQL queries to retrieve user details and authorities/roles by username.
  + The Second method (filterChain): This method configures the security filter chain using the HttpSecurity object. It sets up authorization rules based on the HTTP request methods and the roles required to access specific URLs. It enables HTTP basic authentication and disables Cross-Site Request Forgery (CSRF) protection.
  + The Employees (Username: john, Password:test123) can view and find information.
  + The managers (Username: mary, Password:test123) can perform the functions of the employee and in addition add and edit.
  + Administrators (Username: susan, Password:test123) can do the above two user functions and add delete function.
- I encrypted the password with bcrypt.
