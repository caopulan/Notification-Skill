# Notification Skill

[English](README.md)

用于在 Agent 任务结束后或者需要通知用户的时候，发送推送通知（当前支持Bark）。

## 使用说明

### 1. 安装Notification-Skill
Codex
```bash
codex

$skill-installer https://github.com/caopulan/Notification-Skill
```

### 2. 配置相关信息

1）在机器上配置环境变量

设置环境变量（例如写入 `~/.zshrc` 或 `~/.bashrc`）：

```bash
export CODEX_MACHINE_NAME="你的设备名"
export CODEX_BARK_KEY="你的-bark-key"
export CODEX_BARK_BASE_URL="https://api.day.app"
```

2）为项目配置项目名
- 在`AGENTS.md`中加入项目名称
- 否则使用目录名称作为项目名称

### 3. 使用
1) 在`AGENTS.md`添加说明

```
- 在每次执行完任务后，通过bark-notify skill通知用户
```

2) 显式调用
```bash
python3 bark-notify/scripts/send_bark_notification.py \
  --task-title "任务概述" \
  --status "success" \
  --summary "完成的内容"
```

参数：

- `--task-title`（必填）：任务标题
- `--status`（必填）：执行状态，例如 `success`、`failed`
- `--summary`（必填）：结果摘要
- `--project-name`：覆盖项目名
- `--timeout`：超时秒数（默认 10）
- `--dry-run`：打印请求但不发送