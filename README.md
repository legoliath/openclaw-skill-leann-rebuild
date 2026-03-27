# 🧠 openclaw-skill-leann-rebuild

Rebuild LEANN knowledge index from workspace files

![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-blue) ![Status](https://img.shields.io/badge/Status-Active-green)

## Overview

The `openclaw-skill-leann-rebuild` is designed to refresh and reconstruct the LEANN (Learning, Extraction, Analysis, N-gram Network) knowledge base index. This process ensures that LEANN has the most up-to-date understanding of your OpenClaw workspace, including scripts, memory, documentation, and other critical files.

## Features

- **Comprehensive Indexing**: Rebuilds the LEANN knowledge index from multiple specified workspace directories: scripts, memory, docs, skills, and flowrunner.
- **Flexible Embedding Configuration**: Allows specification of embedding mode, API base URL, API key (if needed), and the embedding model.
- **File Type Inclusion**: Configurable to include specific file types, such as Markdown (`.md`), Python (`.py`), YAML (`.yaml`), and Shell scripts (`.sh`).
- **Hidden File Support**: Includes hidden files in the indexing process for a complete knowledge base.
- **Force Rebuild**: Option to force a complete rebuild of the index, discarding previous states.
- **Timeout Management**: Includes built-in timeouts for script execution and job completion to prevent indefinite hangs.

## Installation

To enable this skill within OpenClaw, place the `leann-rebuild` directory into your `~/.openclaw/workspace/skills/` directory:

```bash
cp -R leann-rebuild ~/.openclaw/workspace/skills/
```

## Usage

This skill is typically invoked via the `cron_runner.py` script, which manages its execution and applies timeouts. The `SKILL.md` provides the exact command:

```bash
cd ~/.openclaw/workspace && \
python3 scripts/cron_runner.py --script '/opt/homebrew/share/leann/bin/leann build brain-knowledge --docs \
/Users/charlesM/.openclaw/workspace/scripts \
/Users/charlesM/.openclaw/workspace/memory \
/Users/charlesM/.openclaw/workspace/docs \
/Users/charlesM/.openclaw/workspace/skills \
/Users/charlesM/.openclaw/workspace/flowrunner \
--embedding-mode openai --embedding-api-base http://127.0.0.1:28100/v1 \
--embedding-api-key not-needed --embedding-model nomic-ai/nomic-embed-text-v1.5 \
--file-types .md,.py,.yaml,.sh --include-hidden --force' --name leann-rebuild --timeout 120
```

> [!IMPORTANT]
> Ensure that `leann` is installed and accessible in your system's PATH, and that `cron_runner.py` is located in `~/.openclaw/workspace/scripts/`. The `embedding-api-base` and `embedding-model` should match your local LEANN setup.

## Configuration

Key configuration parameters are passed directly as arguments to the `leann build` command within the usage script:

- **`--embedding-mode`**: Specifies the embedding provider (e.g., `openai`).
- **`--embedding-api-base`**: The base URL for the embedding API (e.g., `http://127.0.0.1:28100/v1`).
- **`--embedding-api-key`**: API key for the embedding service (can be `not-needed` if not required).
- **`--embedding-model`**: The specific embedding model to use (e.g., `nomic-ai/nomic-embed-text-v1.5`).
- **`--file-types`**: Comma-separated list of file extensions to include.
- **`--timeout`**: Script timeout (120s) and an implicit job timeout (180s) for the `cron_runner`.

## File Structure

```
.
└── leann-rebuild/
    └── SKILL.md
```
