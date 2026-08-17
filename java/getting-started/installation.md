---
id: installation
url: markdown/java/installation
title: Install GroupDocs.Markdown for Java
linkTitle: Installation
weight: 4
description: "How to install GroupDocs.Markdown for Java using Maven, Gradle, Kotlin, Ivy, Sbt, or a manual JAR download."
keywords: GroupDocs.Markdown, install, Maven, Gradle, Kotlin, JAR, Java
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

This topic describes how to add the **GroupDocs.Markdown** library to your Java project.

## Prerequisites

1. **Java Development Kit** -- JDK 8 or later.
2. **Build tool** -- Maven, Gradle, Kotlin DSL, Ivy, or Sbt for dependency management.
3. **License (optional)** -- run in evaluation mode or apply a [temporary license]({{< ref "markdown/java/getting-started/licensing-and-subscription.md" >}}).

## Install from the GroupDocs Repository

All GroupDocs Java packages are hosted at the [GroupDocs Artifact Repository](https://repository.groupdocs.com/) rather than Maven Central, so you must add the repository before declaring the dependency.

### Add the GroupDocs Artifact Repository

{{< tabs "install-repository" >}}
{{< tab "Maven" >}}
```xml
<repositories>
  <repository>
    <id>GroupDocs Artifact Repository</id>
    <name>GroupDocs Artifact Repository</name>
    <url>https://releases.groupdocs.com/java/repo/</url>
  </repository>
</repositories>
```
{{< /tab >}}
{{< tab "Gradle" >}}
```groovy
repositories {
  maven {
    url "https://repository.groupdocs.com/repo/"
  }
}
```
{{< /tab >}}
{{< tab "Kotlin" >}}
```kotlin
repositories {
  maven(url = "https://repository.groupdocs.com/repo/")
}
```
{{< /tab >}}
{{< tab "Ivy" >}}
```xml
<ivysettings>
  <settings defaultResolver="chain"/>
  <resolvers>
    <chain name="chain">
      <ibiblio name="GroupDocs Repository" m2compatible="true" root="https://releases.groupdocs.com/java/repo/"/>
    </chain>
  </resolvers>
</ivysettings>
```
{{< /tab >}}
{{< tab "Sbt" >}}
```scala
resolvers += Resolver.url("GroupDocs Repository", url("https://releases.groupdocs.com/java/repo/"))
```
{{< /tab >}}
{{< /tabs >}}

### Add GroupDocs.Markdown as a dependency

Replace `latest-version` with the version you want to use. The current release is <i class="release-version-number">latest-version</i>.

{{< tabs "install-dependency" >}}
{{< tab "Maven" >}}
```xml
<dependencies>
  <dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-markdown</artifactId>
    <version>latest-version</version>
  </dependency>
</dependencies>
```
{{< /tab >}}
{{< tab "Gradle" >}}
```groovy
dependencies {
  implementation 'com.groupdocs:groupdocs-markdown:latest-version'
}
```
{{< /tab >}}
{{< tab "Kotlin" >}}
```kotlin
dependencies {
  implementation("com.groupdocs:groupdocs-markdown:latest-version")
}
```
{{< /tab >}}
{{< tab "Ivy" >}}
```xml
<dependency org="com.groupdocs" name="groupdocs-markdown" rev="latest-version">
  <artifact name="groupdocs-markdown" ext="jar"/>
</dependency>
```
{{< /tab >}}
{{< tab "Sbt" >}}
```scala
libraryDependencies += "com.groupdocs" % "groupdocs-markdown" % "latest-version"
```
{{< /tab >}}
{{< /tabs >}}

## Manual JAR download

You can also download the JAR directly from the [GroupDocs downloads page](https://releases.groupdocs.com/java/repo/com/groupdocs/groupdocs-markdown/) and add it to your project's classpath manually.

## Example: a minimal command line application

Create the following project structure:

```log
|--- pom.xml
|--- business-plan.docx
|--- src
     |--- main
          |-- java
              |-- com
                  |-- mycompany
                      |-- app
                          |-- App.java
```

{{< tabs "install-project-files" >}}
{{< tab "App.java" >}}
```java
package com.mycompany.app;

import com.groupdocs.markdown.MarkdownConverter;

public class App {

    public static void main(String[] args) {
        MarkdownConverter.toFile("business-plan.docx", "business-plan.md");
        System.out.println("Conversion complete");
    }
}
```
{{< /tab >}}
{{< tab "pom.xml" >}}
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.mycompany.app</groupId>
  <artifactId>markdown-helloworld</artifactId>
  <version>1.0-SNAPSHOT</version>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
  </properties>

  <dependencies>
    <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-markdown</artifactId>
      <version>latest-version</version>
    </dependency>
  </dependencies>

  <build>
    <plugins>
      <plugin>
        <artifactId>maven-assembly-plugin</artifactId>
        <executions>
          <execution>
            <phase>package</phase>
            <goals>
              <goal>single</goal>
            </goals>
          </execution>
        </executions>
        <configuration>
          <archive>
            <manifest>
              <mainClass>com.mycompany.app.App</mainClass>
            </manifest>
          </archive>
          <descriptorRefs>
            <descriptorRef>jar-with-dependencies</descriptorRef>
          </descriptorRefs>
        </configuration>
      </plugin>
    </plugins>
  </build>

  <repositories>
    <repository>
      <id>GroupDocs Artifact Repository</id>
      <name>GroupDocs Artifact Repository</name>
      <url>https://releases.groupdocs.com/java/repo/</url>
    </repository>
  </repositories>
</project>
```
{{< /tab >}}
{{< /tabs >}}

Build it from the directory containing `pom.xml`:

```bash
mvn clean package
```

Then run it:

```bash
java -jar target/markdown-helloworld-1.0-SNAPSHOT-jar-with-dependencies.jar
```

The program prints:

```log
Conversion complete
```

and writes `business-plan.md` next to the source document.

{{< alert style="info" >}}
You can create and run this project in your IDE instead, or build it with Gradle -- nothing in the library depends on Maven.
{{< /alert >}}

## Verify Installation

After installing, verify that the library is on the classpath:

{{< tabs "verify-install" >}}
{{< tab "VerifyInstall.java" >}}
```java
import com.groupdocs.markdown.*;

public class VerifyInstall {

    public static void main(String[] args) {
        // List all supported formats
        for (FileFormat format : MarkdownConverter.getSupportedFormats()) {
            System.out.println(format);
        }
    }
}
```
{{< /tab >}}
{{< /tabs >}}
