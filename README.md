# This is a tutorial about maven

## Build & Run

### Generate a Project

```shell
mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

### Build the Package

```shell
mvn package
```

Or we can use the following command to first remove the target folder
```shell
mvn clean package
```

To skip test, use `-Dmaven.test.skip=true`
```shell
mvn clean package -Dmaven.test.skip=true
```

### Run the Code

```shell
java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App
```

## Basic Concepts

### Maven Phases

Although hardly a comprehensive list, these are the most common default lifecycle phases executed.

- **validate**: validate the project is correct and all necessary information is available
- **compile**: compile the source code of the project
- **test**: test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed
- **package**: take the compiled code and package it in its distributable format, such as a JAR.
- **integration-test**: process and deploy the package if necessary into an environment where integration tests can be run
- **verify**: run any checks to verify the package is valid and meets quality criteria
- **install**: install the package into the local repository, for use as a dependency in other projects locally
- **deploy**: done in an integration or release environment, copies the final package to the remote repository for sharing with other developers and projects.

There are two other Maven lifecycles of note beyond the default list above. They are

- **clean**: cleans up artifacts created by prior builds
- **site**: generates site documentation for this project

### Repository

There are 3 kinds of repository:

- Local, specified in ~/.m2/setting.xml by adding `<localRepository>path/to/lical/repo</localRepository>`, or add the following tag to the pom.xml:
```
<repositories>
    <repository>
        <id>lib</id>
        <url>file:${basedir}/lib</url>
    </repository>
</repositories>
```

- Central, a repository provided by the Maven community
- Remote, is developer's own custom repository containing the required libraries or other project jars:
```xml
<repositories>
  <repository>
     <id>companyname.lib1</id>
     <url>http://download.companyname.org/maven2/lib1</url>
  </repository>
  <repository>
     <id>companyname.lib2</id>
     <url>http://download.companyname.org/maven2/lib2</url>
  </repository>
</repositories>
```


## References

1. [Maben in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)
2. [Introduction to the Build Lifecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)

# maven_tutorial
