#sarathi
Application for appointment booking system
_Sarathi_ is an appointment booking system for patients and doctors designed for a particular hospital

This project is build using  `java` `spring boot` `postgres sql` `maven`

**This project was created using _spring initializer_ Navigate to [spring-initializer](https://start.spring.io.)**
- This service pulls in all the dependencies you need for an application and does most of the setup for you

`Dependencies` used
- `Spring Data JPA`
- `Spring Web`
- `Spring Boot DevTools`
- `Postgres Driver`
- `spring-boot-starter-validation`
- `flyway-core`
- `Spring-security`

## Prerequisites

Following platform is required to run the application:

- **clone the project in your system**
    - Download and unzip the source repository or clone it using Git:
```bash
https://github.com/one2nc/sarathi.git
```
- **Make necessary changes and commit those changes**

```git add .
git commit -m "new feature or fix"
```

- Push changes, replacing <add-your-branch-name>

```
git push origin 
```

- **Java JDK 17**
    - link to download-> https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html
    - Set `JAVA_HOME` system variable with a valid JDK path and add `${JAVA_HOME}/bin` to the PATH variable



- **Build and run the app using maven**

```bash
mvn package
java -fileName.jar
```

Alternatively, you can run the app without packaging it using -

```bash
mvn spring-boot:run
```

- **Installing Docker and Docker Compose**
    - **set up the repo**

      Run this Commands in the Terminal
      ```bash 
            sudo apt-get update
            sudo apt-get install \
            ca-certificates \
            curl \
            gnupg \
            lsb-release
      ``` 

    - **Add Docker’s official GPG key**

      Run the Following Command
  ```bash
      sudo mkdir -p /etc/apt/keyrings
      curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
  ```

    - **Use the following command to set up the repository:**
  ```bash
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

    - **Install Docker Engine**
  ```bash
     sudo apt-get update
     sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
  ```

    - **Install Docker Compose**

  Use the following command to download:
   ```bash
       mkdir -p ~/.docker/cli-plugins/
       curl -SL https://github.com/docker/compose/releases/download/v2.3.3/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
   ```

  set the correct permissions so that the docker compose command is executable:
   ```bash
    chmod +x ~/.docker/cli-plugins/docker-compose
   ```

  To verify that the installation was successful, you can run:
  ```bash
  docker compose version
  ```
    - **Run The app Using Docker**

      Run the command `docker-compose up`

      To stop the Container `ctrl+C`

    - **You can also import the code straight into your `IDE`**

      use IntelliJ IDEA

    - **install postgres and `pgAdmin4`**
    - if installing postgres in windows follow
      this [install-postgres](https://www.guru99.com/download-install-postgresql.html)



**Create Postgres database**
```bash
create database hospital_appointment_db
```

**Change postgres username and password as per your installation**
change the location

+ open `src\main\resources\application.properties`

+ change `spring.datasource.username` and `spring.datasource.password` as per your postgres installation

- Now run the application so that it creates all the tables and inserts the value as we are using `flyway` to know
  more <https://www.baeldung.com/database-migrations-with-flyway>
    - you can check the db. migration package

+ open `src\main\resources\db\migration`

- You can navigate to `pgAdmin` and check the tables and values or do it from command line
  ```
  \l - to view all databases
  \c db_name - to use a database
  select * from users; - to check the values in tables
  ```

**The `Spring Initializer` creates a main class that you can use to launch the application.**
- The following listing
```bash
src\main\java\in\one2n\sararthi\SararthiAppointmentApplication.java
```

**Test the Application:**

- You can load the home page <http://localhost:8080/>
  example `http://localhost:8080/api/v1/appointments`

- You can run the test-cases using maven

  `clean`

  `test`

- To Individually run tests Navigate to `src/test/java`

- You can also test the application in Postman <https://www.postman.com/downloads/>
- Import the file in your `Postman` and test the API calls
  ```bash
  src\main\resources\sarathi.postman_collection.json
  ```

**Controllers**
- This Controller is to check incoming appointments to add an appointments etc
  `src\main\java\in\one2n\sararthi\controller\AppointmentController.java`
- This Controller is get doctors ,add new patients etc
  `src\main\java\in\one2n\sararthi\controller\PatientController.java`
- This Controller to register a user ,login etc
  `src\main\java\in\one2n\sararthi\controller\UserController.java`

**The following guides may also be helpful**

- [Spring-boot](https://spring.io/guides/gs/spring-boot/)
- [consuming-rest](https://spring.io/guides/gs/consuming-rest/)
- [spring-boot](https://spring.io/guides/gs/spring-boot/)
- [Docker](https://container.training/intro-selfpaced.yml.html#1)

> This is just an initial implementation of simple CRUD APIs exercising Spring boot,postgres Another features and technologies will be added to this project

# Todos

- Need to work on UI for patient and receiptionist
- Calculation and display of expected wait time for patients
- Local dev setup with hot reload via Docker
- Continuous Integration via Jenkins or GitHub Actions
- Not on production
- We are using JWT for auth, need to think if this is a right choice
- All onboarding is manual, directly via DB inserts, no UI or API
