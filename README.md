## Project Overview

This repository implements a Scala-based application for managing a pet store, focusing on users, pets, and orders. The project is structured around domain-driven design, with clear separation between domain models, service layers, infrastructure endpoints, and repository implementations. Support for both in-memory and Doobie (SQL-based) repositories is provided, along with robust validation and authentication modules. Functional and unit testing is included to ensure reliability. The application is built and managed using SBT, and supplementary scripts aid in setup and integration.

## Project Structure

```
.
├── AUTHORS.md                     # Project authors information
├── CODE_OF_CONDUCT.md             # Community guidelines
├── LICENSE                        # Licensing details
├── build.sbt, build.sh            # SBT build definition and shell build script
├── functional_test/               # Functional test suite with pytest configuration and scripts
│   ├── bootstrap.sh               # Test environment bootstrap script
│   ├── live_tests/               

### 3. Data Flow Diagram

Below is an illustrative ASCII diagram depicting the data flow in the Spark Pet Store Data Engineering project. Since no explicit details about sources or targets are available, the diagram is based on assumptions drawn from the test files and naming conventions.

```
            +----------------------+
            |   Source Tables      |
            |----------------------|
            |   users, pets, orders|
            +----------+-----------+
                       |
                [Extraction]
                       |
                       v
            +----------------------+
            |  Spark ETL Process   |
            +----------------------+
                       |
               [Transformation]
                       |
                       v
           +-----------------------+
           |   Target Tables       |
           |-----------------------|
           | users_clean, pets_enhanced,|
           | orders_fact                |
           +-----------------------+
```

**Assumptions:**  
- Data originates from three main source tables: `users`, `pets`, and `orders`.  
- ETL process includes

## 5. Transformations

This project implements functional transformations between domain models, repositories, and endpoints. The primary transformations inferred from the provided code are:

- **Domain to DTO Mapping**: Domain classes such as `Pet`, `Order`, and `User` are often serialized/deserialized for API endpoints. They may be transformed to web response objects or persisted as records in the database, typically via case classes with corresponding fields.
- **Status Enumeration Handling**: For both `OrderStatus` and `PetStatus`, string representations received from endpoints are mapped to sealed trait enumerations within the domain logic.
- **Validation Handlers**: Validation interpreters (`PetValidationInterpreter`, `UserValidationInterpreter`) transform and validate incoming objects against business rules, returning either valid domain objects or error information encapsulated in `ValidationError`.
- **Authentication Transformation**: The `Auth` module transforms user credentials and login requests into authentication tokens or error states for session handling.
- **Pagination Transformation**: The `

## 9. Configuration

This Scala Spark project utilizes Maven for dependency management as defined in the `pom.xml` file. Please review your `pom.xml` to ensure all necessary dependencies are included for Spark and Scala. Common dependencies include:

```xml
<dependency>
    <groupId>org.apache.spark</groupId>
    <artifactId>spark-core_2.12</artifactId>
    <version>3.4.0</version>
</dependency>
<dependency>
    <groupId>org.apache.spark</groupId>
    <artifactId>spark-sql_2.12</artifactId>
    <version>3.4.0</version>
</dependency>
```

Check for any Scala or Spark version differences, and verify other relevant libraries as needed by your code.

If your project includes additional visible configuration files (e.g., `application.conf`, `log4j.properties`), ensure these are properly set up and documented for Spark job parameters and