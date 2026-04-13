---
id: agents-and-llm-integration
url: /markdown/net/agents-and-llm-integration
title: Agents and LLM integration
linkTitle: Agents and LLMs
description: "GroupDocs.Markdown for .NET is AI agent and LLM friendly — machine-readable documentation, MCP server, structured output for RAG pipelines, and seamless integration with AI tools."
weight: 9
keywords: AI, LLM, agent, RAG, MCP, machine-readable, documentation, Claude, GPT, Copilot
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

## AI agent and LLM friendly

GroupDocs.Markdown for .NET is designed to work seamlessly with AI agents, LLMs, and automated code generation tools. The library ships machine-readable documentation in multiple formats so that AI assistants can discover and use the API without manual guidance.

## MCP server

GroupDocs provides an [MCP (Model Context Protocol) server](https://docs.groupdocs.com/mcp) that enables LLMs to query the documentation on demand instead of loading it all at once. This saves tokens and lets your AI assistant fetch only the information it needs for the current task.

To connect your AI tool to the MCP server, add the GroupDocs endpoint to your MCP configuration:

{{< tabs "mcp-setup">}}
{{< tab "Claude Code / Claude Desktop" >}}
```json
// Claude Code:   ~/.claude/settings.json (or project .mcp.json)
// Claude Desktop: ~/Library/Application Support/Claude/claude_desktop_config.json
{
  "mcpServers": {
    "groupdocs-docs": {
      "url": "https://docs.groupdocs.com/mcp"
    }
  }
}
```
{{< /tab >}}
{{< tab "GitHub Copilot" >}}
```json
// .vscode/mcp.json in your project root
{
  "servers": {
    "groupdocs-docs": {
      "url": "https://docs.groupdocs.com/mcp"
    }
  }
}
```
{{< /tab >}}
{{< tab "Cursor" >}}
```json
// .cursor/mcp.json in your project root
{
  "mcpServers": {
    "groupdocs-docs": {
      "url": "https://docs.groupdocs.com/mcp"
    }
  }
}
```
{{< /tab >}}
{{< tab "OpenCode" >}}
```json
// ~/.config/opencode/config.json
{
  "mcpServers": {
    "groupdocs-docs": {
      "url": "https://docs.groupdocs.com/mcp"
    }
  }
}
```
{{< /tab >}}
{{< tab "Generic MCP" >}}
```json
// Any MCP-compatible client
{
  "mcpServers": {
    "groupdocs-docs": {
      "url": "https://docs.groupdocs.com/mcp"
    }
  }
}
```
{{< /tab >}}
{{< /tabs >}}

See [https://docs.groupdocs.com/mcp](https://docs.groupdocs.com/mcp) for full setup instructions and the list of available tools.

## Machine-readable documentation

Every documentation page is available as a plain Markdown file that AI tools can fetch and process directly:

| Resource | URL |
|---|---|
| Full documentation (single file) | `https://docs.groupdocs.com/markdown/net/llms-full.txt` |
| Full documentation (all products) | `https://docs.groupdocs.com/markdown/llms-full.txt` |
| Individual page (any page) | Append `.md` to the page URL, e.g. `https://docs.groupdocs.com/markdown/net.md` |
| Quick start guide | `https://docs.groupdocs.com/markdown/net/quick-start-guide.md` |

### How to use with AI tools

Point your AI assistant to the full documentation file for comprehensive context:

```
Fetch https://docs.groupdocs.com/markdown/net/llms-full.txt and use it
as a reference for GroupDocs.Markdown for .NET API.
```

Or reference individual pages for focused tasks:

```
Read https://docs.groupdocs.com/markdown/net/quick-start-guide.md
and help me convert a PDF to Markdown.
```

## Why Markdown output is ideal for AI pipelines

GroupDocs.Markdown converts documents into clean, structured Markdown — the preferred input format for LLMs and RAG systems:

- **Preserves document structure** — headings, lists, tables, and emphasis are retained as semantic markup
- **No binary noise** — unlike PDF or DOCX, Markdown is plain text that tokenizes efficiently
- **Chunk-friendly** — split by headings (`## `) for embedding and retrieval
- **Deterministic output** — same input always produces the same Markdown, enabling reliable pipelines

```csharp
using GroupDocs.Markdown;

// Convert any document to LLM-ready Markdown
var options = new ConvertOptions
{
    ImageExportStrategy = new SkipImagesStrategy(), // text-only for RAG
    Flavor = MarkdownFlavor.CommonMark
};

string markdown = MarkdownConverter.ToMarkdown("professional-services.pdf", options);

// Split into chunks by headings for embedding
string[] chunks = markdown.Split(
    new[] { "\n## ", "\n# " },
    StringSplitOptions.RemoveEmptyEntries);
```

## See also

- [Convert documents for RAG pipelines]({{< ref "markdown/net/developer-guide/use-cases/convert-for-rag" >}})
- [API Reference](https://reference.groupdocs.com/markdown/net)
