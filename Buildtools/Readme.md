# Build Tools


## Table of Contents

1. [What are Build Tools?](#what-are-build-tools)
2. [Purpose of Build Tools](#purpose-of-build-tools)
3. [What is Maven?](#what-is-maven)
4. [What is Gradle?](#what-is-gradle)
5. [Maven vs Gradle: Key Differences](#maven-vs-gradle-key-differences)
6. [What is Maven Remote Repository?](#what-is-maven-remote-repository)
7. [Maven Build Lifecycle Phases](#maven-build-lifecycle-phases)  
   - [Standard Lifecycle Phases](#standard-lifecycle-phases)  
   - [Phase-by-Phase Explanation with Examples](#phase-by-phase-explanation-with-examples)  
     - [1. validate](#1-validate)  
     - [2. compile](#2-compile)  
     - [3. test](#3-test)  
     - [4. package](#4-package)  
     - [5. verify](#5-verify)  
     - [6. install](#6-install)  
     - [7. deploy](#7-deploy)  
   - [Lifecycle Summary Diagram](#lifecycle-summary-diagram)  
   - [Bonus: Common Commands](#bonus-common-commands)

---

## What are Build Tools?

Build tools are software programs used to automate the process of converting source code into executable software (binary). This includes:

- Compiling source code  
- Packaging binaries (like `.jar` or `.war` files)  
- Managing dependencies (libraries)  
- Running tests  
- Deploying applications  

---

## Purpose of Build Tools

The main purposes of build tools are:

- **Automation**: Automates repetitive tasks like compilation, testing, packaging.  
- **Dependency Management**: Automatically downloads and manages third-party libraries.  
- **Standardization**: Provides consistent build processes across environments.  
- **Integration**: Works with CI/CD pipelines (e.g., Jenkins, GitHub Actions).  
- **Error Reduction**: Reduces human errors during builds.  

---

## What is Maven?

**Apache Maven** is a popular **build automation** and **dependency management tool** primarily used in Java-based projects.

### 🔹 Key Features:
- Uses **XML-based configuration** (`pom.xml`).  
- Manages **project lifecycle** phases like validate, compile, test, package, install, and deploy.  
- Handles **dependencies** via Maven Central Repository.  
- Supports plugins for testing, reporting, deployment, etc.  

### Example Dependency:
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
  <version>2.7.0</version>
</dependency>
```


---

## What is Gradle?

**Gradle** is a modern, flexible, and powerful **build tool** used for Java, Kotlin, Groovy, Android, and more.

### 🔹 Key Features:

* Uses **Groovy** or **Kotlin DSL** instead of XML.
* Faster builds with **incremental compilation** and **build caching**.
* Flexible and extensible architecture.
* Widely used in **Android development**.

### Example Dependency:

```groovy
dependencies {
  implementation 'org.springframework.boot:spring-boot-starter-web:2.7.0'
}
```

---

## Maven vs Gradle: Key Differences

| Feature             | Maven                       | Gradle                              |
| ------------------- | --------------------------- | ----------------------------------- |
| **Build Script**    | XML (`pom.xml`)             | Groovy/Kotlin DSL (`build.gradle`)  |
| **Performance**     | Slower                      | Faster (build caching, incremental) |
| **Flexibility**     | Less flexible               | Highly customizable                 |
| **Learning Curve**  | Easier for beginners        | Slightly steeper                    |
| **Dependency Mgmt** | Maven Central, custom repos | Same + advanced resolution options  |
| **Plugin Support**  | Rich ecosystem              | Rich and more flexible ecosystem    |
| **Common Use**      | Java Enterprise Projects    | Modern Java/Android Projects        |

---

## What is Maven Remote Repository?

A **Maven Remote Repository** is a server that hosts **project dependencies** like `.jar` files. Maven fetches them from the remote repository if they're not found in your local repository.

### Types of Repositories:

1. **Local Repository**
   Your machine’s local cache at:
   `~/.m2/repository`

2. **Central Repository**
   Default online repository used by Maven:
   [https://repo.maven.apache.org](https://repo.maven.apache.org)

3. **Remote/Custom Repositories**
   Organizations may host their own repositories (e.g., **JFrog Artifactory**, **Sonatype Nexus**).

### How It Works:

1. You define dependencies in `pom.xml`.
2. Maven checks your **local repository**.
3. If not found, it downloads them from the **remote repository**.
4. The downloaded files are stored in your local repo for future builds.

---

## Maven Build Lifecycle Phases

Maven follows a standard **build lifecycle**, which consists of a sequence of **phases**. Each phase represents a step in the build process.

> When you run a command like `mvn install`, Maven executes all phases **up to** and **including** that phase.

---

### Standard Lifecycle Phases

| Phase Name | Description                                                             |
| ---------- | ----------------------------------------------------------------------- |
| `validate` | Validates project structure and necessary information.                  |
| `compile`  | Compiles the source code.                                               |
| `test`     | Runs unit tests using a testing framework like JUnit.                   |
| `package`  | Packages the code into a JAR, WAR, or EAR.                              |
| `verify`   | Runs checks to verify the package is valid and meets quality standards. |
| `install`  | Installs the package into the local Maven repository (`~/.m2`).         |
| `deploy`   | Uploads the package to a remote repository for sharing.                 |

---

### Phase-by-Phase Explanation with Examples

---

### 1. validate

**Purpose**: Checks if the `pom.xml` is correct and all required directories (like `src/main/java`) are present.

**Example**:

```sh
mvn validate
```

**Behind the Scenes**:

* Ensures all project metadata (groupId, artifactId, version) is defined.
* Validates plugin configurations.

---

### 2. compile

**Purpose**: Compiles all source code from `src/main/java`.

**Example**:

```sh
mvn compile
```

**Behind the Scenes**:

* Uses the **compiler plugin** to convert `.java` files into `.class` files.
* Stores compiled files in `target/classes`.

---

### 3. test

**Purpose**: Runs unit tests using `src/test/java`.

**Example**:

```sh
mvn test
```

**Behind the Scenes**:

* Runs tests using **Surefire Plugin** (usually JUnit/TestNG).
* Fails the build if any test fails.

---

### 4. package

**Purpose**: Packages compiled code into a JAR, WAR, or EAR file.

**Example**:

```sh
mvn package
```

**Behind the Scenes**:

* Combines compiled `.class` files and resources into `target/my-app.jar`.
* Uses the `packaging` type defined in `pom.xml`.

```xml
<packaging>jar</packaging>
```

---

### 5. verify

**Purpose**: Verifies the package meets quality criteria (integration tests, checksums, etc.).

**Example**:

```sh
mvn verify
```

**Behind the Scenes**:

* Runs additional verification steps (custom plugins like Checkstyle, PMD).
* May involve integration tests.

---

### 6. install

**Purpose**: Installs the package into your **local repository** so other local projects can use it.

**Example**:

```sh
mvn install
```

**Behind the Scenes**:

* Copies the package to:

  ```
  ~/.m2/repository/groupId/artifactId/version/
  ```

---

### 7. deploy

**Purpose**: Deploys the package to a **remote repository** for use by other developers or systems.

**Example**:

```sh
mvn deploy
```

**Behind the Scenes**:

* Uses credentials defined in `~/.m2/settings.xml`.
* Uploads `.jar` or `.war` files to a server like Nexus or Artifactory.

---

### Lifecycle Summary Diagram

```
validate → compile → test → package → verify → install → deploy
```

> Running `mvn package` will run: `validate → compile → test → package`
> Running `mvn install` will run all the above **plus install**

---

### Common Commands

| Command       | What it does                                       |
| ------------- | -------------------------------------------------- |
| `mvn clean`   | Deletes `target/` folder (cleans previous builds). |
| `mvn compile` | Compiles Java code.                                |
| `mvn test`    | Runs unit tests.                                   |
| `mvn package` | Builds `.jar` or `.war` file.                      |
| `mvn install` | Installs to local `.m2` repository.                |
| `mvn deploy`  | Uploads to remote repository.                      |

---
