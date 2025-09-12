---
id: convert
url: markdown/net/convert
title: Convert files to various formats
weight: 1
description: "Artcles listed in this page explain the common usage scenarios when documents are stored in a local drive and you want to manage them using GroupDocs.Markdown API"
keywords: common usage
productName: GroupDocs.Markdown for .NET
hideChildren: False
structuredData:
    showOrganization: True
---

**[GroupDocs.Markdown](https://products.groupdocs.com/markdown/net)** provides a quick and easy way to convert files from some source format to various ranges of md format. The conversion process from the user's point of view is pretty simple - the source document is loaded to a converter and after conversion is completed, the result is saved to a desired file path on the local disk or other storage.  
  
By default, when performing internal calculations GroupDocs.Markdown for .NET uses some predefined settings that are most suitable for loading and saving specified file formats. However, the markdown process can always be adjusted by setting specific [LoadOptions](https://reference.groupdocs.com/markdown/net/groupdocs.markdown.options.load) to modify the way the source document is loaded - for example, it's needed to hide document comments, set up font substitution, set passwords for protected documents, etc. Also, the [DocumentConvertOptions](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/documentconverteroptions/) class is used to manage converted documents.  
  
The common markdown workflow always includes the following steps:

1. Loading the source document into a new instance of the [MarkdownConverter](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/markdownconverter/) class. You can provide a file path or a document stream.
2. Instantiate the appropriate [DocumentConvertOptions](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/documentconverteroptions/) object according to your requirements. 
3. Call the [Convert](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/markdownconverter/convert/) method of the [DocumentConvertOptions](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/documentconverteroptions/) object and pass the file path to save the resulting document with the convert options object from the previous step.  
  
These documentation articles explain how to convert files to the most popular formats: