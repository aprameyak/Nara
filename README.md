# Nara

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white&style=for-the-badge)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white&style=for-the-badge)
![Anthropic](https://img.shields.io/badge/Claude_API-D97757?logo=anthropic&logoColor=white&style=for-the-badge)

## About

**Nara** is an autonomous red team CLI that orchestrates three AI agents to scan a codebase for vulnerabilities, plan an ordered attack chain, and execute exploits against an isolated Docker container — all from a single command. Built with **Python** and the **Claude API** (with support for Ollama and Featherless as backends), it streams live exploitation via noVNC so you can watch the attack unfold in a real desktop environment. Built for Bitcamp 2026.

## Features

- `pipeline` command runs the full scan → plan → exploit flow end-to-end from a local path or GitHub URL
- Scanner agent runs Semgrep and Bandit, then uses an LLM to deduplicate and prioritize findings
- Planner agent designs an ordered kill chain from scan results, ending in ransomware deployment
- Exploiter agent provisions a Docker container (Ubuntu 22.04 + XFCE desktop) and executes each step via `docker exec`, adapting on failure
- noVNC streams the desktop live at `localhost:6080` so exploitation is visually observable in the browser
- Ransomware payload encrypts files, drops a ransom note, hijacks the wallpaper, and generates a post-exploitation report
- Interactive REPL with conversational awareness — ask follow-up questions about MITRE tactics, exploit paths, and findings after the pipeline completes
- Swappable LLM backend: Claude, Ollama, or Featherless — configured via `.env` with no code changes

## Technology Stack

- **Language**: Python
- **CLI**: prompt_toolkit, Rich
- **LLM**: Claude API, Ollama, Featherless
- **Static Analysis**: Semgrep, Bandit
- **Containerization**: Docker (Ubuntu 22.04, XFCE, TigerVNC, noVNC)
