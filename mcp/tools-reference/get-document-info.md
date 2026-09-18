---
id: mcp-tool-get-document-info
url: markdown/mcp/tools-reference/get-document-info
title: get_document_info
weight: 2
description: "The get_document_info MCP tool returns format, page count, title, author, and encryption flag without performing a full Markdown conversion."
keywords: get_document_info MCP, page count before conversion, check document encrypted MCP, inspect document agent
productName: GroupDocs.Markdown MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`get_document_info` returns format, page count, title, author, and whether the file is encrypted — **without** doing the conversion. The precondition check before committing to a long document. Example prompt: *"How many pages is this, and is it protected?"*

**Tool description (as the AI agent sees it):**

> Returns document information (file format, page count, title, author, encryption flag) as JSON, without performing a full Markdown conversion. Supports PDF, DOCX, XLSX, EPUB, MOBI, and 20+ more formats recognized by GroupDocs.Markdown. Useful as a precondition check before ConvertToMarkdown — e.g. 'how many pages does this PDF have?' or to decide which pages to request or whether a password is needed. Returns a JSON object with `fileName`, `fileFormat`, `pageCount` (worksheet count for spreadsheets), `title`, `author`, and `isEncrypted`. Do NOT pre-check whether files exist — just pass the filename the user provided. The tool resolves files from storage and returns an error with available files if a name is not found. On failure, the response text starts with 'Document-info lookup failed for' followed by the underlying exception type, message, and inner chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "markdown/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "get_document_info",
  "arguments": {
    "file": {
      "filePath": "handbook.pdf"
    }
  }
}
```

## Result

A JSON object with the file format, page count, title, author, and encryption flag.

Two uses that save time: deciding whether to convert the whole document or a page range, and catching an encrypted file before the conversion fails — the agent can then ask you for the password instead of guessing.

On failure the text starts with `Document-info lookup failed for`, followed by the exception type and message.

## Example prompts

* *"How many pages does this document have?"*
* *"Is this PDF password-protected?"*
* *"What is the title and author before I convert it?"*
