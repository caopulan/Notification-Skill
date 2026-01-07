# :bell: Notification Skill

[English](README.md)

用于在 Agent 任务结束后或者需要通知用户的时候，发送推送通知（当前支持 Bark 和邮件通知）。

## :sparkles: Features
- :zap: **快速使用：** 仅需三步即可使用，安装 Skill、设置环境变量、修改 AGENTS.md 让 Agent 进行通知
- :desktop_computer: **支持多设备区分：** 可以设置 `CODEX_MACHINE_NAME` 来区分设备名称
- :mobile_phone: **支持多端收信：** Bark（iphone）、邮件（任何设备）

## :book: 使用说明

### 1. :package: 安装 Notification-Skill
选择需要的通知工具进行安装
```bash
$skill-installer https://github.com/caopulan/Notification-Skill/tree/main/bark-notify
$skill-installer https://github.com/caopulan/Notification-Skill/tree/main/email-notify
```

### 2. :gear: 配置相关信息

#### 1）:key: 获取所需的 Key 或其他参数
1. [Bark](https://github.com/finb/bark)
2. [Email]()

#### 2）:wrench: 将相关信息设置到机器环境变量

设置环境变量（例如写入 `~/.zshrc` 或 `~/.bashrc`）：

```bash
export CODEX_MACHINE_NAME="你的设备名"

# Bark
export CODEX_BARK_KEY="你的-bark-key"
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

#### 3）:label: （可选）设置项目名称
- 在项目的 `AGENTS.md` 中加入项目名称
- 否则使用目录名称作为项目名称

### 3. :rocket: 使用
#### 1) :memo: 在 `AGENTS.md` 添加说明
可以在全局 AGENTS.md 中设置来支持对该机器的所有任务进行通知。例如在 `~/.codex/AGENTS.md` 中添加：
```
- 在每次执行完任务后，通过bark-notify/email-notify skill通知用户
```

#### 2）:computer: 显式调用
1. Bark
```bash
python bark-notify/scripts/send_bark_notification.py \
  --task-title "任务概述" \
  --status "success" \
  --summary "完成的内容" \
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
