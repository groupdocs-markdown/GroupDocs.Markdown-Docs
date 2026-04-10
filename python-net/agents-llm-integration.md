---
id: agents-and-llm-integration
url: /markdown/python-net/agents-and-llm-integration
title: Agents and LLM integration
linkTitle: Agents and LLMs
description: "GroupDocs.Markdown for Python via .NET is AI agent and LLM friendly — machine-readable documentation, MCP server, AGENTS.md shipped in the package, and structured output for RAG pipelines."
weight: 9
keywords: AI, LLM, agent, RAG, MCP, machine-readable, documentation, Claude, GPT, Copilot, AGENTS.md
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

## AI agent and LLM friendly

GroupDocs.Markdown for Python via .NET is designed to work seamlessly with AI agents, LLMs, and automated code generation tools. The library ships machine-readable documentation in multiple formats — including an `AGENTS.md` file inside the pip package itself — so that AI assistants can discover and use the API without manual guidance.

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

## AGENTS.md — built into the package

The `groupdocs-markdown-net` pip package includes an `AGENTS.md` file at `groupdocs/markdown/AGENTS.md`. AI coding assistants that scan installed packages (such as Claude Code, Cursor, GitHub Copilot) can automatically discover the API surface, usage patterns, and troubleshooting tips.

After installing the package, you can find it at:

```bash
pip show -f groupdocs-markdown-net | grep AGENTS
```

## Machine-readable documentation

Every documentation page is available as a plain Markdown file that AI tools can fetch and process directly:

| Resource | URL |
|---|---|
| Full documentation (single file) | `https://docs.groupdocs.com/markdown/python-net/llms-full.txt` |
| Full documentation (all products) | `https://docs.groupdocs.com/markdown/llms-full.txt` |
| Individual page (any page) | Append `.md` to the page URL, e.g. `https://docs.groupdocs.com/markdown/python-net.md` |
| Quick start guide | `https://docs.groupdocs.com/markdown/python-net/quick-start-guide.md` |

### How to use with AI tools

Point your AI assistant to the full documentation file for comprehensive context:

```
Fetch https://docs.groupdocs.com/markdown/python-net/llms-full.txt and use it
as a reference for GroupDocs.Markdown for Python via .NET API.
```

Or reference individual pages for focused tasks:

```
Read https://docs.groupdocs.com/markdown/python-net/quick-start-guide.md
and help me convert a PDF to Markdown.
```

## Why Markdown output is ideal for AI pipelines

GroupDocs.Markdown converts documents into clean, structured Markdown — the preferred input format for LLMs and RAG systems:

- **Preserves document structure** — headings, lists, tables, and emphasis are retained as semantic markup
- **No binary noise** — unlike PDF or DOCX, Markdown is plain text that tokenizes efficiently
- **Chunk-friendly** — split by headings (`## `) for embedding and retrieval
- **Deterministic output** — same input always produces the same Markdown, enabling reliable pipelines

```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, SkipImagesStrategy, MarkdownFlavor

# Convert any document to LLM-ready Markdown
options = ConvertOptions()
options.image_export_strategy = SkipImagesStrategy()  # text-only for RAG
options.flavor = MarkdownFlavor.COMMON_MARK

md = MarkdownConverter.to_markdown("business-plan.pdf", convert_options=options)

# Split into chunks by headings for embedding
import re
chunks = re.split(r'\n#{1,2} ', md)
```

## AGENTS.md reference

The content below is the same `AGENTS.md` file that ships inside the `groupdocs-markdown-net` package. Copy it into your project as `AGENTS.md` or point your AI assistant to this page.

````markdown
# GroupDocs.Markdown for Python via .NET -- AGENTS.md

> Instructions for AI agents working with this package.

Convert documents to/from Markdown -- DOCX, PDF, XLSX, EPUB, HTML and 20+ formats.

## Install

```bash
pip install groupdocs-markdown-net
```

**Python**: 3.5 - 3.14 | **Platforms**: Windows, Linux, macOS

## Resources

| Resource | URL |
|---|---|
| Documentation | https://docs.groupdocs.com/markdown/python-net/ |
| LLM-optimized docs | https://docs.groupdocs.com/markdown/python-net/llms-full.txt |
| API reference | https://reference.groupdocs.com/markdown/python-net/ |
| Code examples | https://docs.groupdocs.com/markdown/python-net/developer-guide/ |
| Release notes | https://releases.groupdocs.com/markdown/python-net/release-notes/ |
| PyPI | https://pypi.org/project/groupdocs-markdown-net/ |
| Free support forum | https://forum.groupdocs.com/c/markdown/ |
| Temporary license | https://purchase.groupdocs.com/temporary-license |

