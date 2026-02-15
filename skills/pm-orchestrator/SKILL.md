---
name: pm-orchestrator
description: Manages batch processing of RawNotes by delegating to specialized sub-agents.
---
# Instructions
1. **Inventory:** Use `ls` to list all files in the `RawNotes/` folder.
2. **Batch Planning:** Group related notes together. For example, if there are 3 notes about "Login," group them as one "Feature Set."
3. **Delegation:** For each group or large file:
    - Spawn a **prd-architect** sub-agent to create the PRD folder and file.
    - Spawn a **market-intel** sub-agent to perform search-grounded research for that specific feature.
4. **Status Report:** Once all sub-agents finish, provide a summary table of the new folders created in the `PRD/` directory.

# Safety
Always run sub-agents with `--approval-mode=yolo` for batch tasks to avoid 50+ manual confirmation prompts, but only if the output directory is `PRD/`.

