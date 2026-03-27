---
name: leann-rebuild
description: Rebuild LEANN knowledge index from workspace files
version: 1.0.0
triggers:
  - leann rebuild
  - rebuild index
  - knowledge index
---

# LEANN Index Rebuild

Rebuilds the LEANN knowledge base index from workspace scripts, memory, docs, and skills.

## Steps

1. Run: `cd ~/.openclaw/workspace && python3 scripts/cron_runner.py --script '/opt/homebrew/share/leann/bin/leann build brain-knowledge --docs /Users/charlesM/.openclaw/workspace/scripts /Users/charlesM/.openclaw/workspace/memory /Users/charlesM/.openclaw/workspace/docs /Users/charlesM/.openclaw/workspace/skills /Users/charlesM/.openclaw/workspace/flowrunner --embedding-mode openai --embedding-api-base http://127.0.0.1:28100/v1 --embedding-api-key not-needed --embedding-model nomic-ai/nomic-embed-text-v1.5 --file-types .md,.py,.yaml,.sh --include-hidden --force' --name leann-rebuild --timeout 120`
2. Report result

## Timeouts
- Script timeout: 120s
- Job timeout: 180s (allow buffer for large indexing)