## MCP Server

Connect your AI tool to the GroupDocs documentation server for on-demand API lookups:

```json
{
  "mcpServers": {
    "groupdocs-docs": {
      "url": "https://docs.groupdocs.com/mcp"
    }
  }
}
```

Works with Claude Code (`~/.claude/settings.json`), Cursor (`.cursor/mcp.json`), VS Code Copilot (`.vscode/mcp.json`), and any MCP-compatible client.

## Imports

```python
from groupdocs.markdown import License, ConvertOptions, ConvertResult, CustomImageSavingArgs, CustomImagesStrategy, CustomUriExportStrategy, DefaultUriExportStrategy, DocumentInfo, ExportImagesAsBase64Strategy, ExportImagesToFileSystemStrategy, ExportOptions, FileFormat, LoadOptions, MarkdownConverter, MarkdownFlavor, SkipImagesStrategy, UriSavingArgs, DocumentProtectedException
```

## Quick Start

```python
from groupdocs.markdown import MarkdownConverter

# Convert to string
md = MarkdownConverter.to_markdown("report.docx")
print(md)

# Save to file
MarkdownConverter.to_file("report.docx", "report.md")
```

## With Options

```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, LoadOptions

load_opts = LoadOptions()
load_opts.password = "secret"

options = ConvertOptions()
options.heading_level_offset = 1
options.include_front_matter = True

md = MarkdownConverter.to_markdown("document.docx",
    load_options=load_opts, convert_options=options)
```

## Instance API

```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, SkipImagesStrategy

with MarkdownConverter("document.docx") as converter:
    options = ConvertOptions()
    options.image_export_strategy = SkipImagesStrategy()
    result = converter.convert(convert_options=options)
    if result.is_success:
        print(result.content)
```

## Image Strategies

```python
from groupdocs.markdown import ConvertOptions, SkipImagesStrategy
from groupdocs.markdown import ExportImagesToFileSystemStrategy, ExportImagesAsBase64Strategy

options = ConvertOptions()
options.image_export_strategy = SkipImagesStrategy()                        # skip
options.image_export_strategy = ExportImagesToFileSystemStrategy("./images") # to dir
options.image_export_strategy = ExportImagesAsBase64Strategy()               # embed
```

## Custom Image Handler (Callback)

```python
from groupdocs.markdown import MarkdownConverter, ConvertOptions, CustomImagesStrategy

counter = [0]
def rename_handler(call_info):
    ctx = call_info["context"]  # keys: ImageFileName, ShapeType, OutputDirectory
    counter[0] += 1
    return {"output_image_file_name": f"fig-{counter[0]}.png"}

options = ConvertOptions()
options.image_export_strategy = CustomImagesStrategy("./images", rename_handler)
MarkdownConverter.to_file("document.docx", "output.md", convert_options=options)
```

## URI Rewriting (Callback)

```python
from groupdocs.markdown import (MarkdownConverter, ConvertOptions,
    ExportImagesToFileSystemStrategy, CustomUriExportStrategy)

def cdn_handler(call_info):
    name = call_info["context"]["ResourceFileName"]  # keys: ResourceFileName, ResourceFileUri
    return {"resource_file_uri": f"https://cdn.example.com/{name}"}

options = ConvertOptions()
options.image_export_strategy = ExportImagesToFileSystemStrategy("./images")
options.uri_export_strategy = CustomUriExportStrategy(cdn_handler)
MarkdownConverter.to_file("document.docx", "output.md", convert_options=options)
```

## Get Document Info

```python
info = MarkdownConverter.get_info("document.docx")
print(f"Format: {info.file_format}, Pages: {info.page_count}")
```

## Convert from Markdown

```python
from groupdocs.markdown import MarkdownConverter
MarkdownConverter.from_markdown("input.md", "output.pdf")
MarkdownConverter.from_markdown("input.md", "output.docx")
```

## Licensing

```python
from groupdocs.markdown import License

# From file
License().set_license("path/to/license.lic")

# From stream
with open("license.lic", "rb") as f:
    License().set_license(f)
```

