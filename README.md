# Notification Skill

[中文](README_ZH.md)

Send push notifications when an Agent task finishes or when you need to notify users (currently supports Bark and email).

## Features
- **Quick setup:** Only three steps to get started: install a skill, set environment variables, and update AGENTS.md so the Agent can notify
- **Multi-device naming:** Set `CODEX_MACHINE_NAME` to distinguish devices

## Usage

### 1. Install Notification-Skill

Choose the notification tool you need to install:
```bash
$skill-installer https://github.com/caopulan/Notification-Skill/tree/main/bark-notify
$skill-installer https://github.com/caopulan/Notification-Skill/tree/main/email-notify
```

### 2. Configure

#### 1) Get required keys or parameters (TODO)
1. Bark
2. Email

#### 2) Set environment variables on the machine

Set environment variables (for example in `~/.zshrc` or `~/.bashrc`):

```bash
export CODEX_MACHINE_NAME="Your-Machine-Name"

# Bark
export CODEX_BARK_KEY="your-bark-key"
export CODEX_BARK_BASE_URL="https://api.day.app"

# Email
export CODEX_EMAIL_SMTP_HOST="smtp.example.com"
export CODEX_EMAIL_SMTP_PORT="587"
export CODEX_EMAIL_USERNAME="user@example.com"
export CODEX_EMAIL_PASSWORD="..."
export CODEX_EMAIL_FROM="user@example.com"
export CODEX_EMAIL_TO="recipient1@example.com,recipient2@example.com"
export CODEX_EMAIL_USE_TLS="false" # true/false, default false
export CODEX_EMAIL_USE_SSL="true" # true/false, default true
```

#### 3) (Optional) Set project name

- Add a project name in `AGENTS.md`
- Otherwise, the directory name is used as the project name

### 3. Use

#### 1) Add instructions in `AGENTS.md`
You can configure the global AGENTS.md to notify for all tasks on this machine. For example in `~/.codex/AGENTS.md`:

```
- After each task, notify the user via the bark-notify/email-notify skill
```

#### 2) Explicit invocation
1. Bark

```bash
python bark-notify/scripts/send_bark_notification.py \
  --task-title "Task summary" \
  --status "success" \
  --summary "What was done" \
  --project-name "..."
```
2. Email

```bash
python email-notify/scripts/send_email_notification.py \
  --task-title "..." \
  --status "success" \
  --summary "..." \
  --project-name "..."
```
