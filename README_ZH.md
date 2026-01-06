# Bark Notify Skill

[English](README.md)

用于在 Codex 任务结束后发送 Bark (day.app) 推送通知。

## 概览

该技能提供脚本，发送包含设备名、项目名、状态与摘要的 Bark 通知。

## 依赖

- Python 3
- Bark Key

## 配置

设置环境变量（例如写入 `~/.zshrc` 或 `~/.bashrc`）：

```bash
export CODEX_MACHINE_NAME="你的设备名"
export CODEX_BARK_KEY="你的-bark-key"
export CODEX_BARK_BASE_URL="https://api.day.app"
```

## 使用

```bash
python3 bark-notify/scripts/send_bark_notification.py \
  --task-title "任务概述" \
  --status "success" \
  --summary "完成的内容"
```

仅演示请求（不发送）：

```bash
python3 bark-notify/scripts/send_bark_notification.py \
  --task-title "任务概述" \
  --status "success" \
  --summary "完成的内容" \
  --dry-run
```

## 项目名解析

如果未传入 `--project-name`，脚本会在当前目录及其父目录查找 `AGENTS.md`：

- YAML frontmatter：`project_name: My Project`（或 `name:` / `title:`）
- 普通文本：`Project Name: My Project` 或 `项目名称：我的项目`

若未找到，将回退为文件夹名称。

## 参数

- `--task-title`（必填）：任务标题
- `--status`（必填）：执行状态，例如 `success`、`failed`
- `--summary`（必填）：结果摘要
- `--project-name`：覆盖项目名
- `--timeout`：超时秒数（默认 10）
- `--dry-run`：打印请求但不发送

## 文件说明

- `bark-notify/SKILL.md`：技能说明
- `bark-notify/scripts/send_bark_notification.py`：通知脚本
