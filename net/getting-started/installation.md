---
id: installation
url: markdown/net/installation
title: Install GroupDocs.Markdown for .NET
linkTitle: Installation
weight: 4
description: "This guide explains how to install GroupDocs.Markdown for .NET to your environment"
keywords: 
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

This topic describes how to add the **GroupDocs.Markdown** library to your .NET project. You can use a NuGet package to install this library or you can download necessary DLLs from the GroupDocs website: [https://downloads.groupdocs.com/markdown/net](https://downloads.groupdocs.com/markdown/net).  

## Install GroupDocs.Markdown using NuGet packages

You can use the following tools to install the [GroupDocs.Markdown](https://www.nuget.org/packages/GroupDocs.Markdown) NuGet package:

 * [NuGet Package Manager](#use-the-nuget-package-manager)
 * [Package Manager Console](#use-the-package-manager-console)
 * [.NET CLI](#use-the-net-cli)

### Use the NuGet Package Manager

Open your project or solution in Visual Studio and follow the steps below to install the **GroupDocs.Markdown** package using the [NuGet Package Manager](https://learn.microsoft.com/en-us/nuget/consume-packages/install-use-packages-visual-studio):

1. In **Solution Explorer**, right-click your project name and select **Manage NuGet Packages** to display the NuGet Package Manager.

    ![Manage NuGet packages in Visual Studio](/markdown/net/images/getting-started/installation/manage-nuget-packages.png)

2. Select the **Browse** tab and type **GroupDocs.Markdown** in the search box. Select the latest version of the **GroupDocs.Markdown** package and click **Install**.

    ![Install NuGet packages in Visual Studio](/markdown/net/images/getting-started/installation/install-nuget-package.png)

### Use the Package Manager Console

The [Package Manager Console](https://learn.microsoft.com/en-us/nuget/consume-packages/install-use-packages-powershell) uses PowerShell commands to install, update, and remove NuGet packages. Open your project in Visual Studio and click **Tools** -> **NuGet Package Manager** -> **Package Manager Console** to open the console window. Run the the following command to install the latest version of the **GroupDocs.Markdown** library:

{{< tabs "example1">}}
{{< tab "PowerShell" >}}
```shell
PM> Install-Package GroupDocs.Markdown
```
{{< /tab >}}
{{< /tabs >}}

![Use Package Manager Console ](/markdown/net/images/getting-started/installation/package-manager-console.png)

### Use the .NET CLI

You can also use the [.NET CLI tool](https://docs.microsoft.com/en-us/dotnet/core/tools/) to install and update NuGet packages. Open a terminal in your project's folder and execute the following command to install the **GroupDocs.Markdown** package:

{{< tabs "example2">}}
{{< tab ".NET CLI" >}}
```shell
dotnet add package GroupDocs.Markdown
```
{{< /tab >}}
{{< /tabs >}}

## Download GroupDocs.Markdown from the official website

Visit [https://releases.groupdocs.com/markdown/net/](https://releases.groupdocs.com/markdown/net/) and download the **GroupDocs.Markdown** assemblies as a ZIP archive or MSI installer. To reference the downloaded assembly files in your project, do the following:

1. Extract files from the ZIP archive or run the MSI installer to install **GroupDocs.Markdown** to a specific location on your computer.
2. Open your solution or project in Visual Studio.
3. In **Solution Explorer**, right-click the **References** or **Dependencies** node, and select **Add Reference** (for a .NET Framework project) or **Add Project Reference** (for a .NET Core project).
4. In the **Reference Manager** dialog box, select the **Browse** tab and click **Browse** to locate the _GroupDocs.Markdown.dll_ file for the target framework.

    ![Browse for the GroupDocs.Markdown assembly](/markdown/net/images/getting-started/installation/browse-for-groupdocs-dll.png)

5. Click **OK** to add a reference to the **GroupDocs.Markdown** library to your project.

{{< alert style="warning" >}}
If your application targets .NET Core / .NET 5+, ensure that your project has all the required dependencies installed. Refer to the following page for details: [GroupDocs.Markdown dependencies](https://www.nuget.org/packages/groupdocs.markdown#dependencies-body-tab).
{{< /alert >}}