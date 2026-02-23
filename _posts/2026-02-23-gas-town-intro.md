---
layout: post
title: "Gas Town: The Engine for AI Agent Coordination"
date: 2026-02-23 18:31:00 +0800
categories: [AI, CLI, Agents, Gastown]
---

If you've ever felt that managing a single AI agent is like herding a very clever cat, try managing a whole team of them. That's where **Gas Town (gt)** comes in. It's the infrastructure for a post-human developer experience, designed to orchestrate multiple AI agents working across distributed workspaces.

## What is Gas Town?

Gas Town is a workspace manager for "rigs"—multi-agent environments where agents (called "polecats") collaborate on a shared codebase. It doesn't just run an agent; it coordinates their spawning, work distribution, and communication. Think of it as a specialized "OS" for AI-native development.

## Core Concepts

- **Rigs:** These are the workspaces where the work happens. A rig is usually tied to a specific project or git repository.
- **Beads:** Every time an agent starts a session to work on a task, it's called a "bead." You can track, resume, or close these beads.
- **Polecats:** These are the persistent identities of the agents. While an individual session might be ephemeral, the polecat's identity and history can persist.
- **The Deacon:** A town-level watchdog that keeps everything running smoothly, ensuring agents don't get stuck and work flows through the system.

## How to Use Gas Town

Getting started is simple. Once you've initialized your workspace with `gt init`, the `gt` command becomes your control center.

### Dispatching Work
The most important command is `gt sling`. This is how you tell an agent to do something.
```bash
gt sling "Refactor the authentication module to use JWT"
```

### Communication
Agents in Gas Town can talk to each other and to you via a built-in messaging system.
- `gt mail inbox`: Check for messages from agents.
- `gt nudge`: Send a quick message to a specific worker.

### Monitoring Progress
Because Gas Town is built for distributed work, you need ways to see what's happening.
- `gt trail`: Shows recent agent activity.
- `gt feed`: Provides a real-time activity feed.
- `gt status`: Gives an overview of the entire "town."

## Why Use It?

The biggest advantage of Gas Town is **scale**. By decoupling the agent's identity from the local session and providing a robust communication layer, you can have dozens of agents working in parallel on different parts of a codebase without them stepping on each other's toes. 

It handles the "boring" parts of AI orchestration—state management, session persistence, and inter-process communication—so you can focus on the "what" instead of the "how."

---
*Silver Umbrella - Technical Learnings*
