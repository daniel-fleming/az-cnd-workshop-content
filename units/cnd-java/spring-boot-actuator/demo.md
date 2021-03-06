# Spring Boot Actuator

## Goal
Add actuator metrics to our sample app.

## Prerequisites

+ IDE (Spring Tool Suite, Eclipse, IntelliJ)
+ Local Copy of Sample Project

## Navigate to the root directory

1. Navigate to the `starter-app`.

    `$ cd starter-app`

1. Open the `pom.xml` file with your editor.

1. Add the following dependency to your `pom.xml` file:

    ```
    ...
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-actuator</artifactId>
    </dependency>
    ...
    ```

1. Add the following to the bottom of the `src/main/resources/application.yml` file:

    ```
    ...
    management:
      endpoints:
        web:
          exposure:
            include: "*"
    ```

1. Build the project and generate the Spring Boot jar file

    `$ mvn clean package`

1. Push the app to PCF.

    `$ cf push`

1. In a separate terminal window type the following command:

    `$ curl http://<YOUR-APP-FQDN>/actuator/health`

1. You should see the following output verifying that your app is 'UP'.

    ```
    $ curl <YOUR-APP-FQDN>/actuator/health
    {"status":"UP"}
    ```

1. Modify your `application.yml` file and change the following line:

    ```
    management:
      endpoints:
        web:
          exposure:
            include: "health, info"
    ```

1. Stop your app instance and run the following command:
    
    `$ mvn clean package && cf push`

1. In your terminal window type the following command:
    
    `$ curl http://<YOUR-APP-FQDN>/actuator/env`

1. All endpoints except `health` and `info` are now secured.  This is a best practice for production deployments.

1. Browse [Production Ready Endpoints](https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-endpoints.html) to view a list of all Actuator endpoints.