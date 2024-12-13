# Java Development Specifications

Java development specifications to follow during the development process.

## Variable Naming

1. File names and class names use camel case format (e.g., UserService, UseDAO).  
2. Variable names should start with a lowercase letter and use camel case (lowerCamelCase).  
3. Constants should be in all uppercase letters (e.g., HIGH=12).

A single file should not exceed 1000 lines, and a single line should not exceed 120 characters.

Indentation should use four spaces, and tabs should not be used.

Encoding should be UTF-8.

## Commenting Standards

Single-line comments: `//`  
Multi-line comments: `/* content */`, use multi-line comments for functions, classes, etc., following the javadoc standards to allow IDE recognition. Include function descriptions, parameters, return values, and exception handling.

## Logging Standards

Use SLF4J API for logging, with logs retained for a default of 15 days.

### Swagger Annotations

## Spring Boot Development

### Project Structure

The project uses Maven for construction with an MVC structure. The project structure is as follows:

```
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com
│   │   │       └── example
│   │   │           └── demo
│   │   │               ├── controller
│   │   │               ├── entity
│   │   │               ├── mapper
│   │   │               ├── service
│   │   │               └── DemoApplication.java
│   │   └── resources
│   │       ├── application.properties
│   │       ├── static
│   │       └── templates
│   └── test
└── pom.xml
```

In this structure, `controller` holds controller layer code, `entity` contains entity classes, `mapper` stores mapper interfaces, `service` contains business logic code, `DemoApplication.java` is the project entry point, and `application.properties` is the project configuration file.

### Project Configuration

## Project Structure
