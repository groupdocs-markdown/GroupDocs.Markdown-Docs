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
We offer multiple solutions on how you can run GroupDocs.Markdown examples, by building your own or using our back-end or front-end examples.

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
  
  {{< tabs "dotnet-cli-example" >}}
  {{< tab "C#" >}}
  ```csharp
    using GroupDocs.Markdown;

    string documentPath = "business-plan.docx";
    string outputPath = "converted.md";
  
	using (var converter = new MarkdownConverter(documentPath))
	{
		converter.Convert(outputPath);
	}
  ```
  {{< /tab >}}
  {{< tab "business-plan.docx" >}}
  {{< tab-text >}}
  `business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/business-plan.docx) to download it.
  {{< /tab-text >}}
  {{< /tab >}}
{{< tab "converted.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/getting-started/how-to-run-examples/DotnetCliExample/converted.md)
{{< /tab >}}
{{< /tabs >}}
  
7. Replace the `documentPath` value with the actual path to the document you're going to convert.
8. Run the project by executing the `dotnet run` command.
9. The converted document will be saved in the `C:\\output\\` directory.

### Build a project using Visual Studio

1. Open Visual Studio and go to **File** -> **New** -> **Project**.
2. Select the appropriate project type - Console App, ASP.NET Web Application etc.
3. Install **GroupDocs.Markdown for .NET** from Nuget or the official GroupDocs website following this [guide]({{< ref "markdown/net/getting-started/installation.md" >}}).
4. Add the following code to the `Main` method:

  {{< tabs "visual-studio-example" >}}
  {{< tab "C#" >}}
  ```csharp
    using GroupDocs.Markdown;

    string documentPath = "business-plan.docx";
    string outputPath = "converted.md";
  
	using (var converter = new MarkdownConverter(documentPath))
	{
		converter.Convert(outputPath);
	}
  ```
  {{< /tab >}}
  {{< tab "business-plan.docx" >}}
  {{< tab-text >}}
  `business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/business-plan.docx) to download it.
  {{< /tab-text >}}
  {{< /tab >}}
{{< tab "converted.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/getting-started/how-to-run-examples/VisualStudioExample/converted.md)
{{< /tab >}}
{{< /tabs >}}

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