Or auto-apply: `export GROUPDOCS_LIC_PATH="path/to/license.lic"`

**Evaluation**: works without a license with limitations (page/document count cap, evaluation mark in output). Get a free 30-day full license: https://purchase.groupdocs.com/temporary-license

## API Reference

### MarkdownConverter

| Method | Returns | Description |
|---|---|---|
| `__init__(source_path)` | | Constructor |
| `convert_async()` | `Task[ConvertResult]` |  |
| `get_document_info_async()` | `Task[DocumentInfo]` |  |
| `convert()` | `ConvertResult` |  |
| `get_document_info()` | `DocumentInfo` |  |
| `to_markdown_async(source_path)` | `Task[str]` | static |
| `to_file_async(source_path, output_path, convert_options)` | `Task` | static |
| `get_info_async(source_path, load_options)` | `Task[DocumentInfo]` | static |
| `to_markdown(source_path)` | `str` | static |
| `to_file(source_path, output_path)` | `None` | static |
| `get_info(source_path)` | `DocumentInfo` | static |
| `get_supported_formats()` | `IReadOnlyList[FileFormat]` | static |
| `from_markdown(markdown_path, output_path)` | `None` | static |
| `from_markdown_string(markdown_content, output_path, options)` | `None` | static |

### ConvertOptions

| Property | Type | Writable |
|---|---|---|
| `image_export_strategy` | `IImageExportStrategy` | yes |
| `uri_export_strategy` | `IUriExportStrategy` | yes |
| `page_numbers` | `Int32[]` | yes |
| `heading_level_offset` | `int` | yes |
| `include_front_matter` | `bool` | yes |
| `flavor` | `MarkdownFlavor` | yes |
| `max_columns` | `int` | yes |
| `max_rows` | `int` | yes |
| `sheet_separator` | `str` | yes |
| `include_hidden_sheets` | `bool` | yes |

### LoadOptions

| Property | Type | Writable |
|---|---|---|
| `password` | `str` | yes |
| `file_format` | `FileFormat` | read-only |

### ExportOptions

| Property | Type | Writable |
|---|---|---|
| `format` | `FileFormat` | yes |

### ConvertResult

| Property | Type | Writable |
|---|---|---|
| `is_success` | `bool` | read-only |
| `error_message` | `str` | read-only |
| `content` | `str` | read-only |
| `exception` | `Exception` | read-only |
| `warnings` | `IReadOnlyList[str]` | read-only |

### DocumentInfo

| Property | Type | Writable |
|---|---|---|
| `file_format` | `FileFormat` | read-only |
| `page_count` | `int` | read-only |
| `title` | `str` | read-only |
| `author` | `str` | read-only |
| `is_encrypted` | `bool` | read-only |

### Callback Response Keys

| Handler | Key | Effect |
|---|---|---|
| `CustomImagesStrategy` | `output_image_file_name` | Override file name |
| `CustomImagesStrategy` | `replacement_image_path` | Replace image content |
| `CustomUriExportStrategy` | `resource_file_uri` | Override URI in output |

Return `None` to keep defaults. Exceptions preserve original Python type.

## Key Patterns

- **Properties**: use `snake_case` -- auto-mapped to .NET `PascalCase`
- **Context managers**: `with MarkdownConverter(...) as x:` ensures resources are released
- **Streams**: pass `open("file", "rb")` or `io.BytesIO(data)` where .NET expects Stream
- **Enums**: case-insensitive, lazy-loaded (e.g., `FileType.DOCX`)
- **Callbacks**: pass Python functions directly where .NET expects handler interfaces

## Troubleshooting

**`DllNotFoundException: libSkiaSharp`** -- stale system copy conflicts with bundled version. Rename it: `sudo mv /usr/local/lib/libSkiaSharp.dylib /usr/local/lib/libSkiaSharp.dylib.bak`

**`DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` errors** -- do NOT set this. Install ICU: `sudo apt install libicu-dev`

**`TypeLoadException`** -- reinstall: `pip install --force-reinstall groupdocs-markdown-net`

**Still stuck?** Post your question at https://forum.groupdocs.com/c/markdown/ -- the development team responds directly.
````

## See also

- [Convert documents for RAG pipelines]({{< ref "markdown/python-net/developer-guide/use-cases/convert-for-rag" >}})
- [API Reference](https://reference.groupdocs.com/markdown/python-net)
