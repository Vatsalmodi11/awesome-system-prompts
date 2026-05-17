# Graphify Full Setup Guide (macOS + Windows + VS Code + Gemini API)

This guide shows how to fully set up Graphify for any project using:

- macOS
- Windows
- VS Code
- Gemini Free API
- AI-assisted coding workflows

Example project name:

```bash
your-project-name
```

---

# What is Graphify?

Graphify builds a knowledge graph of your codebase.

It can:

- Analyze project architecture
- Map frontend ↔ backend relationships
- Detect imports, functions, APIs, dependencies
- Generate interactive visualizations
- Create AI-queryable project memory
- Help AI assistants understand your repository better

---

# Requirements

Before starting, install:

- Python 3.10+
- VS Code
- Git

---

# Step 1 — Install Python

## macOS

Download Python:

https://www.python.org/downloads/macos/

Verify installation:

```bash
python3 --version
```

---

## Windows

Download Python:

https://www.python.org/downloads/windows/

IMPORTANT:

During installation, enable:

```text
Add Python to PATH
```

Verify installation:

```powershell
python --version
```

---

# Step 2 — Install VS Code

Download VS Code:

https://code.visualstudio.com/

Recommended extensions:

- Python
- ESLint
- Prettier
- GitHub Copilot (optional)

---

# Step 3 — Install UV (Recommended)

UV is a fast Python package manager.

---

## macOS

Install UV:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Load environment:

```bash
source $HOME/.local/bin/env
```

Verify installation:

```bash
uv --version
```

Permanent fix:

```bash
echo 'source $HOME/.local/bin/env' >> ~/.zshrc
source ~/.zshrc
```

---

## Windows (PowerShell)

Install UV:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Restart terminal.

Verify installation:

```powershell
uv --version
```

---

# Step 4 — Install Graphify

Install Graphify globally:

```bash
uv tool install graphifyy
```

Verify installation:

```bash
graphify --help
```

---

# Step 5 — Install OpenAI Dependency

Some Graphify semantic extraction features require the OpenAI package even when using Gemini backend.

Install:

```bash
pip install openai
```

OR:

```bash
uv pip install openai
```

---

# Step 6 — Get Free Gemini API Key

Open:

https://aistudio.google.com/app/apikey

Create a free API key.

---

# Step 7 — Configure Gemini API Key

---

## macOS

Replace:

```text
YOUR_GEMINI_API_KEY
```

with your actual Gemini API key.

Run:

```bash
export GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
```

Permanent save:

```bash
echo 'export GEMINI_API_KEY="YOUR_GEMINI_API_KEY"' >> ~/.zshrc
source ~/.zshrc
```

Verify:

```bash
echo $GEMINI_API_KEY
```

---

## Windows (PowerShell)

Run:

```powershell
setx GEMINI_API_KEY "YOUR_GEMINI_API_KEY"
```

Restart terminal.

Verify:

```powershell
echo $env:GEMINI_API_KEY
```

---

# Step 8 — Open Your Project

Example project:

```bash
your-project-name
```

Open the project in VS Code.

Then open terminal:

```text
Terminal → New Terminal
```

Move into project:

```bash
cd /path/to/your-project-name
```

Verify:

```bash
ls
```

You should see your project files.

---

# Step 9 — Build Your First Knowledge Graph

IMPORTANT:

Modern Graphify versions use:

```bash
graphify extract .
```

NOT:

```bash
graphify .
```

Run:

```bash
graphify extract . --backend gemini
```

This will:

- Scan your project
- Analyze code structure
- Extract semantic relationships
- Build architecture graph
- Generate graph data

---

# Step 10 — Generated Output

After extraction, Graphify creates:

```text
graphify-out/
```

Inside:

```text
graph.json
.graphify_analysis.json
```

Depending on your Graphify version, additional files may appear later.

---

# Step 11 — Generate Interactive Tree Visualization

Generate visualization:

```bash
graphify tree
```

This creates:

```text
graphify-out/GRAPH_TREE.html
```

---

# Step 12 — Open Visualization

## macOS

```bash
open graphify-out/GRAPH_TREE.html
```

---

## Windows

```powershell
start graphify-out/GRAPH_TREE.html
```

---

# Step 13 — Generate Call Flow Visualization

Run:

```bash
graphify export callflow-html
```

Check generated files:

```bash
ls graphify-out
```

Open generated file.

---

## macOS

```bash
open graphify-out/callflow.html
```

---

## Windows

```powershell
start graphify-out/callflow.html
```

---

# Step 14 — Install VS Code Integration

Install Graphify VS Code integration:

```bash
graphify vscode install
```

Restart VS Code completely.

---

# Step 15 — Query Your Project

Graphify supports natural-language architecture queries.

Examples:

```bash
graphify query "How does authentication work?"
```

```bash
graphify query "Where are API routes defined?"
```

```bash
graphify query "How does frontend communicate with backend?"
```

```bash
graphify query "Which files use WebSockets?"
```

---

# Step 16 — Watch Mode (Recommended)

Automatically update graph during development:

```bash
graphify watch .
```

Stop watch mode:

```text
CTRL + C
```

---

# Step 17 — Fast Graph Updates

After code changes:

```bash
graphify update .
```

---

# Recommended Project Structure

Example:

```text
your-project-name/
│
├── client/
├── server/
├── docs/
├── package.json
├── README.md
│
└── graphify-out/
```

Always run Graphify from the root project folder.

---

# Important Notes

## 1. graphify . may fail

Newer Graphify versions use:

```bash
graphify extract .
```

instead.

---

## 2. graph.html may not exist

Modern versions generate:

```text
GRAPH_TREE.html
```

instead of:

```text
graph.html
```

---

## 3. HTML files are NOT executable

Wrong:

```bash
graphify-out/GRAPH_TREE.html
```

Correct:

### macOS

```bash
open graphify-out/GRAPH_TREE.html
```

### Windows

```powershell
start graphify-out/GRAPH_TREE.html
```

---

## 4. Gemini API is NOT fully unlimited

Large repositories may still hit:

- rate limits
- token limits

For huge projects:
- use smaller chunks
- or switch to OpenAI / Claude / Ollama

---

# Useful Commands

## Build graph

```bash
graphify extract . --backend gemini
```

---

## Update graph

```bash
graphify update .
```

---

## Watch mode

```bash
graphify watch .
```

---

## Generate tree

```bash
graphify tree
```

---

## Query graph

```bash
graphify query "How does auth work?"
```

---

## VS Code integration

```bash
graphify vscode install
```

---

# Final Workflow Recommendation

Recommended development workflow:

## First time setup

```bash
graphify extract . --backend gemini
graphify tree
```

---

## During development

```bash
graphify watch .
```

---

## Before major refactors

```bash
graphify update .
graphify tree
```

---

# Final Output Files

| File | Purpose |
|---|---|
| graph.json | Full project knowledge graph |
| GRAPH_TREE.html | Interactive architecture tree |
| callflow.html | Function/call-flow visualization |
| .graphify_analysis.json | Semantic analysis metadata |

---

# Done

Your project is now AI-queryable and architecture-aware using Graphify + Gemini + VS Code.
