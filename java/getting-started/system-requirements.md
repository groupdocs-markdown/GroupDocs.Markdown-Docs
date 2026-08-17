---
id: system-requirements
url: markdown/java/system-requirements
title: System requirements
weight: 3
description: System requirements for GroupDocs.Markdown for Java — supported operating systems, Java versions, and development environments.
keywords: GroupDocs.Markdown for Java, Markdown, system requirements, Java 8, JDK, JRE
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

{{< alert style="info" >}}

GroupDocs.Markdown for Java does not require any external software such as Microsoft Office or third-party document editors. To install GroupDocs.Markdown for Java, follow the steps in the [Installation]({{< ref "markdown/java/getting-started/installation.md" >}}) guide.

{{< /alert >}}

## Supported Operating Systems

GroupDocs.Markdown for Java runs anywhere a supported JVM runs.

### Windows

*   Microsoft Windows 10 (x64, x86)
*   Microsoft Windows 11 (x64)
*   Microsoft Windows Server 2016 and later

### Linux

*   Ubuntu 20.04+, Debian 11+, CentOS 8+, RHEL 8+, Fedora 36+, Alpine 3.16+
*   Any distribution with a Java SE 8+ runtime

### macOS

*   macOS 12 (Monterey) and later — Intel and Apple Silicon (M-series)

## Supported Java Versions

| Java version | Notes |
| --- | --- |
| Java SE 8 | Minimum supported version |
| Java SE 11 | LTS |
| Java SE 17 | LTS |
| Java SE 21 | LTS (latest tested) |

The library is compiled for Java 8 bytecode, so it runs unchanged on any later JVM. A single JAR covers every platform — there are no per-OS or per-version artifacts to choose between.

## Development Environments

GroupDocs.Markdown for Java can be used in any environment that builds Java. The following are explicitly supported:

*   IntelliJ IDEA 2023.1 and later
*   Eclipse IDE 2023-03 and later
*   Apache NetBeans 17 and later
*   Visual Studio Code with the Extension Pack for Java

## Build Tools

*   Apache Maven 3.6+
*   Gradle 7.0+ (Groovy or Kotlin DSL)
*   Apache Ivy, Sbt
