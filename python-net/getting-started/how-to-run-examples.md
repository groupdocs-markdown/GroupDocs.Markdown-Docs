---
id: how-to-run-examples
url: markdown/python-net/how-to-run-examples
title: How to run examples
weight: 7
description: "This article describes how to run GroupDocs.Markdown for Python via .NET code examples."
keywords: markdown, python, run examples, venv, pip
productName: GroupDocs.Markdown for Python via .NET
hideChildren: False
toc: true
---

We offer multiple ways to run GroupDocs.Markdown for Python via .NET code examples — build a project from scratch, run the examples repository from GitHub, or use Docker.

## Build a project from scratch

Create a new Python project, install the package from PyPI, and run a minimal conversion script.

1. Make sure you have [Python 3.5 or later](https://www.python.org/downloads/) installed (64-bit).
2. Create a directory for your project:

   ```bash
   mkdir my-markdown-app
   cd my-markdown-app
   ```

3. Create and activate a virtual environment:

   ```bash
   python -m venv .venv
   # On Windows
   .venv\Scripts\activate
   # On Linux/macOS
   source .venv/bin/activate
   ```

4. Install the GroupDocs.Markdown package:

   ```bash
   pip install groupdocs-markdown-net
   ```

5. Create `convert.py` with the following code:

{{< tabs "run-example-basic" >}}
{{< tab "convert.py" >}}  
```python
from groupdocs.markdown import MarkdownConverter

def convert():
    """Convert a document to Markdown using the instance API."""
    with MarkdownConverter("business-plan.docx") as converter:
        converter.convert("run-example-basic.md")

if __name__ == "__main__":
    convert()
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is sample file used in this example. Click [here](/markdown/python-net/_sample_files/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "run-example-basic.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/python-net/_output_files/getting-started/how-to-run-examples/convert/run-example-basic.md)
{{< /tab >}}
{{< /tabs >}}

6. Replace the `document_path` value with the actual path to the document you want to convert.
7. Run the script:

   ```bash
   python convert.py
   ```

8. The converted Markdown file `converted.md` will appear in the project directory.

## Run examples from GitHub

A complete set of runnable examples is published in our [GitHub repository](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-Python-via-.NET). You can either clone the repository or download it as a ZIP archive.

1. Clone the repository:

   ```bash
   git clone https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-Python-via-.NET.git
   cd GroupDocs.Markdown-for-Python-via-.NET/Examples
   ```

2. Create a virtual environment and install the dependencies:

   ```bash
   python -m venv .venv
   source .venv/bin/activate        # or .venv\Scripts\activate on Windows
   pip install -r requirements.txt
   ```

3. (Optional) Place your GroupDocs license file named `GroupDocs.Markdown.lic` in the `Examples` directory to avoid evaluation watermarks.

4. Run all examples at once:

   ```bash
   python run_all_examples.py
   ```

5. Or run an individual example by executing its `.py` file directly. Each example is a small, self-contained script that converts a sample document.

## Run examples in Docker

The repository ships with a `Dockerfile` so you can run the examples in an isolated Linux environment without installing Python locally:

```bash
docker build -t groupdocs-markdown-python .
docker run --rm -v "$(pwd)/output:/app/output" groupdocs-markdown-python
```

## IDE setup

Any Python-capable IDE works with GroupDocs.Markdown for Python via .NET:

- **Visual Studio Code** with the [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python) — auto-detects the `.venv` interpreter and provides IntelliSense from the installed package.
- **PyCharm** — configure the project interpreter to point at your virtual environment, then run any example as a standard Python file.

## Contribute

If you like to add or improve an example, we encourage you to contribute to the project. All examples in the repository are open source and can be freely used in your own applications.
To contribute, fork the repository, edit the code, and open a pull request. We will review the changes and include them if they are useful.
