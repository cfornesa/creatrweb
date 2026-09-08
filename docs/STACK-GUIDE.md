# Stack Guide — CreatrWeb

Which stack to use for which project. Cross-reference with
project-briefs.md for full project descriptions.

---

## Stack Definitions

| Stack | Key tools | Cost | PRC-clean |
|---|---|---|---|
| Free | Kilo Code + Opencode Zen + Groq + OpenRouter free | $0 | Yes |
| Open Source | Above + Opencode Go (GLM-5.1/MiniMax M2.7) | Opencode Go sub | No |
| OpenRouter | Kilo Code routed through OpenRouter free only | $0 | Yes |
| Kilo Code | Kilo Auto + Nemotron 3 Super + Free Models Router | $0 | Yes |
| Groq | Compound + Compound Mini only | $0 | Yes |
| Opencode Go | GLM-5.1 + MiniMax M2.7 + Zen free models | Opencode Go sub | No |
| Paid | Claude Code + Codex + Gemini CLI + Cursor + Vibe CLI + Copilot | Paid subs | Yes |
| Boycott App | Multi-tool orchestration, PRC-clean only | Mixed | Yes — required |

---

## Project-to-Stack Mapping

| # | Project | Stack | PRC restriction |
|---|---|---|---|
| 1 | Boycott & Ethical Consumption App | Boycott (multi-tool) | Enforced — no PRC models |
| 2 | Consolidated Open Source Showcase | Open Source | No restriction |
| 3 | Free Stack Showcase | Free | No restriction |
| 4 | OpenRouter Standalone | OpenRouter | No restriction |
| 5 | Kilo Code Standalone | Kilo Code | No restriction |
| 6 | Groq Standalone | Groq | No restriction |
| 7 | Opencode Go Standalone | Opencode Go | No restriction |
| 8 | Paid Stack Showcase | Paid | No restriction |
| 9 | Claude Code Standalone | Paid — Claude Code only | No restriction |
| 10 | Codex CLI Standalone | Paid — Codex only | No restriction |
| 11 | Gemini CLI Standalone | Paid — Gemini only | No restriction |
| 12 | Replit Standalone | Replit | No restriction |

---

## Stack Selection Rules

Use **Free** when:
- Zero cost is required
- Project is self-contained and does not involve sensitive political content
- Testing framework behavior on free models specifically

Use **Open Source** when:
- You need GLM-5.1's agentic multi-file strength
- Project content is not politically sensitive (no Xinjiang, Sudan, Congo, Palestine focus)
- Opencode Go quota is available

Use **OpenRouter** when:
- You want to isolate a single provider for testing
- You are comparing model outputs across the free OpenRouter catalog
- No Groq or Opencode dependency is acceptable

Use **Kilo Code** when:
- Testing Kilo Auto's internal routing intelligence specifically
- VS Code is the primary interface for the session
- No terminal-based agentic loops are needed

Use **Groq** when:
- Speed is the visible feature of the project
- Low-latency real-time inference is part of the UX
- Compound's multi-tool support (web search, code execution) adds value

Use **Opencode Go** when:
- GLM-5.1 or MiniMax M2.7 is the model being evaluated
- Project content is not politically sensitive
- Terminal-based agentic sessions are preferred over VS Code

Use **Paid** when:
- Multi-file IndieWeb spec work is required (Claude Code)
- Phase 1 scaffolding with strict question-before-build (Codex)
- Rapid UI iteration (Gemini CLI, Cursor)
- Autonomous bulk build phases (Vibe CLI)
- In-editor inline suggestions (Copilot)

Use **Boycott App multi-tool** when:
- The project is the boycott app specifically
- Every tool must be PRC-clean — no GLM, MiniMax, Kimi, MiMo, or Qwen models