# 🌟 Awesome System Prompts

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#-contributing)

A meticulously curated collection of **System Prompts, Custom Instructions, and Tool Configurations** extracted from the world's most advanced AI assistants and autonomous agents. By studying or adopting these prompts, you can unlock better reasoning, stricter adherence to constraints, and more powerful AI behaviors in your own applications.

---

## 🗂️ Prompt Directory

Explore our extensive vault of AI instructions, structured by their core application.

| Category | Providers & Tools | Description |
| :--- | :--- | :--- |
| **🧠 Foundation Models** | <ul><li>[Anthropic](./prompts/Anthropic/)</li><li>[OpenAI](./prompts/OpenAI/)</li><li>[Google](./prompts/Google/)</li><li>[xAI](./prompts/xAI/)</li></ul> | Core system guidelines dictating the persona, safety rules, and deep reasoning loops of flagship models (e.g., Claude, GPT-4o, Gemini). |
| **💻 Code Assistants** | <ul><li>[Cursor](./prompts/Cursor%20Prompts/)</li><li>[Windsurf](./prompts/Windsurf/)</li><li>[Trae](./prompts/Trae/)</li><li>[VSCode Agent](./prompts/VSCode%20Agent/)</li><li>[Xcode](./prompts/Xcode/)</li></ul> | IDE-integrated prompts engineered for precision coding, strict file-editing limits, and codebase exploration rules. |
| **🕵️ Application Agents** | <ul><li>[Devin AI](./prompts/Devin%20AI/)</li><li>[Manus](./prompts/Manus%20Agent%20Tools%20&%20Prompt/)</li><li>[Perplexity](./prompts/Perplexity/)</li><li>[Notion AI](./prompts/NotionAi/)</li></ul> | Multi-step agent loops, browser searching constraints, and complex memory-management tool definitions. |
| **🌐 Open Source** | <ul><li>[Cline](./prompts/Open%20Source%20prompts/Cline/)</li><li>[RooCode](./prompts/Open%20Source%20prompts/RooCode/)</li><li>[Bolt](./prompts/Open%20Source%20prompts/Bolt/)</li></ul> | Open-source ecosystem implementations of advanced coding loops and agent architectures. |

---

## 🎯 Pro-Tip: Supercharge Your Own Projects

Want to get the absolute **best, most accurate results** when generating code? You can combine these world-class system prompts with your *existing* project context to significantly boost output quality.

Instead of writing basic questions, use this **Context-Driven AI Formula**:

### 1. The Strategy
* **Adopt a Persona:** Copy an IDE prompt (like `prompts/Cursor Prompts/Agent Prompt.txt`). These prompts are heavily engineered to prevent bugs and enforce best practices.
* **Provide Your Architecture:** Feed the AI your existing file structures so it understands your environment. *(Hint: Use the included **Graphify** tool below to generate a map of your codebase!)*

### 2. Permanent Integration into your IDE
You can indefinitely bind these expert coding rules to your project locally so the AI always writes perfectly matched code:
- **For Cursor:** Create a `.cursorrules` file in your root folder and paste your favorite system prompt inside.
- **For Windsurf / Claude Code:** Paste the prompt rules into a `.windsurfrules` or `CLAUDE.md` file.
- **For GitHub Copilot:** Save the prompt into `.github/copilot-instructions.md`.

### 3. The Perfect Mega-Prompt Structure
If using a web chat (like ChatGPT or Claude.ai), structure your message like this:
```text
[SYSTEM RULES]
<Paste a professional prompt from this repository here (e.g., Claude Sonnet 4.6.txt)>

[MY PROJECT CONTEXT]
<Paste your codebase file tree or your Graphify GRAPH_REPORT.md here>

[MY TASK]
Implement completely new Authentication middleware. Ensure you follow the exact modular format found in my existing project files!
```
**Result:** The AI adopts a senior-developer persona, perfectly respects your unique architecture, and writes seamless, highly accurate project-specific code!

---

## 🛠️ Simple Usage (No Coding Required)

Just browsing? You don't need coding skills to use these! 
1. Navigate into any folder (e.g., `prompts/OpenAI`).
2. Open a `.txt` or `.md` file.
3. Select and copy all the text.
4. Paste it into the "System Instructions" or "Custom Instructions" box in ChatGPT, Claude, or Google AI Studio. 

---

## 💻 Developer API Usage

You can programmatically inject these prompts into API requests (OpenAI, Anthropic, Gemini) or local inference tools (like Ollama).

#### cURL Example
```bash
export OPENAI_API_KEY="your-api-key"
SYSTEM_PROMPT=$(cat "prompts/Cursor Prompts/Chat Prompt.txt")

curl https://api.openai.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -d '{
    "model": "gpt-4o",
    "messages": [
      {"role": "system", "content": "'"${SYSTEM_PROMPT//\"/\\\"}"'"},
      {"role": "user", "content": "Help me debug this."}
    ]
  }'
```

---

## 🕸️ Using Graphify (AST Knowledge Graph)

We've included `graphify` directly in this repository. Graphify automatically maps out your codebase (AST), linking files, objects, functions, and their dependencies. This is perfect for feeding exact project context to the AI prompts above!

### Setup & Installation (Support for JS/TS/Python etc.)
Graphify is a Python-based tool that uses `tree-sitter` to parse your project's code. You need to install the dependencies and the specific language parsers (like JavaScript) before running it:

```bash
# Navigate to the tool's folder
cd "graphify"

# 1. Create a virtual environment and activate it
python3 -m venv venv
source venv/bin/activate

# 2. Install base dependencies
pip install networkx pygments jinja2 typing_extensions anthropic litellm

# 3. Install Tree-Sitter and Language Parsers (e.g., for JS and TS)
pip install tree-sitter tree-sitter-javascript tree-sitter-typescript tree-sitter-python
```

### Usage Command
Once installed, you can easily run graphify against any target directory (like a React or Node.js project):
```bash
# Run Graphify against a target directory
python3 -m graphify ../my-js-app
```
Graphify will output a local `graphify-out/GRAPH_REPORT.md` detecting your clusters and core files. Feed this output directly to your AI alongside an Awesome System Prompt for legendary precision.

----

## 🤝 Contributing

Contributions are heavily encouraged! If you've discovered, extracted, or leaked a system prompt for a new tool, structure it in its respective folder and submit a pull request.
