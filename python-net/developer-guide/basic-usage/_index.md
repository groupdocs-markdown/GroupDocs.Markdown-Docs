---
id: basic-usage
url: markdown/python-net/basic-usage
title: Basic Usage
weight: 1
description: "Articles listed in this page explain the common usage scenarios when documents are stored in a local drive and you want to manage them using GroupDocs.Markdown API"
keywords: common usage
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
structuredData:
    showOrganization: True
---
## Quick start with GroupDocs.Markdown API

GroupDocs.Markdown provides both static methods and an instance API for converting documents to Markdown with just a few lines of code.

**Static methods** -- call `MarkdownConverter.to_markdown()` or `MarkdownConverter.to_file()` for one-line conversions without managing object lifetime.

**Instance API** -- create a `MarkdownConverter` instance when you need to inspect document metadata first with `get_document_info()`, or perform multiple operations on the same document.

Explore the topics in this section:

* [Convert files]({{< ref "markdown/python-net/developer-guide/basic-usage/convert/" >}}) -- convert PDF, Word, Excel, EPUB, and text documents to Markdown.
* [Get document info]({{< ref "markdown/python-net/developer-guide/basic-usage/get-document-info" >}}) -- retrieve document metadata such as format, page count, title, and author without performing a full conversion.
