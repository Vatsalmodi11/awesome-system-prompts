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

You can use these system prompts with any API (like OpenAI, Anthropic, Gemini, etc.) or local inference tool (like Ollama) to replicate the behavior of these AI assistants.

### Method 1: API (Using cURL or Scripts)
You can directly pass the contents of a `Prompt.txt` file into the `system` role of an API request. Here's an example using OpenAI's API:

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
