---
id: installation-linux
url: markdown/java/installation-linux
title: Run GroupDocs.Markdown for Java on Linux
linkTitle: Linux Installation
weight: 5
description: "How to run GroupDocs.Markdown for Java on Linux and in Docker containers, including headless mode and font setup."
keywords: GroupDocs.Markdown, Linux, Docker, Ubuntu, Alpine, headless, fonts, Java
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

This article explains how to run **GroupDocs.Markdown for Java** on Linux. The library is pure Java with no native dependencies, so the JAR that runs on Windows runs unchanged on Linux — but two server-specific details are worth getting right: **headless mode** and **fonts**.

## Prerequisites

Install a JDK 8 or later for your distribution:

```bash
# Debian / Ubuntu
sudo apt-get update && sudo apt-get install -y openjdk-17-jdk

# RHEL / Fedora / CentOS
sudo dnf install -y java-17-openjdk-devel

# Alpine
sudo apk add openjdk17
```

## Build and Run

From your project directory:

```bash
mvn clean package
java -jar target/markdown-helloworld-1.0-SNAPSHOT-jar-with-dependencies.jar
```

## Run Headless

Servers usually have no display. Document rendering touches AWT, so run the JVM in headless mode to avoid `HeadlessException`:

```bash
java -Djava.awt.headless=true -jar target/app.jar
```

You can also set it in code before any conversion runs:

```java
System.setProperty("java.awt.headless", "true");
```

## Install Fonts

Minimal Linux images ship with no fonts at all. Without them, text in converted images and in documents that rely on specific typefaces falls back to a default, which changes the output. Install a base font set:

```bash
# Debian / Ubuntu
sudo apt-get install -y fontconfig fonts-dejavu fonts-liberation

# RHEL / Fedora
sudo dnf install -y fontconfig dejavu-sans-fonts liberation-fonts

# Alpine
sudo apk add fontconfig ttf-dejavu
```

## Docker

GroupDocs.Markdown runs in containers with no dependencies beyond a JRE. This multi-stage Dockerfile builds with Maven and runs on a slim JRE image:

```dockerfile
FROM maven:3.9-eclipse-temurin-17 AS build
WORKDIR /app
COPY . .
RUN mvn -q clean package

FROM eclipse-temurin:17-jre
WORKDIR /app

# Fonts are not included in slim JRE images
RUN apt-get update \
 && apt-get install -y --no-install-recommends fontconfig fonts-dejavu fonts-liberation \
 && rm -rf /var/lib/apt/lists/*

COPY --from=build /app/target/*-jar-with-dependencies.jar app.jar
ENTRYPOINT ["java", "-Djava.awt.headless=true", "-jar", "app.jar"]
```

### Build and Run

```bash
docker build -t markdown-demo .
docker run --rm -v $(pwd)/files:/app/files markdown-demo
```

## Supported Distributions

GroupDocs.Markdown for Java works on any Linux distribution with a Java SE 8+ runtime, including:

- Ubuntu 20.04+
- Debian 11+
- CentOS 8+, RHEL 8+
- Fedora 36+
- Alpine 3.16+
- Amazon Linux 2023
