---
name: mediacrawler-conventions
description: Development conventions and patterns for MediaCrawler. Python project with mixed commits.
---

# Mediacrawler Conventions

> Generated from [nquq700488/MediaCrawler](https://github.com/nquq700488/MediaCrawler) on 2026-03-23

## Overview

This skill teaches Claude the development patterns and conventions used in MediaCrawler.

## Tech Stack

- **Primary Language**: Python
- **Architecture**: hybrid module organization
- **Test Location**: separate

## When to Use This Skill

Activate this skill when:
- Making changes to this repository
- Adding new features following established patterns
- Writing tests that match project conventions
- Creating commits with proper message format

## Commit Conventions

Follow these commit message conventions based on 200 analyzed commits.

### Commit Style: Mixed Style

### Prefixes Used

- `fix`
- `docs`
- `feat`
- `refactor`
- `chore`

### Message Guidelines

- Average message length: ~38 characters
- Keep first line concise and descriptive
- Use imperative mood ("Add feature" not "Added feature")


*Commit message example*

```text
docs: 将新增注释和文档改为中文
```

*Commit message example*

```text
fix: extend make_async_client to proxy provider and IP pool
```

*Commit message example*

```text
feat: 新增 JSONL 存储格式支持，默认存储格式改为 jsonl
```

*Commit message example*

```text
refactor(xhs): improve login state check logic
```

*Commit message example*

```text
chore: stop tracking .DS_Store
```

*Commit message example*

```text
Merge remote-tracking branch 'upstream/main'
```

*Commit message example*

```text
Merge pull request #847 from w21180239/fix/ssl-verify-proxy
```

*Commit message example*

```text
fix: make SSL verification opt-in via config, extend fix to all platforms
```

## Architecture

### Project Structure: Single Package

This project uses **hybrid** module organization.

### Configuration Files

- `.github/workflows/deploy.yml`
- `.github/workflows/main.yml`
- `package.json`

### Guidelines

- This project uses a hybrid organization
- Follow existing patterns when adding new code

## Code Style

### Language: Python

### Naming Conventions

| Element | Convention |
|---------|------------|
| Files | snake_case |
| Functions | camelCase |
| Classes | PascalCase |
| Constants | SCREAMING_SNAKE_CASE |

### Import Style: Mixed Style

### Export Style: Default Exports


*Preferred export style*

```typescript
// Use default exports for main component/function
export default function UserProfile() { ... }
```

## Error Handling

### Error Handling Style: Error Boundaries

React **Error Boundaries** are used for graceful UI error handling.


## Common Workflows

These workflows were detected from analyzing commit patterns.

### Feature Development

Standard feature implementation workflow

**Frequency**: ~5 times per month

**Steps**:
1. Add feature implementation
2. Add tests for feature
3. Update documentation

**Files typically involved**:
- `**/*.test.*`
- `**/api/**`

**Example commit sequence**:
```
feat: 添加命令行参数支持
refactor: 简化命令行参数命名
Merge pull request #817 from wanzirong/dev
```

### Add Or Update Command Line Argument

Adds or modifies a command-line argument, often for new crawler features or configuration options.

**Frequency**: ~2 times per month

**Steps**:
1. Edit cmd_arg/arg.py to add or update the argument.
2. Optionally update config/base_config.py if a default or config mapping is needed.
3. If the argument affects platform-specific logic, update related files (e.g., media_platform/xhs/core.py).
4. If the argument affects storage, update store/* files.
5. Optionally update documentation (README or docs/).

**Files typically involved**:
- `cmd_arg/arg.py`
- `config/base_config.py`
- `media_platform/xhs/core.py`
- `store/bilibili/bilibilli_store_media.py`
- `store/douyin/douyin_store_media.py`
- `store/weibo/weibo_store_media.py`
- `store/xhs/xhs_store_media.py`
- `tools/async_file_writer.py`

**Example commit sequence**:
```
Edit cmd_arg/arg.py to add or update the argument.
Optionally update config/base_config.py if a default or config mapping is needed.
If the argument affects platform-specific logic, update related files (e.g., media_platform/xhs/core.py).
If the argument affects storage, update store/* files.
Optionally update documentation (README or docs/).
```

### Add Or Modify Storage Format Or Path

Adds support for a new data storage format or changes the storage path logic for media data.

**Frequency**: ~1 times per month

**Steps**:
1. Edit or add methods in tools/async_file_writer.py for new format support.
2. Update store/*/_store_impl.py and store/*/__init__.py to register/store using the new format.
3. Update config/base_config.py and/or cmd_arg/arg.py for default format/path.
4. Update database/db_session.py for new format guards.
5. Update documentation (docs/data_storage_guide.md, README, etc.).
6. Add or update tests (e.g., tests/test_store_factory.py).

**Files typically involved**:
- `tools/async_file_writer.py`
- `store/bilibili/_store_impl.py`
- `store/bilibili/__init__.py`
- `store/douyin/_store_impl.py`
- `store/douyin/__init__.py`
- `store/kuaishou/_store_impl.py`
- `store/kuaishou/__init__.py`
- `store/tieba/_store_impl.py`
- `store/tieba/__init__.py`
- `store/weibo/_store_impl.py`
- `store/weibo/__init__.py`
- `store/xhs/_store_impl.py`
- `store/xhs/__init__.py`
- `store/zhihu/_store_impl.py`
- `store/zhihu/__init__.py`
- `config/base_config.py`
- `cmd_arg/arg.py`
- `database/db_session.py`
- `docs/data_storage_guide.md`
- `README.md`
- `README_en.md`
- `README_es.md`
- `tests/test_store_factory.py`

**Example commit sequence**:
```
Edit or add methods in tools/async_file_writer.py for new format support.
Update store/*/_store_impl.py and store/*/__init__.py to register/store using the new format.
Update config/base_config.py and/or cmd_arg/arg.py for default format/path.
Update database/db_session.py for new format guards.
Update documentation (docs/data_storage_guide.md, README, etc.).
Add or update tests (e.g., tests/test_store_factory.py).
```

### Propagate Cross Cutting Config Or Utility Change

Implements a config or utility change (e.g., SSL verification, proxy settings) that must be applied across all platforms and proxy providers.

**Frequency**: ~1 times per month

**Steps**:
1. Add or update config option in config/base_config.py.
2. Implement or update a utility in tools/ (e.g., httpx_util.py).
3. Replace or update usage in all affected platform client files (media_platform/*/client.py).
4. Update proxy provider files (proxy/providers/*.py, proxy/proxy_ip_pool.py).
5. Optionally update documentation.
6. Optionally update tests.

**Files typically involved**:
- `config/base_config.py`
- `tools/httpx_util.py`
- `tools/crawler_util.py`
- `media_platform/bilibili/client.py`
- `media_platform/douyin/client.py`
- `media_platform/kuaishou/client.py`
- `media_platform/weibo/client.py`
- `media_platform/xhs/client.py`
- `media_platform/zhihu/client.py`
- `proxy/providers/jishu_http_proxy.py`
- `proxy/providers/kuaidl_proxy.py`
- `proxy/providers/wandou_http_proxy.py`
- `proxy/proxy_ip_pool.py`

**Example commit sequence**:
```
Add or update config option in config/base_config.py.
Implement or update a utility in tools/ (e.g., httpx_util.py).
Replace or update usage in all affected platform client files (media_platform/*/client.py).
Update proxy provider files (proxy/providers/*.py, proxy/proxy_ip_pool.py).
Optionally update documentation.
Optionally update tests.
```

### Documentation Sync Across Languages

Updates documentation in multiple languages to keep feature lists, headings, or sections in sync.

**Frequency**: ~2 times per month

**Steps**:
1. Edit README.md, README_en.md, and README_es.md to update or sync content.
2. If needed, update docs/* for additional guides.
3. Optionally update images or metadata.
4. Commit with a message indicating documentation update or sync.

**Files typically involved**:
- `README.md`
- `README_en.md`
- `README_es.md`
- `docs/data_storage_guide.md`
- `docs/excel_export_guide.md`
- `docs/词云图使用配置.md`
- `docs/项目架构文档.md`
- `docs/static/images/*`

**Example commit sequence**:
```
Edit README.md, README_en.md, and README_es.md to update or sync content.
If needed, update docs/* for additional guides.
Optionally update images or metadata.
Commit with a message indicating documentation update or sync.
```

### Platform Specific Client Fix Or Feature

Implements a fix or feature in a specific media platform's client (e.g., zhihu, xhs), often for crawling or login logic.

**Frequency**: ~2 times per month

**Steps**:
1. Edit the relevant media_platform/<platform>/client.py file.
2. If needed, update related files (core.py, exception.py) for the platform.
3. If related to storage, update store/<platform>/_store_impl.py.
4. Optionally update tests or documentation.

**Files typically involved**:
- `media_platform/zhihu/client.py`
- `media_platform/xhs/client.py`
- `media_platform/xhs/core.py`
- `media_platform/xhs/exception.py`
- `store/zhihu/_store_impl.py`

**Example commit sequence**:
```
Edit the relevant media_platform/<platform>/client.py file.
If needed, update related files (core.py, exception.py) for the platform.
If related to storage, update store/<platform>/_store_impl.py.
Optionally update tests or documentation.
```


## Best Practices

Based on analysis of the codebase, follow these practices:

### Do

- Use snake_case for file names
- Prefer default exports

### Don't

- Don't deviate from established patterns without discussion

---

*This skill was auto-generated by [ECC Tools](https://ecc.tools). Review and customize as needed for your team.*
