# document-processor
Document processor for excel file upload and manipulation

Spring boot application with following  Rest APIs with Role base authentication:

- SignIn API
- List all the records
- Delete by id
- Upload Excel file save to DB

## Requirements

For building and running the application you need:

- [JDK 11]
- [Maven 3]
- [MySQL]


## Running the application locally without Docker

Before starting application you must need to build the project using following command.

Make sure you up and run Postgres first locally

```shell
mvn clean install
```

There are several ways to run a Spring Boot application on your local machine. One way is to execute the `main` method in the `com.example.excel.DocumentProcessorApplication` class from your IDE.


Alternatively you can use the [Spring Boot Maven plugin](https://docs.spring.io/spring-boot/docs/current/reference/html/build-tool-plugins-maven-plugin.html) like so:

```shell
mvn spring-boot:run
```

## Running Unit test cases

```shell
mvn test
```

## Test the APIs using curl

SignIn API :

- Username
- Password
  
```shell
curl --location 'http://localhost:8080/login/signin' \
--header 'Content-Type: application/json' \
--data '{
    "username":"Mehul",
    "password":"bhoomi"
}'
```

Get API to fetch all the records :

```shell
curl --location 'http://localhost:8080/document/get/all' \
--header 'Authorization: Bearer token'
```

Upload API based on valid Excel file :

```shell
curl --location 'http://localhost:8080/document/upload' \
--header 'Authorization: Bearer token'\
--form 'file=@"/C:/Users/admin/Downloads/file_example_XLS_10.xls"'
```

Fetch API to get the record by id and status

```shell
curl --location --request GET 'http://localhost:8080/document/find-by-id-status/15' \
--header 'Authorization: Bearer token' \
--form 'file=@"/C:/Users/admin/Downloads/file_example_XLSX_50.xlsx"'
```



## Test the APIs using Swagger

Open the swagger url : http://localhost:8080/swagger-ui.html#
