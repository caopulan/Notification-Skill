# Bark Notify Skill

Chinese version: [README_ZH.md](README_ZH.md)

Send Bark (day.app) push notifications after a Codex task completes.

## Overview

This skill provides a helper script that sends a Bark notification with device, project, status, and summary details.

## Requirements

- Python 3
- A Bark key from day.app

## Setup

Set environment variables (for example in `~/.zshrc` or `~/.bashrc`):

```bash
export CODEX_MACHINE_NAME="Your-Machine-Name"
export CODEX_BARK_KEY="your-bark-key"
export CODEX_BARK_BASE_URL="https://api.day.app"
```

## Usage

```bash
python3 bark-notify/scripts/send_bark_notification.py \
  --task-title "Task summary" \
  --status "success" \
  --summary "What was done"
```

Dry run (no network request):

```bash
python3 bark-notify/scripts/send_bark_notification.py \
  --task-title "Task summary" \
  --status "success" \
  --summary "What was done" \
  --dry-run
```

## Project name resolution

If `--project-name` is not provided, the script searches for `AGENTS.md` in the current directory or parent directories:

- YAML frontmatter: `project_name: My Project` (or `name:` / `title:`)
- A plain line: `Project Name: My Project`

If nothing is found, it falls back to the folder name.

## Options

- `--task-title` (required): Short task title
- `--status` (required): Execution status, e.g. `success`, `failed`
- `--summary` (required): Short summary
- `--project-name`: Override project name
- `--timeout`: Request timeout in seconds (default: 10)
- `--dry-run`: Print the request without sending it

## Files

- `bark-notify/SKILL.md`: Skill instructions
- `bark-notify/scripts/send_bark_notification.py`: Notification sender
