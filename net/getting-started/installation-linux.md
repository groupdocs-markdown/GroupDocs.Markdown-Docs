---
id: installation-linux
url: markdown/net/installation-linux
title: Install GroupDocs.Markdown for .NET on Linux
linkTitle: Linux Installation
weight: 5
description: "How to install and run GroupDocs.Markdown for .NET on Linux and in Docker containers."
keywords: GroupDocs.Markdown, Linux, Docker, Ubuntu, Alpine, .NET
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

This article explains how to install and run **GroupDocs.Markdown for .NET** on Linux. GroupDocs.Markdown NuGet package references all required native libraries. 

## Prerequisites

Install the .NET SDK (6.0 or later) for your distribution. See [Install .NET on Linux](https://learn.microsoft.com/en-us/dotnet/core/install/linux) for instructions.

## Install the Package

Create a new project or navigate to an existing one, then add the package:

{{< tabs "linux-install" >}}
{{< tab "C#" >}}
```bash
dotnet new console -n MarkdownDemo
cd MarkdownDemo
dotnet add package GroupDocs.Markdown
```
{{< /tab >}}
{{< /tabs >}}

## Run Your Application

{{< tabs "linux-run" >}}
{{< tab "C#" >}}
```bash
dotnet run
```
{{< /tab >}}
{{< /tabs >}}

## Docker

GroupDocs.Markdown runs in Docker containers with no additional dependencies beyond the .NET runtime.

### Example Dockerfile

{{< tabs "docker-example" >}}
{{< tab "C#" >}}
```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /app
COPY . .
RUN dotnet publish -c Release -o /publish

FROM mcr.microsoft.com/dotnet/runtime:8.0
WORKDIR /app
COPY --from=build /publish .
ENTRYPOINT ["dotnet", "MarkdownDemo.dll"]
```
{{< /tab >}}
{{< /tabs >}}

### Build and Run

{{< tabs "docker-run" >}}
{{< tab "C#" >}}
```bash
docker build -t markdown-demo .
docker run --rm -v $(pwd)/files:/app/files markdown-demo
```
{{< /tab >}}
{{< /tabs >}}

## Supported Distributions

GroupDocs.Markdown for .NET works on any Linux distribution that supports .NET 6.0+, including:

- Ubuntu 20.04+
- Debian 11+
- CentOS 8+, RHEL 8+
- Fedora 36+
- Alpine 3.16+
- Amazon Linux 2023
