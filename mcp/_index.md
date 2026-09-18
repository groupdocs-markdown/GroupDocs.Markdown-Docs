---
id: mcp
url: markdown/mcp
title: GroupDocs.Markdown MCP Server
weight: 6
description: "GroupDocs.Markdown MCP server lets AI agents like Claude, Cursor, and Copilot turn PDF, Word, Excel, EPUB and 20+ other formats into clean Markdown — locally on your machine."
keywords: document to markdown MCP server, PDF to markdown AI agent, RAG ingestion MCP, convert documents to markdown locally, Claude markdown conversion
productName: GroupDocs.Markdown MCP Server
hideChildren: True
toc: True
---

**GroupDocs.Markdown MCP server** turns documents into **clean, structured Markdown** — PDF, Word, Excel, EPUB, MOBI, CHM and 20+ more formats — **locally on your machine**. It is the ingestion step for knowledge bases, RAG pipelines, and static sites, without uploading a single file. 

Run it with one command. The Docker image is self-contained — the runtime and every native dependency the engine needs are inside it:

```bash
docker run --rm -i -v $(pwd)/documents:/data \
  ghcr.io/groupdocs-markdown/markdown-net-mcp:latest
```

With the .NET 10 SDK installed, the same server also runs without Docker:

```bash
dnx GroupDocs.Markdown.Mcp --yes
```

Both are the **.NET** build of the server and run on Windows, Linux, and macOS. Other platforms will each get their own launcher — see [Install for your platform](#install-for-your-platform).

Or use the [guided installer]({{< ref "markdown/mcp/getting-started/_index.md" >}}) to register the server in your AI client, verify the setup, and configure shared folders in one pass.

## What you can do

Three tools — a small surface, because the job is specific (full details in the [tools reference]({{< ref "markdown/mcp/tools-reference/_index.md" >}})):

* **[`convert_to_markdown`]({{< ref "markdown/mcp/tools-reference/convert-to-markdown.md" >}})** — the conversion, with control over images, page selection, dialect, and YAML front matter.
* **[`get_document_info`]({{< ref "markdown/mcp/tools-reference/get-document-info.md" >}})** — format, page count, title, author, encryption flag, without converting.
* **[`get_license_status`]({{< ref "markdown/mcp/tools-reference/get-license-status.md" >}})** — active licensing mode and metered consumption.

Ask in plain language — *"turn this handbook into Markdown for the knowledge base"* — and the agent does the rest.

## Install for your platform

Installation, prerequisites, and client configuration are platform-specific; the tools and licensing model below are the same everywhere.

| Platform | Status | Install and setup |
|---|---|---|
| .NET | **Available** | [MCP server for .NET]({{< ref "markdown/net/mcp/_index.md" >}}) |
| Java | Planned | [Tell us you need it](https://forum.groupdocs.com/c/markdown/) |
| Python | Planned | [Tell us you need it](https://forum.groupdocs.com/c/markdown/) |
| Node.js | Planned | [Tell us you need it](https://forum.groupdocs.com/c/markdown/) |

{{< alert style="warning" >}}
**Evaluation mode converts only the first three pages**, with a watermark on each — and the resulting Markdown looks entirely valid. A knowledge base built from unlicensed conversions is almost empty and does not appear broken. Check [`get_license_status`]({{< ref "markdown/mcp/tools-reference/get-license-status.md" >}}) before an ingestion run; see [Licensing]({{< ref "markdown/mcp/getting-started/licensing.md" >}}).
{{< /alert >}}

## The four options that make the output usable

| Option | Values | Why it matters |
|---|---|---|
| `images` | `base64` (default), `file`, none | Self-contained artefact vs. a repository or RAG index where data URIs pollute every chunk |
| `pages` | `1,3,5` | Convert a chapter instead of a 400-page book |
| `frontMatter` | `true` / `false` | YAML title, author, format, page count — for static sites and chunk metadata |
| `flavor` | `github` (default), `commonmark` | Match whatever will render or parse the result |

## Supported AI clients

| Client | How it connects |
|---|---|
| Claude Desktop | `claude_desktop_config.json` |
| Claude Code | `claude mcp add` CLI |
| VS Code / GitHub Copilot | user-level or workspace `mcp.json` |
| Visual Studio 2022 (17.14+) | `.mcp.json` in the solution root |
| Cursor | `~/.cursor/mcp.json` |
| Windsurf | `~/.codeium/windsurf/mcp_config.json` |
| Cline | Cline MCP settings |
| Codex CLI | `codex mcp add` CLI |
| JetBrains Rider | manual registration (Settings → AI Assistant → MCP) |

Exact config blocks for every client: [Register in AI clients]({{< ref "markdown/net/mcp/install-in-ai-clients.md" >}}).

## Delivery channels

| | Docker (recommended) | NuGet (`dnx`) |
|---|---|---|
| Prerequisites | Docker only | .NET 10 SDK (+ `libgdiplus` on Linux/macOS) |
| Native dependencies | bundled in the image | installed by you (or the setup script) |
| Package | `ghcr.io/groupdocs-markdown/markdown-net-mcp` | `GroupDocs.Markdown.Mcp` on NuGet |
| Architectures | linux/amd64 + linux/arm64 (Apple Silicon native) | any OS with .NET 10 |

## How it works

The server uses MCP's **local stdio transport**: your AI client starts the server as a child process and talks to it over standard input/output. No inbound ports, no external endpoints, no telemetry — the data path is *agent → local server → local filesystem*. Ingestion is exactly where documents usually leak: the corpus you are indexing is the corpus you cannot afford to upload. Details: [On-premise architecture]({{< ref "markdown/mcp/use-cases/on-premise-markdown-conversion.md" >}}).

## Markdown here, or in the Conversion server?

Both can produce Markdown. [GroupDocs.Conversion]({{< ref "conversion/mcp/_index.md" >}}) is the general converter across 100+ formats in both directions. **This** server is specialised: dialect selection, image strategy, page ranges, and front matter are first-class parameters. If Markdown is the destination and you care how it looks, this is the one; if you need DOCX → XLSX → PDF as well, use Conversion.

## Resources

* [Quick start]({{< ref "markdown/mcp/getting-started/_index.md" >}}) · [Use cases]({{< ref "markdown/mcp/use-cases/_index.md" >}}) · [Troubleshooting & FAQ]({{< ref "markdown/mcp/troubleshooting-faq.md" >}})
* GitHub: [server source](https://github.com/groupdocs-markdown/GroupDocs.Markdown.Mcp) · [installer](https://github.com/groupdocs/GroupDocs.Mcp.Installer) · [integration tests](https://github.com/groupdocs-markdown/GroupDocs.Markdown.Mcp.Tests)
* [NuGet package](https://www.nuget.org/packages/GroupDocs.Markdown.Mcp) · [Docker image](https://github.com/orgs/groupdocs-markdown/packages/container/package/markdown-net-mcp) · [MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=io.github.groupdocs-markdown/groupdocs-markdown-mcp)
* Questions: [Markdown forum](https://forum.groupdocs.com/c/markdown/)
