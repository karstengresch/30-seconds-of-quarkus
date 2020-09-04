---
title: Create new project (Gradle)
tags: utility,beginner,Quarkus,Gradle,project,start,JAX-RS
---

Scaffolds a Gradle based project structure to start with.

### Example 1: Minimal
```bash
mvn io.quarkus:quarkus-maven-plugin:1.7.2.Final:create \
    -DprojectGroupId=org.acme.service \
    -DprojectArtifactId=hello \
    -DclassName="org.acme.service.hello.HelloResource" \
    -DbuildTool=gradle
```


### Example 2: All attributes

```bash
mvn io.quarkus:quarkus-maven-plugin:1.7.2.Final:create \
    -DprojectGroupId=org.acme.service \
    -DprojectArtifactId=hello \
    -DprojectVersion=0.0.1 \
    -DclassName="org.acme.service.hello.HelloResource" \
    -Dpath="/hello-service" \
    -Dextensions="resteasy-jsonb,quarkus-undertow-websockets" \
    -DbuildTool=gradle
```

Available extensions to be added can be found at: https://code.quarkus.io/

The project structure looks like this:

```bash
hello
├── README.md
├── build.gradle
├── gradle
│   └── wrapper
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── gradle.properties
├── gradlew
├── gradlew.bat
├── settings.gradle
└── src
    ├── main
    │   ├── docker
    │   │   ├── Dockerfile.fast-jar
    │   │   ├── Dockerfile.jvm
    │   │   └── Dockerfile.native
    │   ├── java
    │   │   └── org
    │   │       └── acme
    │   │           └── service
    │   │               └── hello
    │   │                   └── HelloResource.java
    │   └── resources
    │       ├── META-INF
    │       │   └── resources
    │       │       └── index.html
    │       └── application.properties
    ├── native-test
    │   └── java
    │       └── org
    │           └── acme
    │               └── service
    │                   └── hello
    │                       └── NativeHelloResourceIT.java
    └── test
        └── java
            └── org
                └── acme
                    └── service
                        └── hello
                            └── HelloResourceTest.java
```

The main Java file implements a simple. parameterless JAX-RS resource (REST service with the -Dpath parameter given URI):

```Java
package org.acme.service.hello;

import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.Produces;
import javax.ws.rs.core.MediaType;

@Path("/hello-service")
public class HelloResource {

    @GET
    @Produces(MediaType.TEXT_PLAIN)
    public String hello() {
        return "hello";
    }
}
```
