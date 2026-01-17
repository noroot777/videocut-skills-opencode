# 本仓库说明

> opencode 目前不支持子目录内的 skill.md 识别和中文的 skill name，所以在原po的基础上把各个 skill.md 拿出来，并把 skill name 改为英文。

---

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
git clone https://github.com/noroot777/videocut-skills-opencode.git ~/.claude/skills/videocut
mv ~/.claude/skills/videocut/videocut-* ~/.claude/skills/
rm -rf ~/.claude/skills/videocut
```

### 2. 安装环境

打开 Claude Code，输入：

```
/videocut-install
```

AI 会自动安装依赖、下载模型（约5GB）。

## 使用

### 剪口播

```
/videocut-verbal
```

AI 自动：转录 → 识别口误/静音/语气词 → 生成审查稿 → 等你确认

### 执行剪辑

```
/videocut-cut
```

确认后执行删除，循环审查直到零口误。

### 加字幕

```
/videocut-subtitle
```

Whisper 转录 → 词典纠正 → 烧录字幕。

### 自更新

```
/videocut-latest
```

告诉 AI 你的偏好，它会记住。

## Skill 清单

| Skill | 功能 | 触发词 |
|-------|------|--------|
| `videocut-install` | 环境准备、模型下载 | 安装、初始化 |
| `videocut-verbal` | 转录 + 口误/静音识别 → 审查稿 | 剪口播、处理视频 |
| `videocut-cut` | 执行 FFmpeg 剪辑 + 循环审查 | 执行剪辑、确认 |
| `videocut-subtitle` | 字幕生成与烧录 | 加字幕、生成字幕 |
| `videocut-latest` | 从错误中学习，更新规则 | 更新规则、记录反馈 |

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
