---
id: how-to-run-examples
url: markdown/java/how-to-run-examples
title: How to run examples
weight: 7
description: "This article describes how to run Java file markdown API code examples."
keywords: file markdown, Java, Maven, IntelliJ IDEA
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: true
---
<!--
{{< alert style="warning" >}}Before running an example make sure that GroupDocs.Markdown has been installed successfully.{{< /alert >}}

This article describes how to run Java file markdown API code examples.
-->
We offer multiple solutions on how you can run GroupDocs.Markdown examples, by building your own or using our back-end or front-end examples.

<!--Please choose one from the following list:-->

## Build a project from scratch

You can build a project from scratch using [Apache Maven](https://maven.apache.org/) from the command line or using IntelliJ IDEA. We'll step you through both cases.

### Build a project using Maven

1. Make sure you have a JDK 8 or later and Maven installed. Verify with `java -version` and `mvn -version`.
2. Create a project by executing `mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=markdown-demo -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false` in your terminal.
3. Navigate to the `markdown-demo` directory by executing the `cd markdown-demo` command.
4. Add the GroupDocs repository and the `com.groupdocs:groupdocs-markdown` dependency to `pom.xml`, following the [Installation]({{< ref "markdown/java/getting-started/installation.md" >}}) guide.
5. Edit `src/main/java/com/mycompany/app/App.java` and add the following lines to the `main` method:

  {{< tabs "maven-example" >}}
  {{< tab "App.java" >}}
  ```java
package com.mycompany.app;

import com.groupdocs.markdown.MarkdownConverter;

public class App {

    public static void main(String[] args) {
        String documentPath = "business-plan.docx";
        String outputPath = "converted.md";

        try (MarkdownConverter converter = new MarkdownConverter(documentPath)) {
            converter.convert(outputPath);
        }
    }
}
  ```
  {{< /tab >}}
  {{< tab "business-plan.docx" >}}
  {{< tab-text >}}
  `business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/business-plan.docx) to download it.
  {{< /tab-text >}}
  {{< /tab >}}
{{< /tabs >}}
  
6. Replace the `documentPath` value with the actual path to the document you're going to convert.
7. Build and run the project by executing `mvn compile exec:java -Dexec.mainClass=com.mycompany.app.App`.
8. The converted document is written to `converted.md` in the directory you ran the command from.

### Build a project using IntelliJ IDEA

1. Open IntelliJ IDEA and go to **File** -> **New** -> **Project**.
2. Select **Java** and choose **Maven** or **Gradle** as the build system.
3. Add **GroupDocs.Markdown for Java** to your build file following this [guide]({{< ref "markdown/java/getting-started/installation.md" >}}).
4. Add the following code to the `main` method:

  {{< tabs "intellij-example" >}}
  {{< tab "App.java" >}}
  ```java
package com.mycompany.app;

import com.groupdocs.markdown.MarkdownConverter;

public class App {

    public static void main(String[] args) {
        String documentPath = "business-plan.docx";
        String outputPath = "converted.md";

        try (MarkdownConverter converter = new MarkdownConverter(documentPath)) {
            converter.convert(outputPath);
        }
    }
}
  ```
  {{< /tab >}}
  {{< tab "business-plan.docx" >}}
  {{< tab-text >}}
  `business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/business-plan.docx) to download it.
  {{< /tab-text >}}
  {{< /tab >}}
{{< /tabs >}}

5. Replace the `documentPath` value with the actual path to the document you're going to convert.
6. Build and run your project.
7. The converted document is written to `converted.md` in the project's working directory.

## Run back-end examples

You can find many back-end examples in our [GitHub](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-Java) repository. You can either download the ZIP file from [here](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-Java/archive/master.zip) or clone the repository from GitHub using your favorite Git client.  
In case you download the ZIP file, extract the folders on your local disk.

1. Navigate to the `Examples` directory and open its `pom.xml` in IntelliJ IDEA, Eclipse, or NetBeans.
2. Open the `RunExamples.java` file and uncomment the example(s) that you would like to run.
3. Optionally, you can set the path to the license in the `Utils.java` file.

## Run demo projects

To run any demo from [GroupDocs.Markdown for Java Demo projects](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-Java/tree/master/Demos/), you can either:

* Clone the repository:

  ```bash
  git clone git@github.com:groupdocs-markdown/GroupDocs.Markdown-for-Java.git  
  ```

* or [download](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-Java/archive/master.zip) the source code.

## Contribute

If you like to add or improve an example, we encourage you to contribute to the project. All examples in this repository are open source and can be freely used in your own applications.  
To contribute, you can fork the repository, edit the code and create a pull request. We will review the changes and include them in the repository if found helpful.