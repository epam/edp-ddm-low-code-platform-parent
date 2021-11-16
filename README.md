# Low Code Platform Parent

### Overview

* Parent project for all low-code-platfom projects.

### Usage

Specify a parent in your service:

```xml
<project>
  ...
  <parent>
    <groupId>ua.gov.mdtu.ddm.lowcode</groupId>
    <artifactId>low-code-platform-parent</artifactId>
    <version>...</version>
  </parent>
  ...
</project>
```

### Dependencies

*We should stick with Spring Boot and Spring Cloud release trains.*

There are some useful command and tips:
* effective POM (The POM that results from the application of interpolation):
    * in IntelliJ IDEA, place cursor into the content of pom.xml, press `Ctrl + Shift + A`,
      type `Show effective POM` and press `Enter`
    * in console, `mvn help:effective-pom`
* dependencies:
    * `mvn dependency:tree -Dverbose` (provides an information about which dependencies are used for project showing version)
    * `mvn dependency:list` (provides the same information that previous command but without hierarchy and reason why specific version is chosen.)

### Plugins configuration

* `org.apache.maven.plugins:maven-surefire-plugin` - is used for unit tests;
* `org.apache.maven.plugins:maven-failsafe-plugin` - is used for component/integration tests.
* `org.codehaus.mojo:maven-failsafe-plugin` - is used for adding more source directories(for integration test) to project, since pom.xml only allows one source directory.

These plugins are preconfigured in `<pluginManagement/>` section with next settings:
* `maven-surefire-plugin`:
    * execution phase - `test` (by default);
    * includes test classes with `**/*Test.java` mask;
* `maven-failsafe-plugin`:
    * execution phase - `integration-test`;
    * includes test classes with `**/*IT.java` mask;
* `maven-failsafe-plugin`:
    * adds integration test source directory `${project.basedir}/src/it/java`
    * adds integration test resource directory `${project.basedir}/src/it/resources`

### License

The low-code-platform-parent is released under version 2.0 of
the [Apache License](https://www.apache.org/licenses/LICENSE-2.0).