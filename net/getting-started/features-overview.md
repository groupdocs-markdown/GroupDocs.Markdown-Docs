---
id: features-overview
url: markdown/net/features-overview
title: Features overview
weight: 1
description: "Key features of GroupDocs.Markdown for .NET — document to Markdown conversion with flavor control, image handling, front matter, and more"
keywords: features, markdown, conversion, image export, front matter, heading offset, async
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

## Overview

GroupDocs.Markdown for .NET converts documents from various formats into clean, structured Markdown. It uses a custom DOM-based renderer that gives full control over every aspect of the output.

## Supported Input Formats

Convert from 20+ document formats including Word (DOCX, DOC, RTF), Excel (XLSX, XLS, CSV), PDF, EPUB, MOBI, TXT, and CHM. See the full list of [supported formats]({{< ref "markdown/net/getting-started/supported-document-formats.md" >}}).

## Key Features

### Static Convenience Methods

One-liner conversions that throw on failure — no result-checking ceremony:

```csharp
string md = MarkdownConverter.ToMarkdown("business-plan.docx");
MarkdownConverter.ToFile("business-plan.docx", "output.md");
```

### Markdown Flavor Control

Target GitHub Flavored Markdown (pipe tables, strikethrough) or strict CommonMark:

```csharp
var options = new ConvertOptions { Flavor = MarkdownFlavor.GitHub };
```

### Flexible Image Handling

Choose how images are processed during conversion:
- **Base64 embedding** — images inline in the Markdown (default)
- **File system export** — save images to disk with relative paths
- **Skip** — omit images from the output
- **Custom** — rename, replace, or redirect images via callback

### YAML Front Matter

Extract document metadata into YAML front matter for static site generators (Jekyll, Hugo, Docusaurus):

```csharp
var options = new ConvertOptions { IncludeFrontMatter = true };
```

### Heading Level Offset

Shift all heading levels when embedding converted content inside a larger document:

```csharp
var options = new ConvertOptions { HeadingLevelOffset = 2 };
// # Title → ### Title
```

### Spreadsheet Options

Control how Excel and CSV tables are rendered:
- Column and row truncation with ellipsis indicators
- Custom sheet separators
- Hidden worksheet filtering

### Document Inspection

Retrieve document metadata (format, page count, title, author) without performing a full conversion:

```csharp
DocumentInfo info = MarkdownConverter.GetInfo("business-plan.docx");
```

### Page Selection

Convert specific pages or worksheets instead of the full document:

```csharp
var options = new ConvertOptions { PageNumbers = new[] { 1, 3, 5 } };
```

### Relative Image Paths

Control how image file paths appear in the Markdown output:

```csharp
var strategy = new ExportImagesToFileSystemStrategy("output/images")
{
    ImagesRelativePath = "images"
};
```

### Image Replacement

Replace images in the source document with different images during conversion using `IImageSavingHandler`.

### Async API

All static and instance methods have async counterparts with true async file I/O:

```csharp
string md = await MarkdownConverter.ToMarkdownAsync("business-plan.docx");
```

### Proper Error Handling

Specific exception types for common error scenarios:
- `DocumentProtectedException` — wrong or missing password
- `InvalidFormatException` — corrupt or unrecognized file
- `GroupDocsMarkdownException` — general conversion error

### Conversion Warnings

Non-fatal issues are reported via `ConvertResult.Warnings` — for example, when spreadsheet tables are truncated.

### Password-Protected Documents

Load encrypted documents by providing a password via `LoadOptions`:

```csharp
var loadOptions = new LoadOptions(FileFormat.Docx) { Password = "secret" };
```

### Cross-Platform Support

Works on Windows, Linux, and macOS with .NET Framework 4.6.2+, .NET 6.0+, .NET 8.0+, and .NET 10.0+.
