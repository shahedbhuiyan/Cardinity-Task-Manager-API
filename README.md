# Cardinity-Task-Manager-API
A Sample Rest API Project for Cardinity Evaluation Test

[![LinkedIn][linkedin-shield]][linkedin-url]


<!-- ABOUT-->
## About Project
This is a sample REST API Service Cardinity Evaluation Test, has been developed in `spring-boot`.
It contains `spring-security` `jwt-token` `role-base-authentication` `jpa-hibernate`

### Built With
* [Maven](https://maven.apache.org/)
* [Spring Boot](https://spring.io/projects/spring-boot)

### External Tool
Since this is a REST API Service, We need an external `REST Client` to `Test` the API endpoints
* [Post Man](https://www.postman.com/)

<!-- GETTING STARTED -->
## Getting Started

* Clone the repository
```bash
git clone https://github.com/dipanjal/Cardinity-Task-Manager-API.git
```
## Installation
* Open the `pom.xml` as a <b>Maven Project</b> in your `IDE`
* Run the command bellow in your `Terminal`
```bash
mvn clean install
```

## User Roles
Cardinity Users can have bellow Roles
* USER
* ADMIN

## Status
We have bellow status for the `Tasks` and `Projects`
* Open
* In Progress
* Closed

# Execution
* Run the application by executing `CardinityTaskManagerRestApiApplication.java`
* Import the Postman Collection to test the `API` endpoints

## Authentication
* `POST` [/authenticate]()
* Request Body
```json
{
    "username": "dummy_user",
    "password": "user"
}
```
* You will get a `JWT TOKEN` in Success Response which is actually a `Bearer` token.
* Token format `Bearer {{AuthenticationToken}}`
* After that, You will use this Token in `Authorization` Header of each request.

## Endpoints
Each of the endpoints will require this Header bellow to authenticate the ``USER``
```bash
Authorization: Bearer {{AuthenticationToken}}
``` 

### Project
* Create Project 
    - Method `POST`
    - URL [/project/create]()
    - Request Body 
        ```json
        {
            "name": "Cardinity REST API Project",
            "description": "Sample project for test",
            "status": "open",
            "assignedTo": "dummy_user"
        }
        ```
* Get All Projects
    - Method `GET`
    - URL [/project/get-all]()

* Delete Project by `ID`
    - Method `GET`
    - URL [/project/delete/{id}]()

### Task
* Create Task
    - Method `POST`
    - URL [/task/create]()
    - Request Body 
        ```json
        {
            "name": "Spring Security Integration",
            "description": "Spring Security Integration",
            "status": "open",
            "expiryHour": 8,
            "assignedTo":"dummy_user",
            "projectId": 1
        }
        ```  
* Edit Task
    - Method `POST`
    - URL [/task/update]()
    - Request Body 
        ```json
        {
            "taskId": 1,
            "name": "Spring Security Integration",
            "description": "Spring Security Integration",
            "status": "in progress",
            "expiryHour": 16,
            "assignedTo":"",
            "projectId": 1
        }
        ```
* GET Tasks `OWN USER TASK`
    - Method `GET`
    - URL [/task/get]()
    
* GET All `Tasks` by `Project`
    - Method `GET`
    - URL [/task/get-all/by-project/{projectId}]()

* GET ALL `Expired` Tasks
    - Method `GET`
    - URL [/task/get-all/expired]()
* GET ALL Tasks by `Status`
    - Method `GET`
    - URL [/task/get-by/status/{status}]()

### Admin Endpoints
Only users with `ADMIN` Role can access these endpoints

* GET ALL Tasks by `User`
    - Method `GET`
    - URL [/task/get-all/by-user/{username}]()
    
* GET ALL Projects by `User`
    - Method `GET`
    - URL [/project/get-by/{username}]()

    
## Configuration (`Optional`)
* We already have a `StartupLoader` to populate the  *Dummy Users* and *Roles*. <b>Username<b> and <b>Password<b> in the `application.property` file
```properties
dummy.admin.username=dummy_admin
dummy.user.username=dummy_user
dummy.user2.username=dummy_user2

dummy.admin.password.common=admin
dummy.user.password.common=user
```

* Toggle `Hibernate` DDL Auto Generation by `create` or `update`
```properties
hibernate.hbm2ddl.auto=create
```

* Configure Token Expiry `minute` by changing
```properties
jwt.token.expirey.minute=30
```

<!-- CONTACT -->
## Contact
Dipanjal Maitra [@linkedin](https://www.linkedin.com/in/dipanjalmaitra/) - dipanjalmaitra@gmail.com

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/dipanjalmaitra/
