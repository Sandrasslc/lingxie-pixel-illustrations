# 生成提示词模板

不要把整篇文章原样塞进提示词。先提炼视觉简报，再用下面结构组织成一次可执行的生成请求；省略无关字段。

```text
Use case: ads-marketing / illustration-story / stylized-concept
Asset type: <文章头图、活动 KV、周报 Banner、方形社交卡片等>
Primary request: <一句话描述本次要传达的内容与画面>
Source content summary: <从原文提炼的 3 至 5 个事实，保持准确>
Audience and desired response: <受众；看完应理解或采取什么行动>

Input images:
- Image 1: Lingxie logo identity and shape reference; preserve the recognizable crab geometry and red segmentation, reinterpret it as pixel art.
- Image 2: Chinese weekly-banner hierarchy/layout reference only; especially the compact top-left brand lockup. Do not copy its hand-drawn style, paper scene, or text.
- Image 3: English weekly-banner hierarchy/layout reference only. Do not copy its hand-drawn style, paper scene, or text.

Scene/backdrop: <由本次内容推导出的单一主场景；背景不固定>
Subject/action: <灵蟹 mascot 正在做的动作，以及关键道具>
Style/medium: authentic 8/16-bit pixel art, deliberate pixel clusters, stepped curves, hard-edged 2-4 tone shading, consistent black pixel outlines; no smooth vector finish
Composition/framing: <比例、主体位置、标题留白、Logo 锁定区位置>
Color palette: crab red and coral red as dominant brand colors, black outline; <必要的少量辅助色>
Text (verbatim): "<只放必须逐字出现的短标题或标签>"
Brand signature: recognizable pixel Lingxie logo/lockup plus a story-active pixel crab mascot
Constraints: preserve factual details from source; keep one visual focus; readable at thumbnail size; exact brand spelling
Avoid: cream background as a forced default, generic office scene, copied calendar/paper composition, hand-drawn sketch look, smooth gradients, anti-aliased vector curves, glossy 3D, dense paragraphs, garbled Chinese or English, watermark, unrelated brand marks
```

## 内容提炼规则

### 文章或长帖

提炼一个中心观点、一个视觉隐喻和最多三个支撑元素。封面不需要概括每一段，也不要自行添加结论。

### 活动策划

优先提炼活动类型、受众、核心动作、时间地点和参与利益。只有用户明确提供的日期、地点和口号才能进入画面。

### 更新日志或周报

把更新分成少量可视化类别，例如模型、功能、插件、活动、文档。主场景应体现“发布、升级或推进”，标签只保留用户真正需要展示的类别。

## 尺寸表达

在 `Asset type` 和 `Composition/framing` 中同时写明用途与比例，例如：

```text
Asset type: Chinese article hero banner
Composition/framing: wide 16:9 composition; compact pixel Lingxie lockup in the top-left safe area; title on the left; main crab action scene on the right; keep 8% safe margins
```

若用户要求精确像素尺寸，把尺寸也写入提示词，并在生成后检查实际文件。需要后处理时保持原比例，先裁切再用 nearest-neighbor 缩放。

## 文字策略

- 逐字引用用户提供的必需文案。
- 标题尽量控制在一行或两行，副标题保持短句。
- 不把文章摘要、活动规则或多个段落放进生成图。
- 难写的英文品牌名可额外写成 `S-o-l-o-E-n-t` 供模型校对，但成图必须显示为 `SoloEnt`。
- 首次生成出现错字时，只针对文字区域做定向修正，并重复“其他画面保持不变”。仍不可靠时，生成干净标题区后进行精确排版。

## 定向修正句式

一次只改一个问题，同时重申不变量。例如：

```text
Change only the crab mascot's abdomen from pale pink to a deeper coral red so it remains visible against the background. Keep the composition, pose, pixel density, black outlines, logo lockup, title, and every other element unchanged.
```

```text
Correct only the title to the exact text "本周更新". Preserve the existing scene, mascot, colors, pixel-art edges, top-left Lingxie lockup, and all spacing unchanged.
```
