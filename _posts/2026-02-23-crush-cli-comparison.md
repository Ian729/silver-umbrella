---
layout: post
title: "AI in Your Terminal: A Look at Crush CLI and its Peers"
date: 2026-02-23 18:31:00 +0800
categories: [AI, CLI, Tools, CrushCLI, OpenCode]
---

The command line is the developer's most powerful environment, and it's getting a major upgrade with AI. Tools are emerging that bring the power of large language models (LLMs) directly into your terminal, saving you from the context switch of a browser window. One of the most interesting players in this space is **Crush CLI**.

## What is Crush CLI?

Crush CLI (formerly OpenCode AI) is an open-source terminal interface that acts as your AI coding assistant. It's built with Go and designed to be a flexible, session-based tool that integrates with your existing workflow.

One of its standout features is **multi-model support**. You're not locked into a single provider. You can switch between different LLMs (like models from OpenAI, Anthropic, or others) in the middle of a session while keeping your conversation context intact.

### Installation & Usage

Getting started is easy. If you're on macOS, you can use Homebrew:
```bash
brew install charmbracelet/tap/crush
```

For other platforms, it's available via `npm`, `winget`, `scoop`, and as pre-compiled binaries.

Once installed, simply run `crush`. On the first run, it will guide you through setting up your API keys. After that, you can start asking questions, sending code snippets, and getting AI assistance without leaving your terminal.

## How Does it Compare?

Crush CLI isn't alone. Here's a look at the landscape:

- **Gemini CLI:** Google's own open-source agent. Like Crush, it excels at editing large codebases and generating applications. It brings the power of the Gemini model family to the terminal.
- **Amazon Q Developer CLI:** Heavily integrated with the AWS ecosystem, this tool is great for translating natural language into shell commands and automating cloud operations.
- **NovaKit CLI:** A strong competitor, particularly in the JavaScript/TypeScript world. It focuses on semantic code search and reviewing batch changes. While Crush has broader platform support (including native Windows and BSD), NovaKit has powerful features for its target ecosystem.

## Advantages and Disadvantages

- **Crush's Strengths:** Its biggest advantages are flexibility (multi-model, cross-platform) and its session-based context management. The integration with Language Server Protocols (LSP) also allows it to have a deeper understanding of your code, much like a modern IDE.

- **Crush's Weaknesses:** As a general-purpose tool, it may not have the deep, ecosystem-specific integrations that a tool like Amazon Q has for AWS.

## Conclusion

Tools like Crush CLI represent the future of developer workflows. By bringing AI assistance directly to the command line, they reduce friction and allow developers to stay in the flow. While there are many options, Crush's focus on flexibility and a solid terminal user experience makes it a compelling choice for any developer looking to boost their productivity with AI.

---
*Silver Umbrella - Technical Learnings*
