---
name: add-or-modify-storage-format-or-path
description: Workflow command scaffold for add-or-modify-storage-format-or-path in MediaCrawler.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-modify-storage-format-or-path

Use this workflow when working on **add-or-modify-storage-format-or-path** in `MediaCrawler`.

## Goal

Adds support for a new data storage format or changes the storage path logic for media data.

## Common Files

- `tools/async_file_writer.py`
- `store/bilibili/_store_impl.py`
- `store/bilibili/__init__.py`
- `store/douyin/_store_impl.py`
- `store/douyin/__init__.py`
- `store/kuaishou/_store_impl.py`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add methods in tools/async_file_writer.py for new format support.
- Update store/*/_store_impl.py and store/*/__init__.py to register/store using the new format.
- Update config/base_config.py and/or cmd_arg/arg.py for default format/path.
- Update database/db_session.py for new format guards.
- Update documentation (docs/data_storage_guide.md, README, etc.).

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.