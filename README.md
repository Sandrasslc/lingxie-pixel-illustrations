# lingxie-pixel-illustrations

灵蟹（SoloEnt）品牌的像素风配图 Codex Skill。

它可以从文章、活动策划、周报、更新日志等较长内容中提炼视觉主题，生成适合 Banner、文章头图、活动 KV、小红书封面、社交媒体卡片和海报的 8/16-bit 像素风配图。

## 视觉特征

- 蟹红、珊瑚红主色与黑色像素描边
- 灵蟹像素 Logo 和螃蟹 mascot
- 场景、背景、比例和构图根据输入内容变化
- 支持横版、方形和竖版等不同发布尺寸
- 默认保留紧凑的品牌锁定区，不强制使用奶油白底

## 目录结构

```text
lingxie-pixel-illustrations/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── assets/
│   ├── lingxie-logo-reference.png
│   ├── weekly-banner-en-reference.png
│   └── weekly-banner-zh-reference.png
└── references/
    ├── brand-visual-system.md
    └── prompt-template.md
```

## 安装

```bash
git clone https://github.com/Sandrasslc/lingxie-pixel-illustrations.git ~/.codex/skills/lingxie-pixel-illustrations
```

安装后可在下一轮 Codex 对话中调用：

```text
$lingxie-pixel-illustrations
```

## 使用示例

```text
使用 $lingxie-pixel-illustrations，根据下面的活动策划生成一张 3:4 小红书封面。
```

```text
使用 $lingxie-pixel-illustrations，把这篇文章转成一张横版公众号头图。
```

完整工作流、品牌不变量和提示词模板分别见 `SKILL.md` 与 `references/`。
