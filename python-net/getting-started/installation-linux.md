---
id: installation-linux
url: markdown/python-net/installation-linux
title: Install GroupDocs.Markdown for Python via .NET on Linux
linkTitle: Linux Installation
weight: 5
description: "How to install and run GroupDocs.Markdown for Python via .NET on Linux, macOS, and in Docker containers."
keywords: GroupDocs.Markdown, Linux, Docker, Ubuntu, Alpine, Python, macOS
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: True
---

This article explains how to install and run **GroupDocs.Markdown for Python via .NET** on Linux and macOS. The package bundles the .NET runtime — you do **not** need to install .NET separately. No GDI+, fonts, or other system libraries are required for Markdown conversion.

## Prerequisites

The only system-level requirement is **ICU** (International Components for Unicode), which is used by the bundled .NET runtime for text processing.

Most standard Linux distributions and non-slim Docker images already include ICU. You only need to install it on minimal or slim systems:

```bash
# Debian / Ubuntu
apt-get update && apt-get install -y libicu-dev

# Fedora / RHEL / CentOS
dnf install -y libicu

# Alpine
apk add icu-libs
```

On **macOS**, ICU is included in the OS — no extra packages are needed.

{{< alert style="warning" >}}
Do **not** set the `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=1` environment variable. GroupDocs.Markdown requires ICU for proper text processing.
{{< /alert >}}

## Install the Package

```bash
pip install groupdocs-markdown-net
```

## Verify Installation

```python
from groupdocs.markdown import MarkdownConverter

for fmt in MarkdownConverter.get_supported_formats():
    print(fmt)
```

## Docker

### Non-slim image (recommended)

Non-slim Python images (`python:3.13`) include ICU and all necessary system libraries. No additional packages are needed — just install the pip package:

```dockerfile
FROM python:3.13

RUN pip install --no-cache-dir groupdocs-markdown-net

WORKDIR /app
COPY . .
CMD ["python", "convert.py"]
```

### Slim image

Slim Python images (`python:3.13-slim`) do not include ICU. Add it as the only extra dependency:

```dockerfile
FROM python:3.13-slim

RUN apt-get update -qq \
    && apt-get install -y --no-install-recommends libicu-dev \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir groupdocs-markdown-net

WORKDIR /app
COPY . .
CMD ["python", "convert.py"]
```

### Slim vs non-slim comparison

| | `python:3.13` | `python:3.13-slim` |
|---|---|---|
| **Image size** | ~1 GB | ~150 MB |
| **ICU included** | Yes | No (add `libicu-dev`) |
| **Extra apt packages** | None needed | `libicu-dev` only |
| **All formats work** | Yes | Yes (with ICU) |

### Build and Run

```bash
docker build -t markdown-demo .
docker run --rm -v $(pwd)/files:/app/files markdown-demo
```

## Troubleshooting

| Problem | Cause | Fix |
|---|---|---|
| `Couldn't find a valid ICU package` | ICU libraries missing | `apt-get install -y libicu-dev` or use a non-slim Docker image |
| `DllNotFoundException: libSkiaSharp` | Stale system SkiaSharp conflicts with bundled version | Rename or remove `/usr/lib/libSkiaSharp.so` |
| `TypeLoadException` on document operations | Corrupt or incomplete install | `pip install --force-reinstall groupdocs-markdown-net` |

## Supported Distributions

GroupDocs.Markdown for Python via .NET works on any Linux distribution that supports Python 3.5+, including:

- Ubuntu 20.04+
- Debian 11+
- CentOS 8+, RHEL 8+
- Fedora 36+
- Alpine 3.16+
- Amazon Linux 2023
