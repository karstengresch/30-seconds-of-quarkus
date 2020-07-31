---
title: Create new project (Maven)
tags: utility,beginner,Quarkus,Maven,project,start,JAX-RS
---

Scaffolds a Maven based project structure to start with.

### Example 1: Minimal
```bash
mvn io.quarkus:quarkus-maven-plugin:1.6.1.Final:create \
    -DprojectGroupId=org.acme.service \
    -DprojectArtifactId=hello \
    -DclassName="org.acme.service.hello.HelloResource"
```


### Example 2: All attributes

```bash
mvn io.quarkus:quarkus-maven-plugin:1.6.1.Final:create \
    -DprojectGroupId=org.acme.service \
    -DprojectArtifactId=hello \
    -DprojectVersion=0.0.1 \
    -DclassName="org.acme.service.hello.HelloResource" \
    -Dpath="/hello-service" \
    -Dextensions="resteasy-jsonb,quarkus-undertow-websockets"
```

Available extensions to be added can be found at: https://code.quarkus.io/

The project structure looks like this:

```bash
hello
├── README.md
├── mvnw
├── mvnw.cmd
├── pom.xml
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
    └── test
        └── java
            └── org
                └── acme
                    └── service
                        └── hello
                            ├── HelloResourceTest.java
                            └── NativeHelloResourceIT.java
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
