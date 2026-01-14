# 剪辑 Skills

> 用 Claude Code Skills 做的视频剪辑 Agent

## 功能

- **口误识别**：逐字检测，精准定位，不漏不误
- **静音检测**：自动识别 ≥1s 静音片段
- **语气词处理**：自动识别"嗯""哎"等，精确删除
- **字幕生成**：Whisper + 词典纠正，质量碾压剪映
- **自更新**：越用越懂你的剪辑习惯

## 安装

### 1. 下载 Skills

```bash
# 克隆到 Claude Code skills 目录
git clone https://github.com/Ceeon/videocut-skills.git ~/.claude/skills/videocut
```

### 2. 安装环境

打开 Claude Code，输入：

```
/videocut:安装
```

AI 会自动安装依赖、下载模型（约5GB）。

## 使用

### 剪口播

```
/videocut:剪口播
```

AI 自动：转录 → 识别口误/静音/语气词 → 生成审查稿 → 等你确认

### 执行剪辑

```
/videocut:剪辑
```

确认后执行删除，循环审查直到零口误。

### 加字幕

```
/videocut:字幕
```

Whisper 转录 → 词典纠正 → 烧录字幕。

### 自更新

```
/videocut:自更新
```

告诉 AI 你的偏好，它会记住。

## Skill 清单

| Skill | 功能 | 触发词 |
|-------|------|--------|
| `videocut:安装` | 环境准备、模型下载 | 安装、初始化 |
| `videocut:剪口播` | 转录 + 口误/静音识别 → 审查稿 | 剪口播、处理视频 |
| `videocut:剪辑` | 执行 FFmpeg 剪辑 + 循环审查 | 执行剪辑、确认 |
| `videocut:字幕` | 字幕生成与烧录 | 加字幕、生成字幕 |
| `videocut:自更新` | 从错误中学习，更新规则 | 更新规则、记录反馈 |

## 依赖

- Python 3.8+
- FFmpeg
- FunASR（口误识别）
- Whisper large-v3（字幕生成）

## 工作流

```
安装（首次）
    ↓
剪口播 → 转录 + 识别 → 审查稿
    ↓
【用户确认】
    ↓
剪辑 → 执行删除 → 重新审查 → 循环直到零口误
    ↓
字幕 → 词典纠错 → 烧录
    ↓
自更新（发现问题时）
```

## License

MIT
