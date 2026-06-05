---
name: project-context-manager
description: Manage project context documents for Codex across sessions. Use when creating, reading, updating, compressing, or handing off project context with AGENTS.md and docs/codex files such as PROJECT_CONTEXT.md, HANDOFF.md, CURRENT_TASK.md, API_TODO.md, and TASK_LOG.md; also use when starting a new project conversation, preparing a new Codex session, or preserving interface/field/task knowledge between chat windows.
---

# Project Context Manager

Use this skill to keep project context portable across Codex sessions without copying long chat history. Prefer the project's own `AGENTS.md` rules whenever they conflict with this skill.

## Core Documents

Use this default document set when the project has no stronger convention:

- `AGENTS.md`: collaboration rules, hard boundaries, and required startup behavior.
- `docs/codex/PROJECT_CONTEXT.md`: stable project facts, architecture, long-lived business rules, important directories, and durable implementation status.
- `docs/codex/HANDOFF.md`: concise cross-session handoff for what the next conversation truly needs.
- `docs/codex/CURRENT_TASK.md`: only unfinished work that must continue in another session.
- `docs/codex/API_TODO.md`: uncertain APIs, fields, enums, payload conversions, response shapes, form backfill, and integration questions.
- `docs/codex/TASK_LOG.md`: stage-level history for traceability; do not log every small edit.

If a project already uses different names, follow the project convention and map these responsibilities to the existing files.

## Startup Workflow

When asked to continue a project, start a new session, or align context:

1. Read `AGENTS.md` first if it exists.
2. Read `PROJECT_CONTEXT.md`, `HANDOFF.md`, and `CURRENT_TASK.md` if they exist.
3. Read `API_TODO.md` only when the task involves APIs, fields, enums, schemas, integration, form backfill, or submit payload conversion.
4. Output a short current-task understanding before editing:

```md
## 当前任务理解

- 任务目标：
- 重点参考文件：
- 预计修改文件：
- 风险点 / 待确认项：
```

If files are missing, state that fact and continue with the best available context. Do not invent missing project facts.

## New Project Initialization

When the user asks to create project context documents:

1. Inspect the repository first: app type, framework, package scripts, key entry files, services, state management, routes/pages, tests, and existing docs.
2. Create only the needed context files. Avoid duplicate docs if equivalent files already exist.
3. Keep `AGENTS.md` short and procedural. Do not place full business requirements or chat history there.
4. Put long-lived project facts in `PROJECT_CONTEXT.md`.
5. Put current unfinished work in `CURRENT_TASK.md`; use `暂无` or equivalent when nothing is pending.
6. Put integration uncertainty in `API_TODO.md`, not in page code or long-term context.
7. Put cross-session resume notes in `HANDOFF.md`.
8. Put only meaningful milestones in `TASK_LOG.md`.

Use concise headings and stable wording so future agents can scan quickly.

## End-of-Task Update Rules

Update documents by need, not mechanically:

- Update `PROJECT_CONTEXT.md` only when a stable project fact or durable rule changed.
- Update `API_TODO.md` when APIs, fields, enums, schemas, payload conversion, or integration uncertainty was discovered or resolved.
- Update `CURRENT_TASK.md` only when work remains unfinished and must continue in a new session; clear it when the task is complete.
- Update `HANDOFF.md` when the user asks to compress context, end the conversation, prepare a new chat, or when the next session would otherwise miss important state.
- Append `TASK_LOG.md` only for milestones, user-requested records, or context compression.

Always mention which context documents were updated in the final response.

## Compression / Handoff Workflow

When preparing for a new conversation:

1. Record the current durable state in `PROJECT_CONTEXT.md` if it changed.
2. Record recently completed work and exact continuation notes in `HANDOFF.md`.
3. Record unresolved API or field questions in `API_TODO.md`.
4. Set `CURRENT_TASK.md` to the actual next unfinished task, or `暂无` if there is none.
5. Append a compact milestone to `TASK_LOG.md` only when the work is worth historical traceability.
6. Give the user a short suggested opening prompt for the next conversation.

Do not paste raw conversation summaries, exhaustive diffs, or speculative plans into long-term files.

## Guardrails

- Do not rely on chat history as the only source of truth when context files exist.
- Do not write temporary progress into `PROJECT_CONTEXT.md`.
- Do not pile historical tasks into `CURRENT_TASK.md`.
- Do not mark uncertain backend fields or enums as final.
- Do not scatter field mapping policy across page files; recommend adapters/mapping functions and document uncertainty in `API_TODO.md`.
- Do not update every document after every small request if the project rules say updates should be selective.
- Do not overwrite project-specific rules with this generic workflow.

## Useful Next-Session Prompt

When the user asks how to start a new conversation, suggest this shape and adapt it to the project:

```md
请先读取项目根目录的 AGENTS.md。

然后按 AGENTS.md 的规则读取必要上下文文件：

1. docs/codex/PROJECT_CONTEXT.md
2. docs/codex/HANDOFF.md
3. docs/codex/CURRENT_TASK.md

如果当前任务涉及接口、字段、枚举、表单回填或提交参数转换，再读取 docs/codex/API_TODO.md。

读取完成后，请先输出：

## 当前任务理解

- 任务目标：
- 重点参考文件：
- 预计修改文件：
- 风险点 / 待确认项：

确认理解后，再开始分析或修改代码。
```
