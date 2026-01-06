# Notification Skill

[中文](README_ZH.md)

Send push notifications when an Agent task finishes or when you need to notify users (currently supports Bark).

## Usage

### 1. Install Notification-Skill

Codex

```bash
codex

$skill-installer https://github.com/caopulan/Notification-Skill
```

### 2. Configure

1) Configure environment variables on the machine

Set environment variables (for example in `~/.zshrc` or `~/.bashrc`):

```bash
export CODEX_MACHINE_NAME="Your-Machine-Name"
export CODEX_BARK_KEY="your-bark-key"
export CODEX_BARK_BASE_URL="https://api.day.app"
```

2) Configure the project name

- Add a project name in `AGENTS.md`
- Otherwise, the directory name is used as the project name

### 3. Use

1) Add instructions in `AGENTS.md`

```
- After each task, notify the user via the bark-notify skill
```

2) Explicit invocation

```bash
python3 bark-notify/scripts/send_bark_notification.py \
  --task-title "Task summary" \
  --status "success" \
  --summary "What was done"
```

Parameters:

- `--task-title` (required): Task title
- `--status` (required): Execution status, e.g. `success`, `failed`
- `--summary` (required): Result summary
- `--project-name`: Override project name
- `--timeout`: Timeout in seconds (default: 10)
- `--dry-run`: Print the request but do not send it
