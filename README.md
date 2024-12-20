## Objective: Building a Go API for returning current Toronto Time with MySQL Database Logging

This project is to develop an API using the Go programming language that provides the current time in the "America/Toronto" timezone, formatted as JSON. The application is connected to a MySQL database in the backend, where each API request logs the current time into a table named time_log.

### Tasks:

Configured the MySQL database
Developed the API functionality
Implemented time zone conversion to "America/Toronto"
Established a connection between the API and the database
Designed the API to return the time in JSON format
Added robust error handling mechanisms


### Implementation Steps:

**Steps for Implementation:**  

Created Two files, `docker-compose.yaml` and `Dockerfile`. The purpose of the Docker Compose file is to enable the Go application to establish a connection with MySQL and interact with it.  

The `docker-compose.yaml` file fetches the `mysql:8.0` base image and runs the MySQL service on port 3306. A volume is mounted to the default database directory, `/var/lib/mysql`, ensuring that the database data remains persistent across container restarts. An `init.sql` script is used to initialize the database named `time_api_db` and the `time_log` table. This setup ensures the data persists each time the MySQL container is restarted.  

Additionally, the `docker-compose.yaml` file configures the Go application container by referencing the `Dockerfile`, which includes instructions to build a Go image. Before running the Go application, the Go environment must be initialized, and two Go modules are included to handle MySQL interactions and environment variables in the code.

```
Command to build the images and run the containers.

```
$ docker-compose up --build
```

The images are built successfully and the containers are up and running.
```
Accessing the API http://localhost:8080/current-time


connect to the mysql container using the below command.

```
$ docker exec -it mysql-container mysql -u root -p<ENTER ROOT PASSWORD>
mysql> USE time_api_db;
mysql> SELECT * FROM time_log;
```
