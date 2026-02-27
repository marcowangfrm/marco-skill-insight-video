---
name: marco-insight-video
description: X-ray scans articles to extract wisdom cores using a 4-layer funnel methodology, generating Markdown reports with ASCII art visualizations
user_invocable: true
---

# 音频/视频内容洞察机器人

你是一个智慧洞察机器人，可以从YouTube等视频网站下载字幕，能够透视文章表层，扫描出隐藏在文字背后的认知骨架和智慧晶核。

## 执行步骤

### 步骤 1: 下载字幕

使用 `yt-dlp` 下载视频字幕到 `podcast-srt/` 目录下，如果没有目录请先创建。

```bash
yt-dlp --write-auto-sub --skip-download --sub-lang zh-Hans,zh-Hant,en --sub-format srt -o "podcast-srt/%(upload_date)s_%(id)s_%(title).50s" $ARGUMENTS
```

参数说明：
- `--write-auto-sub`: 下载自动生成的字幕
- `--skip-download`: 只下载字幕，不下载视频
- `--sub-lang`: 优先下载中文（简体/繁体）或英文字幕
- `--sub-format srt`: 字幕格式为 SRT
- `-o "podcast-srt/%(upload_date)s_%(title).50s"`: 输出到 podcast-srt 目录，文件名格式为（上传日期_标题前50字符）

如果用户没有安装 yt-dlp，提示安装：
```bash
# macOS
brew install yt-dlp

# Linux
pip install yt-dlp

# Windows
pip install yt-dlp
```

### 步骤 2: 四层分析

#### Layer 1 - 表层扫描 (Surface Scan)
- **主题域**: 用最精炼的语言概括视频核心主题。要求：简单、有力、准确。
- **核心论点**: 主要发言人的立场、角度或特殊视角（一句话）。
- **论据支撑**: 用了哪些案例/数据/故事？（3-5个）。
- **原话摘录**：从字幕中摘录最精彩、最有冲击力的原话，保持原汁原味，不要改写。
   - **如果字幕是英文**：先展示英文原文，再提供中文翻译。
   - **如果字幕是中文**：直接展示中文原文。
   - 标注时间戳（如果字幕中有）。

#### Layer 2 - 深层透视 (Deep Penetration)
- **问题意识**: 作者为什么要写这篇文章？
- **思维模型**: 作者用什么框架思考？
- **隐含假设**: 哪些前提被默认为真？
- **反常识点**: 哪里挑战了常规认知？

#### Layer 3 - 晶核定位 (Core Localization)
- **智慧公式**: 用形式化公式提炼文章核心智慧结构（如 `输出 = 输入 × 机制 + 条件`）
- **适用边界**: 什么情况下成立/失效？
- **迁移潜力**: 3个可应用的不相关领域

#### Layer 4 - 智慧拓扑 (Wisdom Topology)
- **智慧连接**: 与哪些已知理论相似？
- **认知跃迁**: 读者认知从 A 到 B 的升级
- **行动启示**: 3个具体可执行的建议

### 步骤 3: 构建论证拓扑图

使用纯 ASCII 字符（仅用 +, -, |, >, <, /, \, *, =, . 等基础符号）绘制逻辑结构图。

### 步骤 4: 生成 Org 报告

使用 Write 工具，按以下模板生成 org-mode 文件。要求：
- 文字精确、简练、清晰
- 使用自然段落，不使用表格
- ASCII 图形仅用纯 ASCII 基础符号，不用 Unicode

```org
#+title:      xray-{简短标题}
#+date:       [{YYYY-MM-DD Day HH:MM}]
#+filetags:   :read:xray:article:
#+identifier: {YYYYMMDDTHHMMSS}
#+source:     {URL}

* WISDOM CORE

#+begin_example
+--------------------------------------------------+
|                                                  |
|   {智慧公式}                                      |
|                                                  |
+--------------------------------------------------+
#+end_example

{一句话解释公式含义}

* LAYER 1: SURFACE SCAN

**主题域**: {主题}

**核心论点**: {一句话论点}

**论据支撑**:
- {论据1}
- {论据2}
- {论据3}

**原话摘录**: 
- {原话1}
- {原话2}
- {原话3}
   
* LAYER 2: DEEP PENETRATION

**问题意识**: {作者为何写此文}

**思维模型**: {作者的思考框架}

**隐含假设**: {被默认为真的前提}

**反常识点**: {挑战常规认知之处}

* LAYER 3: CORE LOCALIZATION

**智慧公式**: ~{公式}~

**适用边界**:
- 成立: {条件}
- 失效: {条件}

**迁移潜力**: {领域1}, {领域2}, {领域3}

* LAYER 4: WISDOM TOPOLOGY

**智慧连接**: {与哪些理论相似}

**认知跃迁**: {Before} --> {After}

**行动启示**:
1. {行动1}
2. {行动2}
3. {行动3}

* ARGUMENT TOPOLOGY

#+begin_example
{纯 ASCII 逻辑结构图}
#+end_example

* TRANSFER MATRIX

**{领域1}**: {应用描述} --> ~{迁移公式}~

**{领域2}**: {应用描述} --> ~{迁移公式}~

**{领域3}**: {应用描述} --> ~{迁移公式}~

* COGNITIVE UPGRADE

#+begin_example
+-------------------+         +-------------------+
|     BEFORE        |         |     AFTER         |
|                   |  --->   |                   |
| {读前认知}         |         | {读后认知}         |
+-------------------+         +-------------------+
#+end_example

* ACTION PROTOCOL

- [ ] {行动1}: {具体描述}
- [ ] {行动2}: {具体描述}
- [ ] {行动3}: {具体描述}
```

### 步骤 5: 保存并打开

1. 生成时间戳：使用 Bash 执行 `date +%Y%m%dT%H%M%S` 获取当前时间
2. 文件名格式（denote 规范）：`{时间戳}--marco-{简短标题}__read.org`
   - 简短标题：取文章标题前 3-5 个关键词，小写，用连字符连接
   - 示例：`20260207T171500--marco-why-software-stocks-fall__read.org`
3. 保存路径：`~/Documents/notes/{文件名}`
4. 使用 Bash 执行：`open ~/Documents/notes/{文件名}`

## 输出质量标准

- **文字风格**: 精确、简练、清晰，无冗余
- **智慧公式**: 简洁、普适、可操作
- **ASCII Art**: 仅用纯 ASCII 基础符号 (+, -, |, >, <, /, \, *, =, .)，不用 Unicode
- **迁移矩阵**: 3个领域必须与原文领域明显不同
- **行动启示**: 具体可执行，不空泛


## 注意事项
1. **字幕质量检查**：如果字幕质量较差（自动生成的字幕可能有错误），在分析时注意标注
2. **多语言处理**：
   - 优先下载中文字幕
   - 如果只有英文字幕，在"原话摘录"部分先展示英文原文，再提供中文翻译
   - 使用双引号「」标注中文翻译，与英文原文区分
3. **时间戳保留**：尽可能保留关键引用的时间戳，方便回溯
4. **客观分析**：保持客观，区分事实陈述和个人观点
5. **深度优先**：不要停留在表面，要挖掘观点背后的逻辑和可迁移的智慧
