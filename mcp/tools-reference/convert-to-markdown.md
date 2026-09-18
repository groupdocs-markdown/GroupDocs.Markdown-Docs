---
id: mcp-tool-convert-to-markdown
url: markdown/mcp/tools-reference/convert-to-markdown
title: convert_to_markdown
weight: 1
description: "The convert_to_markdown MCP tool converts PDF, Word, Excel, EPUB and 20+ other formats to clean structured Markdown, with control over images, pages, dialect, and front matter."
keywords: convert_to_markdown MCP tool, PDF to markdown AI agent, document to markdown RAG, EPUB to markdown MCP
productName: GroupDocs.Markdown MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`convert_to_markdown` turns a document into **clean, structured Markdown**. PDF, Word, Excel, EPUB, MOBI, CHM, TXT and 20+ more formats go in; a `.md` file comes out, with the layout, headings, lists, and tables preserved. Example prompt: *"Convert handbook.pdf to Markdown for my knowledge base."*

**Tool description (as the AI agent sees it):**

> Converts a document to clean, structured Markdown (.md). Supports PDF, DOCX/DOC/RTF/ODT, XLSX/XLS/ODS/CSV/TSV, EPUB, MOBI, TXT, CHM and 20+ more formats. By default, images are embedded as base64 data URIs so the output is fully self-contained. Use 'images' to control image handling: 'base64' (default), 'file' (save images alongside the .md and reference by path), or 'skip' (omit images — text-only). Use 'pages' to limit output to specific 1-based pages or worksheets. The generated Markdown is saved to storage AND the content is returned inline. Returns the saved file path followed by the Markdown content (long output is truncated inline — the saved .md holds the full text). Call this tool immediately whenever the user asks to convert a document to Markdown, export as MD, or extract as Markdown. Do NOT pre-check whether files exist — just pass the filename the user provided. The tool resolves files from storage and returns an error with available files if a name is not found. On failure, the response text starts with 'Conversion to Markdown failed for' followed by the underlying exception type, message, and inner chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "markdown/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `images` | string | no | Image handling: 'base64' (default — embed as data URIs, self-contained), 'file' (save images alongside .md), or 'skip' (text-only, no images) |
| `pages` | string | no | Comma-separated 1-based page or worksheet numbers to convert, e.g. '1,3,5'. Omit for the whole document. |
| `frontMatter` | boolean | no | Include YAML front matter (title, author, format, page count) at the top of the output |
| `flavor` | string | no | Markdown dialect: 'github' (default) or 'commonmark' |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "convert_to_markdown",
  "arguments": {
    "file": {
      "filePath": "handbook.pdf"
    },
    "images": "file",
    "frontMatter": true,
    "flavor": "github"
  }
}
```

## Result

A saved-path message naming the `.md` file in your output folder — plus the extracted image files when `images: "file"`.

The four options are the reason to use this server rather than a generic converter:

| Option | Values | When it matters |
|---|---|---|
| `images` | `base64` (default), `file`, or none | `base64` for a self-contained artefact; `file` for repositories and RAG indexes |
| `pages` | `1,3,5` | Convert a section instead of a 400-page book |
| `frontMatter` | `true` / `false` | YAML title, author, format, page count — for static sites and chunk metadata |
| `flavor` | `github` (default), `commonmark` | Match whatever will render or parse the result |

On failure the text starts with `Markdown conversion failed for`, followed by the exception type and message.

## Example prompts

* *"Convert handbook.pdf to Markdown for my knowledge base."*
* *"Turn this EPUB into Markdown with images saved as files."*
* *"Convert only pages 10-12 and include front matter."*
* *"Give me CommonMark, not GitHub flavour."*

See it used end-to-end: [Convert documents to Markdown for RAG]({{< ref "markdown/mcp/use-cases/convert-documents-for-rag.md" >}}).
