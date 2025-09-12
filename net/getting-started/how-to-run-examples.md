---
id: how-to-run-examples
url: markdown/net/how-to-run-examples
title: How to run examples
weight: 7
description: "This article describes how to run .NET file markdown API code examples."
keywords: file markdown, C#
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: true
---
<!--
{{< alert style="warning" >}}Before running an example make sure that GroupDocs.Markdown has been installed successfully.{{< /alert >}}

This article describes how to run .NET file markdown API code examples.
-->
We offer multiple solutions on how you can run GroupDocs.Markdown examples, by building your own or using our back-end or front-end examples.

<!--Please choose one from the following list:-->

## Build a project from scratch

You can build a project from scratch using Visual Studio or [.NET CLI](https://docs.microsoft.com/en-us/dotnet/core/tools/). We'll step you through both cases.

### Build a project using .NET CLI

1. Make sure you have .NET SDK installed <https://dotnet.microsoft.com/download>.
2. Create a directory for your console app by executing the `mkdir my-console-app` command in your terminal.
3. Navigate to the `my-console-app` directory by executing the `cd my-console-app` command.
4. Create an empty console app by executing the `dotnet new console` command.
5. Add the GroupDocs.Markdown for .NET package by executing the `dotnet add package GroupDocs.Markdown` command.
6. Edit `Program.cs` and add the following lines to the `Main` method:
  
  ```csharp
    using GroupDocs.Markdown;

    string documentPath = @"C:\sample.docx"; // NOTE: Put here actual path for your document
    string outputPath = @"C:\output\converted.md";
  
	using (var converter = new MarkdownConverter(documentPath))
	{
		converter.Convert(CoutputPath);
	}
  ```
  
7. Replace the `documentPath` value with the actual path to the document you're going to convert.
8. Run the project by executing the `dotnet run` command.
9. The converted document will be saved in the `C:\\output\\` directory.

### Build a project using Visual Studio

1. Open Visual Studio and go to **File** -> **New** -> **Project**.
2. Select the appropriate project type - Console App, ASP.NET Web Application etc.
3. Install **GroupDocs.Markdown for .NET** from Nuget or the official GroupDocs website following this [guide]({{< ref "markdown/net/getting-started/installation.md" >}}).
4. Add the following code to the `Main` method:

  ```csharp
    using GroupDocs.Markdown;

    string documentPath = @"C:\sample.docx"; // NOTE: Put here actual path for your document
    string outputPath = @"C:\output\converted.md";
  
	using (var converter = new MarkdownConverter(documentPath))
	{
		converter.Convert(CoutputPath);
	}
  ```

5. Replace the `documentPath` value with the actual path to the document you're going to convert.
6. Build and Run your project.
7. The converted document will be saved in the `C:\\output\\` directory.

## Run back-end examples

You can find many back-end examples in our [GitHub](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET) repository. You can either download the ZIP file from [here](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET/archive/master.zip) or clone the repository from GitHub using your favorite Git client.  
In case you download the ZIP file, extract the folders on your local disk.

1. Navigate to the `Examples` directory and open the `GroupDocs.Markdown.Examples.CSharp.sln` solution using Visual Studio.
2. Open the `RunExamples.cs` file and uncomment the example(s) that you would like to run.
3. Optionally, you can set the path to the license in `Utils.cs` file.

## Run demo projects

To run any demo from [GroupDocs.Markdown for .NET Demo projects](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET/tree/master/Demos/), you can either:

* Clone the repository:

  ```bash
  git clone git@github.com:groupdocs-markdown/GroupDocs.Markdown-for-.NET.git  
  ```

* or [download](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET/archive/master.zip) the source code.

## Contribute

If you like to add or improve an example, we encourage you to contribute to the project. All examples in this repository are open source and can be freely used in your own applications.  
To contribute, you can fork the repository, edit the code and create a pull request. We will review the changes and include them in the repository if found helpful.