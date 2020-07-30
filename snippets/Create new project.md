---
title: Create new project
tags: utility,beginner,Quarkus,Maven,project,start,JAX-RS
---

Scaffolds a Maven based project structure to start with.


```bash
mvn io.quarkus:quarkus-maven-plugin:1.6.1.Final:create \
    -DprojectGroupId=my-groupId \
    -DprojectArtifactId=my-artifactId \
    -DprojectVersion=my-version \
    -DclassName="org.my.group.MyResource"
```

The project structure looks like this:

```bash
.
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
    │   │       └── my
    │   │           └── group
    │   │               └── MyResource.java
    │   └── resources
    │       ├── META-INF
    │       │   └── resources
    │       │       └── index.html
    │       └── application.properties
    └── test
        └── java
            └── org
                └── my
                    └── group
                        ├── MyResourceTest.java
                        └── NativeMyResourceIT.java
```

The main Java file implements a simple. parameterless JAX-RS resource (REST service):

```Java
package org.my.group;

import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.Produces;
import javax.ws.rs.core.MediaType;

@Path("/hello")
public class MyResource {

    @GET
    @Produces(MediaType.TEXT_PLAIN)
    public String hello() {
        return "hello";
    }
}
```
