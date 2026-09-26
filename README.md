# Dera1.6

**Dera1.6** is a local-first system diagnostic runtime for Windows. It turns real computer evidence into explainable diagnostics and tightly controlled maintenance actions.

Dera is designed to sit between an AI interface and a computer. It gives software a way to observe, investigate, propose, validate, and verify without treating a user message as unrestricted permission.

## What it does

- Observes CPU, memory, storage, network, uptime, and running-process evidence
- Investigates common issues such as PC slowness, storage pressure, startup load, and application crashes
- Inspects user-accessible folders and Downloads storage use
- Supports optional local AI for grounded explanations
- Records local task and action history
- Provides controlled preview → approval → execution → verification flows for supported actions

## Controlled actions

Dera1.6 can support carefully bounded local actions when the host product enables them:

- Close a reviewed, non-protected application
- Disable or restore supported current-user startup entries
- Move or copy a reviewed user-owned file or folder
- Prepare a reversible move recovery action
- Execute a bounded Guided Cleanup plan selected by the user

Every action must be proposed, validated, explicitly approved, separately executed, and verified.

## Safety model

Dera1.6 is built around a simple rule: **evidence is not permission**.

1. Observe current computer state.
2. Prepare a specific action proposal.
3. Run a dry preview.
4. Ask for explicit approval.
5. Require a separate execution choice.
6. Verify the result and record it locally.

The optional language model can explain evidence, but it cannot bypass the controlled-action boundary.

## What Dera does not do

- It does not silently change a computer.
- It does not run arbitrary shell commands from chat.
- It does not automatically delete files or duplicate files.
- It does not include browsers, editors, terminals, or protected Windows processes in Guided Cleanup.
- It does not expose a computer directly to the public internet.

## Use with Moon

[Moon](https://github.com/FushiguroZenin/Moon-ADT) is a personal computer companion built on Dera1.6. Moon provides the conversational dashboard, Downloads workspace, Guided Cleanup review, Recovery Center, and user-facing permissions experience.

Dera1.6 remains useful as a standalone local diagnostic runtime or as a foundation for other controlled computer products.

## Local development

Requirements:

- Windows
- Python 3.13 or later

```powershell
python -m pip install -e ".[api,test]"
python -m pytest -q
python run_api.py
```

Open the local dashboard at [http://127.0.0.1:8765/app/](http://127.0.0.1:8765/app/).

## Project principles

- Local-first by default
- Deterministic evidence before model interpretation
- Explicit user control for every change
- Small, auditable action surface
- Verification and recovery where possible

## Status

Dera1.6 is an evolving Windows-first runtime. Its public interfaces and supported action set may expand, but its core permission model remains the same: users remain the authority over their own computer.
