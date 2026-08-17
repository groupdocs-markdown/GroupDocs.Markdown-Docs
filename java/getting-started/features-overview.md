---
id: features-overview
url: markdown/java/features-overview
title: Features overview
weight: 1
description: "Key features of GroupDocs.Markdown for Java — document to Markdown conversion with flavor control, image handling, front matter, and more"
keywords: features, markdown, conversion, image export, front matter, heading offset, async
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

## Overview

GroupDocs.Markdown for Java converts documents from various formats into clean, structured Markdown. It uses a custom DOM-based renderer that gives full control over every aspect of the output.

## Supported Input Formats

Convert from 20+ document formats including Word (DOCX, DOC, RTF), Excel (XLSX, XLS, CSV), PDF, EPUB, MOBI, TXT, and CHM. See the full list of [supported formats]({{< ref "markdown/java/getting-started/supported-document-formats.md" >}}).

## Key Features

### Static Convenience Methods

One-liner conversions that throw on failure — no result-checking ceremony. All exceptions are unchecked, so nothing forces a `try`/`catch`:

```java
String md = MarkdownConverter.toMarkdown("business-plan.docx");
MarkdownConverter.toFile("business-plan.docx", "output.md");
```

### Markdown Flavor Control

Target GitHub Flavored Markdown (pipe tables, strikethrough) or strict CommonMark:

```java
DocumentConvertOptions options = new DocumentConvertOptions();
options.setFlavor(MarkdownFlavor.GITHUB);
```

### Flexible Image Handling

Choose how images are processed during conversion:
- **Base64 embedding** — images inline in the Markdown (default)
- **File system export** — save images to disk with relative paths
- **Skip** — omit images from the output
- **Custom** — rename, replace, or redirect images via callback

### YAML Front Matter

Extract document metadata into YAML front matter for static site generators (Jekyll, Hugo, Docusaurus):

```java
DocumentConvertOptions options = new DocumentConvertOptions();
options.setIncludeFrontMatter(true);
```

### Heading Level Offset

Shift all heading levels when embedding converted content inside a larger document:

```java
DocumentConvertOptions options = new DocumentConvertOptions();
options.setHeadingLevelOffset(2);
// # Title → ### Title
```

### Spreadsheet Options

Control how Excel and CSV tables are rendered:
- Column and row truncation with ellipsis indicators
- Custom sheet separators
- Hidden worksheet filtering

### Document Inspection

Retrieve document metadata (format, page count, title, author) without performing a full conversion:

```java
DocumentInfo info = MarkdownConverter.getInfo("business-plan.docx");
```

### Page Selection

Convert specific pages or worksheets instead of the full document:

```java
DocumentConvertOptions options = new DocumentConvertOptions();
options.setPageNumbers(new int[] { 1, 3, 5 });
```

### Relative Image Paths

Control how image file paths appear in the Markdown output:

```java
ExportImagesToFileSystemStrategy strategy =
        new ExportImagesToFileSystemStrategy("output/images");
strategy.setImagesRelativePath("images");
```

### Image Replacement

Replace images in the source document with different images during conversion using `IImageSavingHandler` — a functional interface, so a stateless handler can be a lambda.

### Async API

`MarkdownConverterAsync` mirrors the static conversion methods, returning `CompletableFuture` for non-blocking use:

```java
String md = MarkdownConverterAsync.toMarkdownAsync("business-plan.docx").join();
```

### Proper Error Handling

Specific exception types for common error scenarios:
- `DocumentProtectedException` — wrong or missing password
- `InvalidFormatException` — corrupt or unrecognized file
- `GroupDocsMarkdownException` — general conversion error

### Conversion Warnings

Non-fatal issues are reported via `DocumentConvertResult.getWarnings()` — for example, when spreadsheet tables are truncated.

### Password-Protected Documents

Load encrypted documents by providing a password via `LoadOptions`:

```java
LoadOptions loadOptions = new LoadOptions(FileFormat.DOCX);
loadOptions.setPassword("secret");
```

### Cross-Platform Support

A single JAR runs on Windows, Linux, and macOS on any Java SE 8 or later runtime — no native dependencies and no per-platform artifacts.
