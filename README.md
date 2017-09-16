# protobuf-template
Protocol Buffers template ready for creating Java protobuf artifacts.

# Useful Links
- Protocol Buffers documentation: https://developers.google.com/protocol-buffers
- Maven build tool: https://maven.apache.org/download.cgi

# How to use
Design how you want your information for serialization to be structured in a `.proto` file and use Maven build tool to construct and build the `.proto` file into a Java artifact.

## 1. Designing your .proto file
There is the template `.proto` file located under `src/main/proto`. Here you can create one or many `.proto` files. The end result will bundle all the `.proto` files into one Java artifact when built. 

Documentation and more on designing of the `.proto` file can be found in the useful link section.

### 2. Changes to make before building with Maven
Make the following changes to specify your artifact properties by changing the defaults.
```
<groupId>com.protobuf</groupId>
<artifactId>protobuf-template</artifactId>
<version>0.0.1-SNAPSHOT</version>

<name>Protobuf Template</name>
```

Also change the name of the artifact binary name under `properties` section.
```
<properties>
    <artifact.name>protobuf-template</artifact.name>
</properties>
```

### 3. Compiling .proto file
Run `mvn compile` goal to see if your `.proto` file will compile successfully without error.
If successful you will get a `.jar` file under the `${project.build.directory}\target`.

Incorrect syntax or errors in the `.proto` file can be identified when invoking `mvn compile` on the command line.
```
[INFO] ------------------------------------------------------------------------
[INFO] Building Protobuf Template 0.0.1-SNAPSHOT
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] --- protobuf-maven-plugin:0.5.0:compile (default) @ protobuf-template ---
[INFO] Compiling 1 proto file(s) to C:\Workspace\protobuf-template\target\generated-sources\protobuf\java
[ERROR] PROTOC FAILED: ProtobufTemplate.proto:13:13: Expected field name.

[ERROR] C:\Workspace\protobuf-template\src\main\proto\ProtobufTemplate.proto [0:0]: 
        ProtobufTemplate.proto:13:13: Expected field name.

[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
```

### 4. Producing the Java artifact
Once the `.proto` file compiles without any errors then it can be installed locally, pushed onto remote hosting server or included in your project classpath if your project does not use Maven via the following `mvn` goals:

- `mvn package` - Produces the `.jar` file under `${project.build.directory}\target`.
- `mvn install` - Installs to local `.m2` folder on your system.
- `mvn deploy` - Push to remote Maven hosting server. __Note:__ need to be defined in `pom.xml`.

Finally include the Maven artifact into your project's dependencies of your `pom.xml`
