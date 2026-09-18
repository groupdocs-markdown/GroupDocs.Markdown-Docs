---
id: mcp-tools-reference
url: markdown/mcp/tools-reference
title: Tools reference
weight: 2
description: "Complete reference of every tool the GroupDocs.Markdown MCP server exposes to AI agents, with parameters, example prompts, and results."
keywords: MCP tools list markdown conversion, convert_to_markdown MCP tool, document to markdown MCP, RAG ingestion tools reference
productName: GroupDocs.Markdown MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

Complete reference of every tool the GroupDocs.Markdown MCP server exposes to AI agents, with parameters, example prompts, and results. Captured from a live `tools/list` call against server version **26.9.0** (raw capture: `tools-list.generated.json` in this section's source).

| Tool | What it does |
|---|---|
| [`convert_to_markdown`]({{< ref "markdown/mcp/tools-reference/convert-to-markdown.md" >}}) | Converts a document to clean, structured Markdown with controllable image handling |
| [`get_document_info`]({{< ref "markdown/mcp/tools-reference/get-document-info.md" >}}) | Returns format, page count, title, author, and encryption flag |
| [`get_license_status`]({{< ref "markdown/mcp/tools-reference/get-license-status.md" >}}) | Reports the active licensing mode and, under metered licensing, consumption |

## The FileInput shape

Every tool takes its document through the same `file` object — pass **either** a name from your storage folder **or** inline content:

```json
{ "file": { "filePath": "handbook.pdf" } }
```

| Field | Type | Description |
|---|---|---|
| `filePath` | string | File path or name in the configured storage folder |
| `fileContent` | string | Base64-encoded file content (alternative to `filePath`) |
| `fileName` | string | Original filename with extension — required with `fileContent`. Since **26.9.0** it also works on its own, resolved from the storage folder exactly like `filePath` |

You rarely write this JSON yourself: the AI agent does, from your plain-language prompt. Missing files are not an error to fear — the tool responds with the list of available files so the agent can correct itself.
