---
id: installation
url: markdown/net/installation
title: Install GroupDocs.Markdown for .NET
linkTitle: Installation
weight: 4
description: "How to install GroupDocs.Markdown for .NET using NuGet, .NET CLI, or from the official website."
keywords: GroupDocs.Markdown, install, NuGet, .NET CLI, Visual Studio
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

This topic describes how to add the **GroupDocs.Markdown** library to your .NET project.

## Install from NuGet

[GroupDocs.Markdown](https://www.nuget.org/packages/GroupDocs.Markdown) is available on NuGet. The main package is a meta-package that automatically pulls in the correct runtime package for your project's target framework.

### Using .NET CLI

Open a terminal in your project folder and run:

```bash
dotnet add package GroupDocs.Markdown
```

### Using Package Manager Console

In Visual Studio, open **Tools** > **NuGet Package Manager** > **Package Manager Console** and run:

```powershell
Install-Package GroupDocs.Markdown
```

### Using PackageReference

Add directly to your `.csproj` file:

```xml
<PackageReference Include="GroupDocs.Markdown" Version="26.3" />
```

## Runtime Packages

The NuGet package includes assemblies for four target frameworks:

| Target Framework | Runtime Package |
| --- | --- |
| .NET Framework 4.6.2 | GroupDocs.Markdown.Net462 |
| .NET 6.0 | GroupDocs.Markdown.Net60 |
| .NET 8.0 | GroupDocs.Markdown.Net80 |
| .NET 10.0 | GroupDocs.Markdown.Net100 |

In most cases, install only the main `GroupDocs.Markdown` package. NuGet will resolve the correct runtime package automatically. You can also install a specific runtime package directly if needed:

```bash
dotnet add package GroupDocs.Markdown.Net80
```

## Download from the Official Website

You can also download the assemblies as a ZIP archive or MSI installer from the [GroupDocs Releases](https://releases.groupdocs.com/markdown/net/) website.

1. Download the ZIP or MSI for the desired version.
2. Extract files (ZIP) or run the installer (MSI).
3. In your project, add a reference to the `GroupDocs.Markdown.dll` file for the target framework you need (e.g., `bin/net8.0/GroupDocs.Markdown.dll`).

## Verify Installation

After installing, verify that the package is accessible:

{{< tabs "verify-install" >}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// List all supported formats
foreach (FileFormat format in MarkdownConverter.GetSupportedFormats())
    Console.WriteLine(format);
```
{{< /tab >}}
{{< /tabs >}}
