# green_stitch
# How to use this code?<br />
Make sure you have Java 8 and Maven installed<br />

Fork this repository and clone it <br />

$ git clone https://github.com/<your-user>/spring-boot-jwt <br />
Navigate into the folder <br />

$ cd spring-boot-jwt

Install dependencies <br />

$ mvn install <br />

Run the project
$ mvn spring-boot:run <br />
Navigate to http://localhost:8080/swagger-ui.html in your browser to check everything is working correctly. You can change the default port in the application.yml file
server:<br />
        port: 8080 <br />
Make a GET request to /users/me to check you're not authenticated. You should receive a response with a 403 with an Access Denied message since you haven't set your valid JWT token yet <br />
$ curl -X GET http://localhost:8080/users/me <br />
Make a POST request to /users/signin with the default admin user we programatically created to get a valid JWT token <br />
$ curl -X POST 'http://localhost:8080/users/signin?username=admin&password=admin' <br />
Add the JWT token as a Header parameter and make the initial GET request to /users/me again <br />
$ curl -X GET http://localhost:8080/users/me -H 'Authorization: Bearer <JWT_TOKEN>' <br />
And that's it, congrats! You should get a similar response to this one, meaning that you're now authenticated <br />
{
  "id": 1, <br />
  "username": "admin", <br />
  "email": "admin@email.com", <br />
  "roles": [ <br />
    "ROLE_ADMIN" <br />
  ] <br />
} <br />
