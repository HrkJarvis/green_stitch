# green_stitch
How to use this code?
Make sure you have Java 8 and Maven installed

Fork this repository and clone it

$ git clone https://github.com/<your-user>/spring-boot-jwt
Navigate into the folder
$ cd spring-boot-jwt
Install dependencies
$ mvn install
Run the project
$ mvn spring-boot:run
Navigate to http://localhost:8080/swagger-ui.html in your browser to check everything is working correctly. You can change the default port in the application.yml file
server:
  port: 8080
Make a GET request to /users/me to check you're not authenticated. You should receive a response with a 403 with an Access Denied message since you haven't set your valid JWT token yet
$ curl -X GET http://localhost:8080/users/me
Make a POST request to /users/signin with the default admin user we programatically created to get a valid JWT token
$ curl -X POST 'http://localhost:8080/users/signin?username=admin&password=admin'
Add the JWT token as a Header parameter and make the initial GET request to /users/me again
$ curl -X GET http://localhost:8080/users/me -H 'Authorization: Bearer <JWT_TOKEN>'
And that's it, congrats! You should get a similar response to this one, meaning that you're now authenticated
{
  "id": 1,
  "username": "admin",
  "email": "admin@email.com",
  "roles": [
    "ROLE_ADMIN"
  ]
}
