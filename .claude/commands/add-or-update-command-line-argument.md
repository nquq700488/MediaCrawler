---
name: add-or-update-command-line-argument
description: Workflow command scaffold for add-or-update-command-line-argument in MediaCrawler.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-command-line-argument

Use this workflow when working on **add-or-update-command-line-argument** in `MediaCrawler`.

## Goal

Adds or modifies a command-line argument, often for new crawler features or configuration options.

## Common Files

- `cmd_arg/arg.py`
- `config/base_config.py`
- `media_platform/xhs/core.py`
- `store/bilibili/bilibilli_store_media.py`
- `store/douyin/douyin_store_media.py`
- `store/weibo/weibo_store_media.py`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit cmd_arg/arg.py to add or update the argument.
- Optionally update config/base_config.py if a default or config mapping is needed.
- If the argument affects platform-specific logic, update related files (e.g., media_platform/xhs/core.py).
- If the argument affects storage, update store/* files.
- Optionally update documentation (README or docs/).

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.