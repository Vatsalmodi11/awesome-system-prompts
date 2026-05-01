# All AI Prompt File (System Prompts and Models)

A comprehensive collection of system prompts, custom instructions, and tool configurations utilized by various state-of-the-art AI assistants and agents. 

## 📂 Contents

This repository includes prompts and tool specifications from prominent AI tools, organized by provider and application:

- **Anthropic & Claude:** Claude Code, Claude for Chrome, Sonnet models
- **Code Assistants & IDEs:** Cursor, Windsurf, Trae, CodeBuddy, VSCode Agent, Replit, Augment Code, Xcode
- **Autonomous Agents & Search:** Devin AI, Manus Agent, Notion AI, Perplexity, Comet Assistant
- **Open Source Prompts:** Bolt, Cline, Codex CLI, RooCode

## 🚀 Purpose & Usage

Explore the folders to learn how different AI applications structure their system prompts, agent loops, reasoning constraints, and tool definitions. 

- **`Prompt.txt` / `.md` files**: The core system prompts instructing the AI's behavior and constraints.
- **`.json` / `.yaml` files**: Typical function schemas, agent tool configurations, and API integrations.

## 🛠️ How to Use These Prompts

### 🟢 The Easiest Way (No Coding Required)

If you just want to see how these prompts work, you don't need any coding skills! Just follow these steps:

1. **Pick a tool you like:** Navigate into any folder (for example, `Cursor Prompts`).
2. **Open the prompt file:** Click on the `Chat Prompt.txt` or `Agent Prompt.txt` file.
3. **Copy the text:** Select all the text inside the file and copy it to your clipboard.
4. **Paste it into your favorite AI:**
   - Go to **ChatGPT** (under "Custom Instructions"), **Claude** (under "Projects" or "System Instructions"), or any AI Playground (like **Google AI Studio**).
   - Paste the copied text into the "System Prompt" or "Instructions" box and save.

That's it! When you start chatting, the AI will now act like the tool you copied the prompt from.

---

### 💻 For Developers (Using APIs or Custom Scripts)

You can programmatically use these system prompts with any API (like OpenAI, Anthropic, Gemini) or local inference tool (like Ollama).

#### Using an API (cURL Example)
You can directly read a `Prompt.txt` file and insert it into the `system` role of an API request:

```bash
# Set your API key
export OPENAI_API_KEY="your-api-key"

# Read the prompt into a variable, then call the API
SYSTEM_PROMPT=$(cat "Cursor Prompts/Chat Prompt.txt")

curl https://api.openai.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -d '{
    "model": "gpt-4o",
    "messages": [
      {
        "role": "system",
        "content": "'"${SYSTEM_PROMPT//\"/\\\"}"'"
      },
      {
        "role": "user",
        "content": "Hello, how can you help me?"
      }
    ]
  }'
```

### Method 2: AI CLI Tools
If you use CLI tools like [fabric](https://github.com/danielmiessler/fabric) or [aichat](https://github.com/sigoden/aichat), you can pipe the prompt file contents into your command:

```bash
# Using aichat to run a prompt as context
cat "Devin AI/Prompt.txt" | aichat "Write a Python script to scrape a website."
```

### Method 3: Simple Copy-Paste
You can simply open any `Prompt.txt` file (e.g., `Anthropic/Claude Sonnet 4.6.txt`), copy all of its text, and paste it into the "System Instructions" or "Custom Instructions" section of ChatGPT, Claude web interfaces, or your favorite AI playground (like OpenAI Playground or Google AI Studio).

## 🤝 Contributing

Contributions are welcome! If you've discovered or extracted a system prompt for a new tool, structure it in its respective folder and submit a pull request.

---

## 🕸️ Using Graphify (AST-based knowledge graph for code)

Graphify is a tool included in the `graphify` folder to map out your codebase structure (AST) automatically! It creates a graph of files, objects, functions, and their dependencies to help agents or you quickly navigate large AI prompt repositories or software projects.

### 🛠️ Usage Command:
To run graphify to analyze a repository or a specific folder, you simply use the Python CLI module inside it.

```bash
# Navigate to the tool's folder
cd "graphify"

# Run Graphify against a target directory (e.g. your prompt folders)
python -m graphify ../prompts/Anthropic
```

Graphify will parse the files, build a structured map, and output a local knowledge graph directory called `graphify-out/`.

### 📊 What does the Graph look like?

When graphify finishes, it creates an easily readable `GRAPH_REPORT.md` (and a JSON graph index) that looks like this abstract example:

```markdown
# Codebase Graph Report
**Directory analyzed:** ../Anthropic

### 👑 God Nodes (Highly Connected/Important Files)
* `claude-sonnet-4.6.md` - Connected to 12 shared reasoning frameworks.
* `claude-code.md` - Foundational prompt affecting 6 other tools.

### 🏘️ Communities (Clusters of related Prompts)
**Cluster 1: Claude Desktop**
* `claude-desktop-code.md` -> references Desktop API limits
* `claude-in-chrome.md` -> shares browser reading functions with Desktop

**Cluster 2: Microsoft Office Integration**
* `claude-for-word.md` -> uses Word-specific COM tool formats
* `claude-for-excel.md` -> uses Data Analysis function formats
```

This visualization lets agents see which prompts share dependencies or common rules at a glance!
